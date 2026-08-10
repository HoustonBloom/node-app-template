# Node App Template

> **Download this folder and double-click `START-HERE.html`. That file is the documentation.**
> It opens as a map you can click through, and it teaches the whole system by being a working
> example of it. This README is the short version for people who want to read before they click.

A map of your stuff, drawn as a web of connected dots. You pick a question, your AI assistant fills the map from one of your apps, and you get a single file you can open, explore, and share.

Tap any dot and two things happen. A panel slides in with the story: what it is, why it is on the map, what it connects to, and a button to open the real thing. And the map itself moves, pulling back to hold that dot and everything joined to it while the rest fades. Tap the middle dot to see the whole map again, or tap the background to come back out.

The map itself is one HTML file: no coding, nothing to install, no account. The assistant that builds it is the one thing you set up.

## `START-HERE.html` is the guide, and it is also the template

That one file does both jobs, which is the part worth understanding before anything else.

**As the guide,** it opens as a starter map whose dots teach you how to use this system. Where to download the app, what you can connect, prompts worth copying, articles worth reading, all with links to real sources. Drag to move, scroll to zoom, tap a dot, tap the background to come back out. The quickest way through it is the button in the middle panel: it starts you at step 1 and every step hands you to the next, ending at four examples you can copy.

**As the template,** it is what your assistant copies. Every map you ask for is a duplicate of `START-HERE.html` with your own material poured into it, which is why your maps behave exactly like the starter one: same clicking, same zooming, same panels. The original is never edited and never goes away, so it stays your permanent reference no matter how many maps you build.

Every map your assistant makes lands right here too, in this same folder, next to the template. That is the rule the instructions give it. So this folder becomes the shelf your maps live on: one place, all double-clickable, no hunting. Anything the starter map does, your maps do, because each one is a copy of it.

One housekeeping note: if this folder arrived as a .zip, extract it before anything else. Maps built inside an unextracted zip get lost.

## What you need

1. **An AI desktop app.** Claude or ChatGPT. This template is not an app; it runs on whichever assistant you use. The desktop version matters because it can work with files on your computer, and this template is a file. On Claude, that file work happens in Cowork or Claude Code. On ChatGPT, it happens in a Codex session inside the desktop app.
2. **One of your apps connected to that assistant.** This is the key move. Assistants can connect to the apps you already use: Google Drive, Gmail, your calendar, Notion, and many more. In Claude, add them in Settings under Customize, then Connectors. ChatGPT calls them apps and keeps its own page in settings. Connect one app and your assistant can read what is in it.
3. **This folder.** If you are reading this file, you have it. If someone only showed you the map, ask them for a copy. A download link will live on the map's "Get the template" dot once the template has a public home.

**What it costs, honestly.** Both apps download free, but neither free plan finishes the whole job. On Claude, connecting Google apps is free; writing the map file needs a paid plan (Cowork or Claude Code, Pro and up). On ChatGPT it is the reverse: writing files works on the free desktop app through Codex, and the Google connectors need a paid plan. Plans shift; check the pricing pages before you commit. Checked July 14, 2026.

That is the whole idea of this template: **connect an app, then ask your assistant to draw what it finds.**

## How to use it, in three steps

1. **Connect one app** to your assistant (see above).
2. **Pick one specific question.** Not "map my Drive." Something with a point of view: "which of my saved recipes could feed twelve people?" A map of everything is noise.
3. **Point your assistant at this folder and give it a prompt.** In Claude, open Cowork and choose this folder when it asks where to work. In ChatGPT's desktop app, start a Codex session and pick this folder. Then say something like:

> Read the AGENT-INSTRUCTIONS.md in this folder. Then look through my [app] and build me a version of START-HERE.html that answers this question: [your question]. Save it as a new file next to the template, and leave the template itself untouched.

Your assistant reads the instructions file, pulls from your app, and writes a new HTML file into this same folder. Double-click it. Done.

## Example prompts

These four are working recipes, not hypotheticals: each one is a map that has been built and used. Steal one, fill in the brackets, and edit any line to fit how you work. They all end the same way on purpose: new file, template untouched.

**How does this connect to my work?** (works with any connector you have)
> Read AGENT-INSTRUCTIONS.md in this folder. First ask me to describe my work in a few sentences, and make that the hub. Then go through my [app] and build me a version of START-HERE.html answering: how does what I have saved connect to my work? Group items by the part of my work they touch, write each node's explanation as the specific connection, and link every node to its source. Save the map as a new file in this folder. Leave START-HERE.html untouched. This prompt is one specific recipe: change the app or the grouping to fit.

**Keep up with your collaborators** (needs an email connector; Gmail works in Claude and ChatGPT)
> Read AGENT-INSTRUCTIONS.md in this folder. Then look through my email from the last [three months] and build me a version of START-HERE.html mapping the people and organizations active around [my project], grouped by what each is working on with me. Note each person's last thread and when it happened. Include only people I would be comfortable showing on a shared screen. Save the map as a new file in this folder. Leave START-HERE.html untouched. This prompt is one specific recipe: change the time window, the project, or the grouping to fit.

**Synthesize a Drive folder of research** (needs the Google Drive connector)
> Read AGENT-INSTRUCTIONS.md in this folder. Then go through my Google Drive folder [folder name] and build me a version of START-HERE.html answering: what does this library already say about [my question]? Group documents by theme, give each node one or two sentences on what that document contributes, and link every node to its file in Drive. Save the map as a new file in this folder. Leave START-HERE.html untouched. This prompt is one specific recipe: swap the folder, the question, or the grouping to fit.

**Surface what your community is saving** (needs a bookmarking or feed connector, like Pinboard or RSS)
> Read AGENT-INSTRUCTIONS.md in this folder. Then pull the recent links saved by [my community's Pinboard account, shared tag, or RSS feed] and build me a version of START-HERE.html answering: what is my community reading right now, and how does it relate to [our shared work]? Group links by theme, credit who saved each one, and link every node to the original. Save the map as a new file in this folder. Leave START-HERE.html untouched. This prompt is one specific recipe: point it at a different feed or question any time.

## Tips for a good map

- **One question per map.** A map of everything is noise.
- **15 to 40 dots reads best.** Ask your assistant to pick the most relevant items, not all of them.
- **The "why" is the good part.** Each dot carries one or two sentences on why it belongs. Ask your assistant to make those sentences specific to your question.
- **Iterate out loud.** "Add a group for tools," "drop the ones older than 2024," "make the links open in Drive." Your assistant edits the same file.
- **A map is a snapshot, so make refresh a routine.** The data is only as current as the day it was drawn. Claude and ChatGPT can both run scheduled tasks that refresh a map on a rhythm; the "Refresh routine" dot on the starter map shows how.
- **A red or amber badge in a map's corner means the layout broke somewhere.** Ask your assistant to fix it.

## Privacy, worth thirty seconds

The map is a plain file on your computer. Nothing in it goes online by itself. But everything your assistant writes into it is inside that file, including names, email addresses, and private links if you asked for them. Before you send a map to anyone, open it and read the panels. If it includes other people, include only what they would be comfortable with.

## What is in this folder

| File | What it is |
|---|---|
| `START-HERE.html` | The template and the guide in one. Opens as a getting-started map; your assistant copies it to build yours. |
| `AGENT-INSTRUCTIONS.md` | Instructions written for your AI assistant. You never need to read it, but you can. |
| `README.md` | This file. |
| `LICENSE` | MIT. Copy it, adapt it, share it. |
| your maps | Everything your assistant builds arrives here as its own `.html`, named after the question it answers. |

## Where this came from

This template is the distilled form of a family of relational maps: an email network drawn around one person, a document library drawn around a research spec, and a bookmark collection drawn around the same spec. The engine and the click-a-dot-read-the-story pattern survived all three. The personal data did not come along.
