# Agent Instructions · Node App Template

Written for your AI assistant. If a human is skimming: the part worth your eyes is rule 5 of the contract, on people and privacy.

You are populating a self-contained HTML node map for a person who is not technical. Read this whole file before touching the template.

## What you are building

`node-app-template.html` is a single-file interactive map: a hub question at the center, items from the person's connected app arranged around it in colored groups, every item clickable.

Your job is content only. The engine does the rest, and because every map you build is a copy of this file, every map you build inherits all of it. You do not implement any of the following, and you do not remove any of it:

- **Tap a node and the view follows it.** The camera reframes to hold that node and everything it connects to, the node and its connections stay lit, and everything else fades back. Tapping the hub frames the whole map, so the hub is also the way back out. Tapping the background, or pressing Escape, returns to the resting view.
- **A selection outranks the filters.** With a group or source filter on, selecting a node pulls its connections back on screen even when the filter excluded them, so a person never sees a node with half its relationships hidden.
- **The panel lists real connections.** Each node's panel shows "Connected to" (the actual links you declared in `EXTRA_LINKS`) and "Same group" (its cluster siblings). Both lists are clickable and move the map.
- **Filters explain themselves.** Turn on a filter with nothing selected and the panel names the filter, counts what is in it, lists every item, and offers a way back to the whole map.
- **The rest.** Radial layout, pan, drag, scroll zoom, zoom buttons, hover dimming, label collision avoidance, clipboard copy for prompts, phone layout, and the layout audit at the bottom of the file.

## The contract

1. **Copy the template to a new file. Never modify `node-app-template.html` itself, for any reason.** The template ships as a getting-started map, and that content is the person's permanent guide to this whole system. Every map you build is a copy. If the person asks you to "update" or "fix" the template, confirm they mean a copy first. One maintainer exception: whoever publishes this template may set `templateRepo` in CONFIG and delete that node's placeholder note line. That is the only sanctioned edit to the template file.
2. **Save the copy next to the template, at the top level of this folder.** Same folder as `node-app-template.html` and this file, not a subfolder, not a scratch directory, not somewhere else on the person's disk. Name it after the question in kebab-case: `recipes-for-a-crowd.html`. The person opens their maps by double-clicking them, so every map they own sits in one place they already know. Put it elsewhere only if the person names the place. When you hand the map back, say where it is by folder and file name.
3. **Edit only SECTION 1** (marked `SECTION 1 · YOUR CONTENT` in the file). Everything below the `SECTION 2 · ENGINE` marker, including the layout audit block at the bottom, stays byte-identical. That block is what gives your map the behavior described above. Copying the file is the whole inheritance mechanism: nothing to install, nothing to wire up, and nothing to delete because it looks unused.
4. **Every node must be real.** Each node comes from something you found in the person's connected app. Never invent items, counts, dates, or links. If a field is unknown, omit it.
5. **People are sensitive data.** If nodes are people, include only people the person asked for, and put nothing in a panel the person would not show on a shared screen. When in doubt, ask before writing.

## What to replace in SECTION 1

### CONFIG
```js
var CONFIG = {
  kicker:   "Short eyebrow line",            // e.g. "My Drive · research scan"
  title:    "The question, as a title",      // e.g. "What do I already know about X?"
  subtitle: "One sentence on what this map shows and what tapping a node does.",
  relLabel: "Why it is on this map",         // heading above each node's explanation
  linkLabel:"Open the source &rarr;"         // default button text
};
```

### CLUSTERS and ORDER
Keep the `anchor` entry. Replace the rest with 2 to 6 groups that answer the question, each with a label, a distinct color, AND a distinct `shape` (circle, square, triangle, diamond, hexagon, star). The shape draws on the map and in the filter chips, so a color-blind reader can still tell groups apart. List every non-anchor key in `ORDER`; that sets the sectors around the hub.

**Pick colors for the dots, not for the text.** A group color is a large shape on the map, so choose what reads well there. The engine runs every text use of that color through `readable()`, which darkens it just enough to clear WCAG AA (4.5:1) on the panel background and behind button labels, and leaves it alone when it already passes. Panel text and buttons stay legible whatever palette you pick, and the dots keep the color you chose. Do not pre-darken your palette to compensate; that only dulls the map.

**Group labels name what the reader gets, not what you did.** "Start here", "Best practices", "Examples to try" tell someone where to go. "Miscellaneous", "Other", "Additional items" do not. One group may legitimately hold the long tail; the shipped map puts twelve of its twenty-three nodes in Additional resources, because splitting the tail into three thin groups made the reader choose between labels that meant nothing to them.

### SOURCES and SOURCE_LEGEND (a label, not a filter)
When the map draws from more than one place (two apps, or an app plus the web), define `SOURCES` and give every node a `src` key. Source is labelling only: each node's panel shows a source badge, any source with a `ring` style ("solid", "dashed", or "dotted") wears that outline on its dot, and one legend line under the chips explains the rings. Nothing filters by it.

That is deliberate. Groups are the one thing a person filters, so there is a single row of chips to understand and the first one they reach is the one that matters. Do not add a second filter row.

Use one ring style per source, never two sources with the same style: plain vs solid vs dotted is what a reader can tell apart at a glance. Write `SOURCE_LEGEND` as one short line (follow the shipped example's "plain dot = ... · solid ring = ..." pattern). If everything comes from one place, set `SOURCES = {}` and the source line hides itself.

### NODES
Exactly one node keeps `cluster:"anchor"`: it is the hub, and its `rel` states the question the map answers. Every other node:

| Field | Required | What goes in it |
|---|---|---|
| `id` | yes | unique short string |
| `cluster` | yes | one of your CLUSTERS keys |
| `src` | only when SOURCES is defined | one of your SOURCES keys |
| `title` | yes | full name, shown in the panel |
| `short` | yes | 1 to 3 words, drawn on the map itself |
| `sub` | no | provenance line: source app, author, or date |
| `rel` | yes | one or two sentences: why this item answers the map's question. Specific beats generic. |
| `href` | no | link the panel button opens (the Drive URL, the bookmark, the mailto) |
| `linkLabel` | no | per-node button text, e.g. `"Open in Drive &rarr;"` |
| `links` | no | extra links as `[{label, href}, ...]`; rendered as secondary buttons after the main one |
| `prompt` | no | copy-able prompt text; renders as a block with a working Copy button. Use for nodes that teach prompting. Write prompts as editable examples: brackets for the fill-ins, and a closing line telling the person the recipe is theirs to change. Any prompt that builds a map must end by instructing the agent to save a new file and leave node-app-template.html untouched |
| `note` | no | small print at the panel bottom |
| `next` | no | `{id, label}` renders a button that jumps to another node, clearing the filter if needed. The hub can carry one too, and should: it is the panel every reader lands on, so give it a `next` into the first step rather than leaving them to find it. Chain every step of a numbered sequence to the one after it, and point the last step at whatever the reader is meant to do with all of it. A step with no `next` is where the guided path stops |

Layout is computed automatically from `cluster` membership. Do not add `x`/`y`.

### EXTRA_LINKS
Every node is linked to the hub automatically. Add `["idA","idB"]` pairs only for real relationships between items worth showing.

This field carries more weight than its size suggests. A pair here does three things at once: it draws an edge on the map, it fills the "Connected to" list in both nodes' panels, and it widens the camera when either node is selected, since the view reframes to hold a node and everything it connects to. A map with no pairs still works, but every node reads as an island and selecting one just zooms to it and the hub.

So: walk the items once, ask which ones genuinely relate, and write those pairs. Two items by the same author, a document and the thread that produced it, a tool and the guide that explains it. Do not pair items merely because they share a group, since "Same group" already covers that, and do not manufacture pairs to make the map look busy. A relationship you cannot state in a sentence is not one.

## Quality bar

- **15 to 40 nodes.** Curate. If the app has 300 candidates, pick the ones that best answer the question and say in the subtitle what you scoped to.
- **`rel` carries the value.** "A guide about composting" is filler. "First thing to set up before anything goes in the ground" is a map worth reading. One to three sentences; put the useful part first; never restate the title.
- **Button labels say what the reader gets.** "Read the paper," "See the steps," "Open in Drive." Never "Open the link," "Open the repo," "Visit the org," or bare app jargon.
- **`sub` is provenance, `note` is honest caveats.** `sub` names where the item came from (source, author, date when known). `note` is for warnings the reader deserves: a paywall, a plan-gated feature, a link you could not verify.
- **Never state a number you did not count.** No "hundreds of files" unless you counted; no dates you did not see. Counts you did make are welcome and specific.
- **Only link what resolves.** Every `href` must be a URL you saw in the person's app or opened yourself. If something cannot be checked, say so in the `note` instead of linking anyway.
- **Number the `short` labels when order matters** ("1 · Connect", "2 · Pick a question"). Otherwise keep them to 1 to 3 words; they are what people see on the canvas.
- **`short` labels must not collide.** Same words on two dots reads as a bug.
- **Never encode meaning in color alone.** Every group pairs its color with a shape; every source pairs its panel badge with a ring style (plain, solid, dashed, dotted). The engine draws both everywhere; your job is to assign distinct pairs, one shape per group and one ring style per source.
- **No em dashes anywhere.** Use periods, commas, colons, or a spaced middot. No filler intensifiers (very, really, actually), no exclamation marks.
- **HTML entities in strings are fine** (`&rarr;`, `&middot;`). The engine escapes node text; CONFIG strings render as HTML.

## Verify before you hand it back

Build in ONE pass: read the source app once, curate, write the file, then run this check. Do not spawn subagents, review panels, or extra research loops; the person is paying for your tokens, and the built-in audit plus one honest read-through is enough.

1. Open the new file in a browser from disk (double-click or `file://`).
2. The built-in layout audit runs automatically on `file://` and shows a red or amber pill bottom-left if the layout breaks, including at phone width. No pill means clean. Fix anything it flags.
3. Click the hub, one node per group, and one filter chip. Confirm every `href` opens the right thing and every button label says what the reader gets.
4. Click a node that has an `EXTRA_LINKS` pair. The camera should reframe to hold it and its connections, and "Connected to" should list them. Click the background to come back out. If a panel shows no "Connected to" section anywhere in the map, you wrote no pairs; go back and ask whether that is true.
5. Read the panels once as a stranger: any number you did not count, any claim you did not see in the source, any name the person might not want on a shared screen comes out now.
6. Tell the person where the file is (folder and file name), the node count, and what you scoped out, in plain sentences. Say that it opens by double-clicking, and that it sits next to the getting-started map with any others they have made.
7. If the person asks for changes, edit the same map file in place; do not rebuild from scratch and do not touch the template.
