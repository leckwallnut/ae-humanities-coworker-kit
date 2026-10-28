# Check and animate a deck with desktop PowerPoint (Windows)

Use this on a Windows computer with desktop PowerPoint installed. PowerPoint renders the slides with the real Georgia and Arial fonts, measures whether text fits its box, and adds native transitions and reveals itself. On a Mac, or without desktop PowerPoint, use the host's own rendering and keep its limits in mind.

Previews made without the real fonts can misreport fit. LibreOffice, for example, replaces Georgia with a font of different width, so a heading can look fine there and wrap in PowerPoint, or the reverse. Trust the PowerPoint render for Georgia headings.

These snippets were written and tested on 28 October 2026 with PowerPoint for Windows 16.0, build 20527, while building the first-run test lesson.

## Ground rules

- Run each snippet directly in PowerShell. Do not save it as a `.ps1` file and run it with `-ExecutionPolicy Bypass`; security tools may block that, and it is not needed.
- Work in a short folder such as `%TEMP%\lesson-build`, then copy the finished file to its destination. Some tools fail on paths longer than 260 characters.
- Each snippet checks whether PowerPoint was already open. It quits PowerPoint only if the snippet started it, so a teacher's open presentations are left alone.
- Checks open the deck read-only. Only the motion snippet saves, and only to the copy it is given.
- Do not automate slideshow playback. In testing, starting a slideshow through automation was rejected (`RPC_E_CALL_REJECTED`) and PowerPoint closed. Ask the teacher to press **F5** and click through instead.

## 1. Render every slide and check text fit

Set the two paths, run, then look at every exported image.

```powershell
$deck = "$env:TEMP\lesson-build\deck.pptx"
$outDir = "$env:TEMP\lesson-build\render"
$wasRunning = [bool](Get-Process POWERPNT -ErrorAction SilentlyContinue)
New-Item -ItemType Directory -Force $outDir | Out-Null
Get-ChildItem $outDir -Filter "slide-*.png" | Remove-Item -Force
$app = New-Object -ComObject PowerPoint.Application
$p = $app.Presentations.Open($deck, -1, 0, 0)   # read-only, no window
try {
  foreach ($s in $p.Slides) {
    $s.Export(("{0}\slide-{1}.png" -f $outDir, $s.SlideIndex), "PNG", 1600, 900)
    foreach ($sh in $s.Shapes) {
      if ($sh.HasTextFrame -and $sh.TextFrame2.HasText) {
        $tr = $sh.TextFrame2.TextRange
        $fonts = ($tr.Runs() | ForEach-Object { "{0}{1} {2}pt" -f $_.Font.Name, $(if ($_.Font.Bold) { " Bold" } else { "" }), $_.Font.Size } | Select-Object -Unique) -join "; "
        $flag = if ($tr.BoundHeight -gt $sh.Height + 1) { "OVERFLOW" } else { "ok" }
        "slide {0} | {1,-14} | box {2,6:N1} pt | text {3,6:N1} pt | {4} | {5}" -f $s.SlideIndex, $sh.Name, $sh.Height, $tr.BoundHeight, $flag, $fonts
      }
    }
  }
} finally {
  $p.Close()
  if (-not $wasRunning) { $app.Quit() }
}
```

`OVERFLOW` means the text is taller than its box. Split the content, shorten it or enlarge the box; do not shrink below the sizes in the design system. The font column shows what PowerPoint actually used, which catches substitutions. A box can pass this check and still look crowded, so inspect the images too.

## 2. Add motion to a copy of the finished deck

Finish and check the static deck first, then animate a copy, as [motion.md](motion.md) requires. Reveals find their targets by shape name, so give reveal targets meaningful names when building the deck. If the deck is generated with pptxgenjs, text added to a layout placeholder takes the placeholder's name, so set `objectName` in the layout's placeholder definition rather than on the slide.

List the reveals in click order. `ByParagraph = $true` shows one paragraph per click; `$false` shows the whole box at once.

```powershell
$deck = "$env:TEMP\lesson-build\deck (animated).pptx"   # a copy of the static deck
$reveals = @(
  @{ Slide = 1; Shape = "right";     ByParagraph = $false }
  @{ Slide = 2; Shape = "questions"; ByParagraph = $true }
)
$notes = @{
  1 = "Motion: Fade transition, 0.4 s, manual advance. Click 1 shows the Interpretation column."
  2 = "Motion: Fade transition, 0.4 s, manual advance. Click 1 shows question 1; click 2 shows question 2."
  3 = "Motion: Fade transition, 0.4 s, manual advance. No click reveals, so the task stays visible while students work."
}
$wasRunning = [bool](Get-Process POWERPNT -ErrorAction SilentlyContinue)
$app = New-Object -ComObject PowerPoint.Application
$p = $app.Presentations.Open($deck, 0, 0, 0)   # read-write, no window
try {
  foreach ($s in $p.Slides) {
    $t = $s.SlideShowTransition
    $t.EntryEffect = 3849      # Fade, as named in the Transitions tab
    $t.Duration = 0.4
    $t.AdvanceOnClick = -1
    $t.AdvanceOnTime = 0
  }
  foreach ($r in $reveals) {
    $s = $p.Slides($r.Slide)
    $level = if ($r.ByParagraph) { 2 } else { 0 }
    $null = $s.TimeLine.MainSequence.AddEffect($s.Shapes($r.Shape), 1, $level, 1)   # Appear, on click
    if ($r.ByParagraph) {
      # PowerPoint also adds an effect for the box itself; left in, it costs a click that shows nothing.
      @($s.TimeLine.MainSequence | Where-Object { $_.Shape.Name -eq $r.Shape -and -not $_.Paragraph }) | ForEach-Object { $_.Delete() }
    }
    foreach ($e in $s.TimeLine.MainSequence) { if ($e.Shape.Name -eq $r.Shape) { $e.Timing.TriggerType = 1 } }
  }
  foreach ($i in $notes.Keys) {
    $null = $p.Slides($i).NotesPage.Shapes.Placeholders(2).TextFrame.TextRange.InsertAfter("`r`r" + $notes[$i])
  }
  $p.Save()
} finally {
  $p.Close()
  if (-not $wasRunning) { $app.Quit() }
}
```

Give every slide a motion line in `$notes`, including slides with a transition only, so the teacher knows what each click does.

## 3. Confirm the motion after saving

Reopen the saved file and read back what PowerPoint stored. This checks that the effects survived saving; it does not replace watching them play.

```powershell
$deck = "$env:TEMP\lesson-build\deck (animated).pptx"
$wasRunning = [bool](Get-Process POWERPNT -ErrorAction SilentlyContinue)
$app = New-Object -ComObject PowerPoint.Application
$p = $app.Presentations.Open($deck, -1, 0, 0)
$trigger = @{ 1 = "on click"; 2 = "with previous"; 3 = "after previous" }
try {
  foreach ($s in $p.Slides) {
    $t = $s.SlideShowTransition
    "slide {0}: transition {1}, {2} s, manual {3}" -f $s.SlideIndex, $t.EntryEffect, $t.Duration, ($t.AdvanceOnClick -and -not $t.AdvanceOnTime)
    foreach ($e in $s.TimeLine.MainSequence) {
      $what = if ($e.Paragraph) { $e.Shape.TextFrame2.TextRange.Paragraphs($e.Paragraph).Text.Trim() } else { "(whole box)" }
      "  click: {0} | {1} | {2}" -f $e.Shape.Name, $trigger[[int]$e.Timing.TriggerType], $what
    }
  }
} finally {
  $p.Close()
  if (-not $wasRunning) { $app.Quit() }
}
```

Every slide should show transition `3849` at `0.4` seconds with manual advance. Each reveal should be listed once, `on click`, in the intended order. A `(whole box)` line for a box that should reveal by paragraph is the empty click described above.

Then ask the teacher to open the file, press **F5** and click through once, checking each slide's starting state and every click.

## Test record: 28 October 2026

PowerPoint for Windows 16.0, build 20527. While the first-run reference lesson (three slides, generated with pptxgenjs) was being built, an early version of these steps found two overflowing boxes, fixed by resizing them. It also left an empty click from the box-level effect, which led to the deletion step above.

The three snippets were then run exactly as printed here on the rebuilt deck. Snippet 1 reported every box fitting, in Georgia Bold and Arial as intended. Snippet 2 added the motion and saved. After reopening, snippet 3 listed a 0.4-second Fade with manual advance on all three slides and three on-click reveals in the intended order, with no empty click. Slideshow playback of the saved file was not observed by automation.
