# Motion for Humanities slides

A small native [motion pilot](../assets/motion-pilot.pptx) is available. Read the [pilot guide](motion-pilot-guide.md) for exact examples, reuse instructions and test results. It includes 0.4-second Fade slide transitions and instantaneous Appear reveals. Object Fade animations are a future option, not a tested part of this collection.

As of 25 October 2026, all six reveal steps passed desktop PowerPoint playback. Native effects survived byte-preserving delivery, but the tested artifact-tool import/re-export removed all transitions and reveals. Complete the static export first, add or retain native motion afterward and preserve that final PPTX. Do not send the animated file back through that export route unless a new preservation test passes. On 28 October 2026, desktop PowerPoint for Windows (16.0, build 20527) added Fade transitions and Appear reveals to a newly generated deck through automation, saved it, and reopened it with every transition and reveal intact; [powerpoint-checks.md](powerpoint-checks.md) gives the method. Playback of that saved file was not observed, and copying animated slides into another deck remains untested. Keep motion a pilot until the remaining checks pass.

## Preferred effects

- Use one subtle Fade transition through most of the deck, about 0.3–0.5 seconds, with manual slide advance by the teacher. A quiet dissolve or occasional supported Morph may suit a chapter change if tested in the target presentation software.
- Use the pilot’s instantaneous Appear on click, or a short Fade of 0.2–0.4 seconds only after testing it, to reveal an answer after students consider a question, an interpretation after they read a passage, or biography stages in explanatory order.
- Reveal complete ideas. Keep text and any paper image that must appear with it in one supported group, or apply coordinated effects to both.
- Keep reading passages, task instructions, essential source context, chart units, and citations needed to interpret evidence visible. Avoid automatic slide advance unless the user requests a timed presentation.
- Preserve the quiet atmosphere: no spins, bouncing, typewriter letter effects, sound effects, flashing candles, or continuously moving decorations.

## Make the deck easy to animate

Keep reveal targets in separate editable text boxes or supported groups. Give them meaningful names such as `question`, `answer`, `interpretation`, `biography-stage-1`, or `model-response` where object naming is supported. A whole-slide PNG is one flat image; its shelves, paper panels, and objects cannot animate independently. Use separate supplied component PNGs when independent objects are needed. When a text box reveals one paragraph per click, PowerPoint also adds an effect for the box itself; delete it, or the first click shows nothing. [powerpoint-checks.md](powerpoint-checks.md) does this for you.

An answer hidden behind a reveal should also be available in the teacher's notes. Maintain a readable final state and an understandable PDF/static export. Do not replace native motion with a macro or speculative XML timing patch. If a later user explicitly requests another method, use a copy and verify it end to end.

## Verify and communicate

Check the exported package retains expected transitions and animation targets. When slideshow playback is available, verify initial state, click order, grouping, duration, and final state on representative slides. Static previews cannot establish animation behavior. If only structural inspection is possible, describe that narrower verification accurately. Automating PowerPoint's slideshow failed in testing, so on Windows confirm the saved effects with [powerpoint-checks.md](powerpoint-checks.md) and ask the teacher to press F5 and click through.

If the tool cannot implement motion, finish the deck and put a brief actionable plan in the relevant speaker notes, for example:

> Motion plan: Fade transition, 0.4 s, manual advance. The passage and question are visible initially. Click 1 reveals `interpretation`. Click 2 reveals `model-response`.

Identify this as a plan at handoff. Do not claim effects are implemented until they have actually been added and checked.
