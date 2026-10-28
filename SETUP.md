# Setup and troubleshooting

The skill works with any AI assistant that supports **skills**: folders containing a `SKILL.md` file, in the open Agent Skills format. That includes WorkBuddy, Kimi Code, Qwen Code, CodeBuddy, Trae, Codex and many others. Nothing in the kit belongs to one assistant.

## What you need

- **An assistant that can work with files on your computer**, usually its desktop app or command-line version. A web chat that cannot open your folders cannot use the kit's layouts and images.
- **A way to make PowerPoint files.** Many assistants have a presentation tool. If yours does not but can run code, it can write the file with a PowerPoint library such as python-pptx (Python) or pptxgenjs (Node.js). If it can do neither, it can only give you a slide plan.
- **PowerPoint or another presentation editor** to open and adapt the decks. Use desktop PowerPoint for the motion pilot's documented workflow.
- **Georgia and Arial** on the computer that makes the deck and the one that presents it. See [FONT-GUIDE.md](FONT-GUIDE.md).

You can also copy slides and use the images by hand, without any assistant.

## Three ways to start

### A. Try it straight from the kit folder

Extract the ZIP. In your assistant, open the extracted **AE Humanities - Coworker Kit** folder as the working folder (some assistants call it a project or workspace). Paste the first-run prompt from [START-HERE.md](START-HERE.md); it tells the assistant to read the skill from inside the kit. This works even in an assistant without a skills feature. Keep your source material and new lessons in a folder the assistant can open.

### B. Ask your assistant to install it (easiest)

Extract the ZIP, then paste this, changing the path to where your kit folder is. If you used GitHub's **Download ZIP** button, the folder is called `ae-humanities-coworker-kit-main`:

```text
Please install the skill in this folder: C:\Users\[your name]\Downloads\AE Humanities - Coworker Kit\artifact-template-ae-humanities-ppts

Copy the whole folder, keeping its name and everything inside it, into your personal skills folder so I can use it in every project. Do not change any files. Then tell me where you put it, and check that you can see a skill named artifact-template-ae-humanities-ppts.
```

Then start a new chat or session (restart the app if it asks) and ask: "Which skills can you use?" The list should include `artifact-template-ae-humanities-ppts`.

If your assistant can download from the internet, you can skip the ZIP altogether: paste the install prompt from [README.md](README.md), which points the assistant at the kit on GitHub (https://github.com/leckwallnut/ae-humanities-coworker-kit).

### C. Copy the folder yourself

Copy the **entire** folder named `artifact-template-ae-humanities-ppts` into your assistant's skills folder from the table below. Afterwards, `SKILL.md` must sit directly inside that folder, for example `...\skills\artifact-template-ae-humanities-ppts\SKILL.md`. Copy the skill folder, not the outer kit folder and not only SKILL.md, and do not rename anything inside it.

| Assistant | Personal skills folder | After copying | Source |
| --- | --- | --- | --- |
| Kimi Code | `~/.kimi-code/skills/` or `~/.agents/skills/` | Start a new session. | [Kimi Code docs](https://www.kimi.com/code/docs/en/kimi-code-cli/customization/skills.html) |
| Qwen Code | `~/.qwen/skills/` | Restart Qwen Code. | [Qwen Code docs](https://qwenlm.github.io/qwen-code-docs/zh/users/features/skills/) |
| CodeBuddy, and WorkBuddy's command-line version | `~/.codebuddy/skills/` | Type `/skills` to list loaded skills. | [CodeBuddy docs](https://www.codebuddy.ai/docs/cli/skills) |
| WorkBuddy desktop app | `~/.workbuddy/skills/` | Restart WorkBuddy if the skill does not appear. Method B also works well here. | Community guides; no official page found |
| Trae | Use **Settings → Rules and Skills (规则和技能)**, or method B | Check the skill appears in that list. | Community guides; not confirmed in official docs |
| Codex | `~/.agents/skills/` | Restart Codex if the skill does not appear. | [OpenAI docs](https://learn.chatgpt.com/docs/build-skills) |
| Any other assistant with skills | Try `~/.agents/skills/`, a shared folder several assistants read | Otherwise check its documentation, or ask it where it loads skills from. | [agentskills.io](https://agentskills.io) |

Folder locations were checked on 28 October 2026. These assistants change quickly, so if a folder is not recognised, ask the assistant itself where it loads skills from. If you use WorkBuddy's desktop app and its command-line version, they may keep separate skill folders.

**What `~` means:** your own home folder. On Windows that is `C:\Users\[your name]` (also written `%USERPROFILE%`); on a Mac it is `/Users/[your name]`. Folders whose names begin with a dot, such as `.agents`, are hidden: turn on "Show hidden items" in File Explorer, or let the assistant do the copying (method B).

On Windows, these PowerShell lines create the shared folder and copy the skill into it. Change the first line to where you extracted the kit, and the second if your assistant uses a different folder:

```powershell
$kit = "$env:USERPROFILE\Downloads\AE Humanities - Coworker Kit"
$dest = "$env:USERPROFILE\.agents\skills"
New-Item -ItemType Directory -Force $dest | Out-Null
Copy-Item -Recurse "$kit\artifact-template-ae-humanities-ppts" $dest
```

On a Mac:

```bash
mkdir -p ~/.agents/skills
cp -R "AE Humanities - Coworker Kit/artifact-template-ae-humanities-ppts" ~/.agents/skills/
```

**Keep one copy.** If you use several assistants, install the skill in one shared folder such as `~/.agents/skills/` where they support it, instead of keeping copies that drift apart. Before replacing an older version, move it to a backup folder outside any skills folder.

## Using the skill

Plain words work in every assistant:

```text
Use the AE Humanities PPTs skill (artifact-template-ae-humanities-ppts) to create my Humanities lesson from the attached material.
```

Many assistants also choose the skill by themselves when you ask for an AE Humanities or dark academia lesson. Some have a shortcut as well: `/skill:artifact-template-ae-humanities-ppts` in Kimi Code, `/artifact-template-ae-humanities-ppts` in CodeBuddy and `$artifact-template-ae-humanities-ppts` in Codex. Ready-made prompts are in [STARTER-PROMPTS.md](artifact-template-ae-humanities-ppts/STARTER-PROMPTS.md).

## Check the first result

Run the first-run test from [STARTER-PROMPTS.md](artifact-template-ae-humanities-ppts/STARTER-PROMPTS.md) and compare it with [what a good first-run result looks like](artifact-template-ae-humanities-ppts/references/first-run-check.md). In particular:

1. The assistant can find `assets/teaching-layouts.pptx`, the image library and the selected images without the original creator's computer or chats.
2. The deck opens, its text is editable, and the intended fonts are available. The layout library and sample lesson have embedded artwork.
3. Slide text is readable, nothing is cut off or runs across busy artwork, and required source images remain intact. Check the deck in slideshow mode.
4. If you use motion, check the starting state and every click in the exact file you will present. A PDF preview cannot show animation.

## Common fixes

| Problem | Action |
| --- | --- |
| The skill is missing | Check that `SKILL.md` sits directly inside `artifact-template-ae-humanities-ppts`, inside the skills folder. Start a new session or restart the assistant. Or use method A. |
| The assistant has no skills feature | Use method A: open the kit folder and paste the first-run prompt. |
| Pictures cannot be found | Extract the whole package and keep `assets/`, `references/` and SKILL.md together. Do not copy only the markdown file. |
| The assistant refers to another computer | Ask it to find every file inside the installed skill folder, using the relative paths in the catalogs. No creator-specific paths are needed. |
| No PowerPoint file is produced | Ask the assistant to build the deck with python-pptx or pptxgenjs if it can run code. Otherwise use the editable layout deck by hand. A slide plan is not a finished PPTX. |
| Text changes after opening | Check that the fonts are installed, use one consistent font pair, and inspect wrapping after any substitution. |
| Text is too small | Split the content or use a quiet surface. Do not shrink the whole passage to make it fit. |
| Text fits in the preview but not in PowerPoint | Previews that substitute Georgia misreport fit. On Windows with desktop PowerPoint, use [the PowerPoint checks](artifact-template-ae-humanities-ppts/references/powerpoint-checks.md). |
| Animations disappear | Return to the preserved animated PPTX. Finish the static deck before adding motion, then test the final PowerPoint file using the pilot guide. |

## Package structure and portability

The skill follows the open [Agent Skills](https://agentskills.io) format: a folder with `SKILL.md`, whose header gives the skill's name and description, with details in `references/` and reusable artwork and decks in `assets/`. The `agents/openai.yaml` file is extra display information for Codex; other assistants ignore it.

All file references inside the skill are relative. Markdown links are relative to their document, and catalog paths beginning `assets/` are relative to the skill folder. The examples have no links to outside files, and generated lessons should embed the chosen artwork. No earlier chat, cloud drive or API key is needed.

The optional Extras download holds the original PNGs of the 62 opaque images, which the skill ships as high-quality JPEG copies, and the three visual guide PDFs. Nothing in the skill links to Extras, so coworkers who only install the skill can skip it.

The included package manifest records file hashes and counts. The package was checked after extraction to a different local folder, and the skill was used in Claude Code on Windows. Installation in each assistant listed above has not been tested; follow its documentation if anything differs. Assistant availability and font installation remain part of each coworker's setup.
