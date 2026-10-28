# Humanities motion pilot

This collection contains four editable slides with native PowerPoint effects. It remains a pilot, not a promise that motion survives every editing or export route.

## Copyable examples

Open [motion-pilot.pptx](../assets/motion-pilot.pptx) in desktop PowerPoint. All four slides use a Fade transition configured for 0.4 seconds with manual advance. Reveals use **Appear**, instantly showing a complete text box.

| Slide | Pattern | Initial state | Teacher clicks |
| --- | --- | --- | --- |
| 1 | Subtle slide fade | Passage and question visible | Next click advances |
| 2 | Answer reveal | Passage and question visible, answer hidden | 1: answer |
| 3 | Ordered annotations | Passage and question visible, notes hidden | 1: annotation-1; 2: annotation-2; 3: annotation-3 |
| 4 | Revision example | Draft and practice instruction visible | 1: revision; 2: explanation |

The click after the last reveal advances to the next slide. Answers also appear in speaker notes. Text remains editable in Georgia and Arial. The static final state contains all teaching content.

To adapt an example, copy the whole slide using Keep Source Formatting and replace text inside the existing objects. Deleting a reveal object and drawing a new box loses the effect attached to it. Remove collection-label and demo-footer before class. Preserve the bundled pilot unchanged. Copying and saving edited slides still need the validation below.

## What was tested

Test date: 25 October 2026. PowerPoint for Windows 16.0.20527.20088.

- All three reveal slides played in the actual PowerPoint slideshow. Each of the six targets began hidden and appeared at its intended click. Passages, questions and task instructions stayed visible. Earlier annotations remained visible.
- A mouse click revealed the answer. Right Arrow advanced the other effects. Left Arrow on slide 4 hid the explanation while keeping the revision visible.
- The Transitions tab displayed 0.40 seconds, On Mouse Click checked, After unchecked and No Sound. Slide navigation succeeded. Continuous transition frame timing and smoothness were not measured.
- The final delivered PPTX is byte-for-byte identical to the animated candidate tested in playback. Package validation confirmed four Fade transitions, six click effects and valid object targets.
- Importing and re-exporting that file with the bundled artifact-tool runtime 26.1009.11318 removed every transition and click effect. That route **failed motion preservation**.
- PowerPoint editing, copying slides, Save As and a PowerPoint save/reopen cycle remain untested because the installed app reported an expired subscription and disabled editing and saving. PDF/video, PowerPoint for Mac/web, Google Slides and LibreOffice playback were not tested.

### Follow-up test: 28 October 2026

- PowerPoint for Windows 16.0, build 20527, with editing and saving available.
- Automation added 0.4-second Fade transitions and Appear-on-click reveals to a newly generated three-slide deck, saved it, closed it and reopened it. Every transition and all three reveals were intact after reopening. This answers the save/reopen check for that route; see [powerpoint-checks.md](powerpoint-checks.md).
- Revealing one paragraph per click also added an effect for the text box itself, which produced a first click that showed nothing. Deleting that box-level effect fixed it.
- Automated slideshow playback failed (the call was rejected and PowerPoint closed), so playback of the saved file was not observed. Copying slides with Keep Source Formatting and other delivery routes remain untested.

## Export boundary

Finish the static slide-generation export first. Add or retain native effects after that export, validate the animated PPTX and deliver it without importing and re-exporting it through the tested artifact-tool version. A read-only import used for inspection does not establish that a later export will preserve effects. Static previews cannot verify motion.

For coworkers working in licensed PowerPoint, use the native pilot as a starting point and test the actual edited file. Until the checks below pass, describe it as a pilot and state the remaining gap. Do not claim general animation support in the skill description.

## Checks before promotion

1. In licensed PowerPoint, copy each example into a new 16:9 deck using Keep Source Formatting. Change text inside the existing answer, annotation and revision objects.
2. Save as a new PPTX, close it, reopen it and start each example with Shift+F5. Check the initial state and every click against the table above. Confirm one whole idea appears per click.
3. Inspect all four transitions in the Transitions tab and observe their fades in playback. Confirm manual advance and no sound. Test restarting a slide and reverse navigation.
4. Run the intended delivery/export route on a copy. Reopen that actual output in PowerPoint and repeat the checks. Inspect the package for valid transition and timing targets.
5. Record application version, workflow and observed results. Promote only the tested combination. Keep unsupported routes explicit and retest when the authoring/export tool changes.

## Implementation provenance

The Appear sequence was retained from the user's native PowerPoint source, Comparing Sources AE for Science.pptx, slide 19, with object targets and unique timing IDs remapped. The pilot uses no macros or embedded executable code. Fade transition duration follows Microsoft's [documented PresentationML transition extension](https://learn.microsoft.com/en-us/openspecs/office_standards/ms-pptx/99b95b35-568a-4652-9cba-df3d1175952f). The Science file is not needed to use the bundled pilot.
