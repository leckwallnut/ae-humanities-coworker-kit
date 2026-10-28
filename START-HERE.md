# AE Humanities: coworker kit

**Version 1.1 - 28 October 2026**

Make readable, varied Humanities slides in a dark academia style. This folder contains the skill, all 117 images, editable examples, lesson presets and the practical guides. Keep the folder structure intact when sharing it.

## What's new in 1.1

- **A much smaller skill.** The installed skill folder is about 140 MB instead of 443 MB, and new decks are lighter. The 62 opaque backgrounds and scenes are now high-quality JPEG copies; the 55 images with transparency are unchanged PNGs. The original PNGs and the three visual guide PDFs moved to an optional Extras download.
- **PowerPoint checks for Windows.** [The PowerPoint checks](artifact-template-ae-humanities-ppts/references/powerpoint-checks.md) render slides with the real fonts, flag text that overflows its box, and add and confirm Fade transitions and click reveals with desktop PowerPoint. The motion guides record the 28 October test, including a fix for an empty click when revealing one paragraph at a time.
- **Prompts travel with the skill.** The starter prompts now live inside the skill folder, with the first-run test and [a description of a good result](artifact-template-ae-humanities-ppts/references/first-run-check.md). Static and animated reference decks for the first-run test are in [examples](examples/README.md).
- **Setup for any assistant.** [SETUP.md](SETUP.md) now covers WorkBuddy, Kimi Code, Qwen Code, CodeBuddy, Trae, Codex and other assistants that support skills, and the prompts use plain wording instead of one assistant's shortcut.

## Get started in five minutes

1. Extract the whole ZIP to a folder on your computer.
2. Open [the 20-slide layout library](artifact-template-ae-humanities-ppts/assets/teaching-layouts.pptx) in PowerPoint to see the style and how much text fits. Save a copy to adapt it manually.
3. For AI-assisted creation, open this extracted kit folder in your AI assistant (WorkBuddy, Kimi Code, Qwen Code, Trae, Codex or similar) as its working folder. Paste the first-run prompt below. The assistant needs access to your files and a way to make PowerPoint files; the kit supplies design guidance and assets.
4. For repeated use across projects, follow [SETUP.md](SETUP.md) to install the skill in your assistant. The easiest way is to ask the assistant to install it for you.
5. Use a prompt from [STARTER-PROMPTS.md](artifact-template-ae-humanities-ppts/STARTER-PROMPTS.md), attach your lesson material, and check the finished deck in your classroom setup.

### First-run prompt

```text
Read ./artifact-template-ae-humanities-ppts/SKILL.md and use that skill for this task. Confirm you can find the 20-slide layout library and the 117-image collection.

Create a three-slide, 16:9 editable PowerPoint introducing the difference between observation and interpretation. Use this original example: "The chair is empty. A wet coat hangs beside the door." Label it as a classroom example.

Slide 1: explain observation and interpretation. Slide 2: show the example with two discussion questions; keep suggested answers in notes. Slide 3: give a short independent practice task. Use Georgia Bold headings, Arial body text, and three different suitable layouts. Reuse the bundled images. Render and check the slides, and save the result in a new lesson-output folder. If presentation creation is unavailable, say so clearly and give the slide plan.
```

Compare the result with [what a good first-run result looks like](artifact-template-ae-humanities-ppts/references/first-run-check.md).

## What is included

| Resource | Where to start |
| --- | --- |
| Portable skill | [SKILL.md](artifact-template-ae-humanities-ppts/SKILL.md) |
| 20 editable layout examples | [Teaching layouts](artifact-template-ae-humanities-ppts/assets/teaching-layouts.pptx) and [slide index](artifact-template-ae-humanities-ppts/references/layout-library.md) |
| Complete 11-slide sample lesson | [Quiet Words: scary stories](<examples/Quiet Words - Scary Stories with Hemingway.pptx>) |
| Four lesson presets | [Brief explanation, close reading, discussion, writing workshop](artifact-template-ae-humanities-ppts/references/lesson-presets.md) |
| 117 images | [Image library](artifact-template-ae-humanities-ppts/references/image-library.md) |
| Fonts and readable text | [FONT-GUIDE.md](FONT-GUIDE.md) |
| First-run test and six prompts | [STARTER-PROMPTS.md](artifact-template-ae-humanities-ppts/STARTER-PROMPTS.md) and [a good first-run result](artifact-template-ae-humanities-ppts/references/first-run-check.md) |
| Motion examples - pilot | [Four-slide deck](artifact-template-ae-humanities-ppts/assets/motion-pilot.pptx) and [test limits](artifact-template-ae-humanities-ppts/references/motion-pilot-guide.md) |
| PowerPoint checks (Windows) | [Render, fit-check and animate](artifact-template-ae-humanities-ppts/references/powerpoint-checks.md) |
| Original PNGs and visual guide PDFs | Optional Extras download, in `Extras/` |

The images comprise 53 original dark academia assets, 16 transparent symbolic objects, 12 quiet text surfaces, 12 storytelling images and 24 spacious backgrounds. The newer collections include placement advice; their visual guide PDFs are in the optional Extras download. Every image the skill uses, and the example decks, are included locally.

Use **Georgia Bold + Arial**, normally **38 pt headings + 26 pt body**, on **16:9 slides**. Font files are not included; check that those fonts are available on the computer that makes and presents the deck. See the font guide for alternatives and checks.

The motion examples are a pilot: Windows playback passed for six click reveals, but one tested import/export route removed the effects. Saving and reopening in desktop PowerPoint kept the effects in a 28 October test; copying slides and playback after saving remain unverified. Read the pilot guide and test your actual delivery file before relying on animation.

## Share and maintain

The kit is published at https://github.com/leckwallnut/ae-humanities-coworker-kit, so you can send coworkers that link; its front page has an install prompt to paste into their assistant. You can also share the complete ZIP or the whole extracted folder. The Extras ZIP is optional: extract it in the same place and its `Extras` folder joins the kit. The skill never needs it. Copy the complete skill folder when installing; retain its name and subfolders. The original installed skill on the package creator's computer is not required. Save classroom work outside the bundled examples so the kit remains reusable.

[Setup and troubleshooting](SETUP.md) · [Fonts](FONT-GUIDE.md) · [Prompts](artifact-template-ae-humanities-ppts/STARTER-PROMPTS.md) · [Example notes](examples/README.md)
