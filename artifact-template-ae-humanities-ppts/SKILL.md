---
name: artifact-template-ae-humanities-ppts
description: "Create or restyle Academic English for Humanities PowerPoint decks in a readable dark academia style. Use for AE Humanities PPTs or this template, with Georgia and Arial fonts, varied teaching layouts, lesson presets, and 117 bundled images."
---

# AE Humanities PPTs

Create editable Humanities lessons with dark libraries, warm paper, restrained brass and burgundy, readable text and varied teaching layouts. The teacher's current material, instructions and time constraints take priority over all examples.

## Start here

Read [authoring-guide.md](references/authoring-guide.md) and [design-system.md](references/design-system.md) before making a deck. Use Georgia Bold headings and Arial body text; no cursive. Default to 16:9, 38 pt slide headings and 26 pt body text. Split crowded material before shrinking it.

Resolve bundled file paths from this skill folder, not the working directory or a previous computer. Markdown links resolve from their containing document; asset catalog paths beginning `assets/` resolve from the skill root. The whole folder is portable. No access to an earlier chat is needed.

Use the host's available presentation-authoring and rendering tools. If a Presentations skill is available, follow it for deck creation, inspection and export; it is a host capability and is not bundled here. If no presentation tool is offered but you can run code, build the deck with a PowerPoint library such as python-pptx or pptxgenjs, then render it and check it. If this environment cannot produce an editable PPTX, explain that limitation and provide a slide plan with asset choices rather than claiming a file was created.

## Prompts and first-run check

[STARTER-PROMPTS.md](STARTER-PROMPTS.md) holds a first-run test and six prompts to adapt. After the first run, or when a coworker asks what a good result looks like, compare it with [first-run-check.md](references/first-run-check.md).

## Plan the lesson

Use [lesson-presets.md](references/lesson-presets.md) for a brief explanation, close reading, discussion or writing workshop. Adapt pacing to the teacher's material. Use [layouts.md](references/layouts.md) for composition choices and [layout-library.md](references/layout-library.md) to select from the [20 editable example slides](assets/teaching-layouts.pptx). Replace sample content and remove template labels and capacity guides before class. Preserve required source images, quotations, tasks and answers.

[artifact-template.json](artifact-template.json) points to the [teaching layout library](assets/teaching-layouts.pptx) as the reference deck, with its preview image. Work on copies of bundled decks.

## Choose artwork

Read [image-library.md](references/image-library.md) for the 117-image index. Preview selected files and keep overlaid text editable.

- [Spacious backgrounds](references/spacious-backgrounds.md): 24 architectural scenes with left, right, center and wide text areas, colors and sample word budgets.
- [Quiet surfaces](references/quiet-surfaces.md): 12 paper backgrounds for substantial readings, quotations, comparisons and revision.
- [Symbolic objects](references/symbolic-objects.md): 16 transparent objects with possible themes and discussion prompts.
- [Story sequences](references/picture-sequences.md): four related three-image sets for inference and writing.

Prefer these existing assets over regenerating equivalents. Preserve transparency and aspect ratio. Generated art is illustrative, not documentary evidence.

## Motion and delivery

When motion is requested, read [motion.md](references/motion.md) and [motion-pilot-guide.md](references/motion-pilot-guide.md). The four-slide pilot has native Fade transitions and six click-to-Appear reveals. Playback passed in the documented Windows test; the tested slide-generation import/export removed motion. A 28 October follow-up confirmed that effects added by desktop PowerPoint survive saving and reopening; playback of a saved file and copying slides remain unverified. On Windows with desktop PowerPoint, add and confirm motion with [powerpoint-checks.md](references/powerpoint-checks.md). Keep motion labelled a pilot and ask the teacher to click through the actual delivery file.

Render and inspect every finished slide for text fit, contrast, font consistency and purposeful layout variety. On Windows with desktop PowerPoint, render and measure fit with [powerpoint-checks.md](references/powerpoint-checks.md); previews without the real Georgia font can misreport fit. Preserve required lesson content and sources. Return an editable PPTX, with teaching notes and any material validation limits. Follow the authoring guide for the full quality checks.
