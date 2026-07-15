# Node App Template

A map of your stuff, drawn as a web of connected dots. You pick a question, your AI assistant fills the map from one of your apps, and you get a single file you can open, explore, and share. Click any dot and a panel slides in with the story: what it is, why it is on the map, and a button to open the real thing.

The map itself is one HTML file: no coding, nothing to install, no account. The assistant that builds it is the one thing you set up.

## Open the template first

Double-click `node-app-template.html`. What opens is the guide: a starter map whose dots teach you how to use the template itself. Where to download the app, what you can connect, prompts worth copying, articles worth reading, all with links to real sources. Drag to move, scroll to zoom, tap a dot, try the filter buttons.

This starter map never goes away. When your assistant builds your maps, it copies the template and fills in the copy. The original stays in the folder as your permanent reference.

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

> Read the AGENT-INSTRUCTIONS.md in this folder. Then look through my [app] and build me a version of node-app-template.html that answers this question: [your question]. Save it as a new file next to the template, and leave the template itself untouched.

Your assistant reads the instructions file, pulls from your app, and writes a new HTML file into this same folder. Double-click it. Done.

## Example prompts

Steal one of these and swap in your own question. Every one ends the same way on purpose: new file, template untouched.

**From Google Drive**
> Read AGENT-INSTRUCTIONS.md in this folder. Scan my Google Drive folder called "Research" and build a node map answering: what have I already collected about community gardens, and how does it connect? Each dot should link back to the Drive file. Save the map as a new file in this folder and leave node-app-template.html untouched.

**From email**
> Read AGENT-INSTRUCTIONS.md in this folder. Look through my email from the last six months and build a node map of the people and organizations involved in the school fundraiser, grouped by how they are involved. Only include people I would be comfortable showing on a shared screen. Save the map as a new file in this folder and leave node-app-template.html untouched.

**From your calendar**
> Read AGENT-INSTRUCTIONS.md in this folder. Look at my calendar for this year and build a node map answering: where does my time go? Group recurring commitments, one-offs, and travel. Save the map as a new file in this folder and leave node-app-template.html untouched.

**From your notes app**
> Read AGENT-INSTRUCTIONS.md in this folder. Go through my notes and build a node map of every idea I have written down for the podcast, grouped by how ready each one is. Save the map as a new file in this folder and leave node-app-template.html untouched.

**From your bookmarks or read-later app** (works when your bookmarks app appears in the connectors directory)
> Read AGENT-INSTRUCTIONS.md in this folder. Go through my saved bookmarks and build a node map answering: which of my saved links would help me start a small business? Group them by what stage they help with. Save the map as a new file in this folder and leave node-app-template.html untouched.

## Tips for a good map

- **One question per map.** A map of everything is noise.
- **15 to 40 dots reads best.** Ask your assistant to pick the most relevant items, not all of them.
- **The "why" is the good part.** Each dot carries one or two sentences on why it belongs. Ask your assistant to make those sentences specific to your question.
- **Iterate out loud.** "Add a group for tools," "drop the ones older than 2024," "make the links open in Drive." Your assistant edits the same file.
- **A red or amber badge in a map's corner means the layout broke somewhere.** Ask your assistant to fix it.

## Privacy, worth thirty seconds

The map is a plain file on your computer. Nothing in it goes online by itself. But everything your assistant writes into it is inside that file, including names, email addresses, and private links if you asked for them. Before you send a map to anyone, open it and read the panels. If it includes other people, include only what they would be comfortable with.

## What is in this folder

| File | What it is |
|---|---|
| `node-app-template.html` | The template and the guide in one. Opens as a getting-started map; your assistant copies it to build yours. |
| `AGENT-INSTRUCTIONS.md` | Instructions written for your AI assistant. You never need to read it, but you can. |
| `README.md` | This file. |
| `LICENSE` | MIT. Copy it, adapt it, share it. |

## Where this came from

This template is the distilled form of a family of relational maps: an email network drawn around one person, a document library drawn around a research spec, and a bookmark collection drawn around the same spec. The engine and the click-a-dot-read-the-story pattern survived all three. The personal data did not come along.
