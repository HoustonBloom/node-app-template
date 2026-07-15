# Agent Instructions · Node App Template

Written for your AI assistant. If a human is skimming: the part worth your eyes is rule 4 of the contract, on people and privacy.

You are populating a self-contained HTML node map for a person who is not technical. Read this whole file before touching the template.

## What you are building

`node-app-template.html` is a single-file interactive map: a hub question at the center, items from the person's connected app arranged around it in colored groups, every item clickable. Clicking a node fills the side panel with the item's name, where it came from, one or two sentences on why it is on the map, and a button that opens the real thing. Filter chips isolate one group at a time. Pan, zoom, hover dimming, and mobile layout are already built.

Your job is content only. The engine does the rest.

## The contract

1. **Copy the template to a new file. Never modify `node-app-template.html` itself, for any reason.** The template ships as a getting-started map, and that content is the person's permanent guide to this whole system. Every map you build is a copy. Name the copy after the question, kebab-case: `recipes-for-a-crowd.html`. Save it in the same folder unless the person says otherwise. If the person asks you to "update" or "fix" the template, confirm they mean a copy first. One maintainer exception: whoever publishes this template may set `templateRepo` in CONFIG and delete that node's placeholder note line. That is the only sanctioned edit to the template file.
2. **Edit only SECTION 1** (marked `SECTION 1 · YOUR CONTENT` in the file). Everything below the `SECTION 2 · ENGINE` marker, including the layout audit block at the bottom, stays byte-identical.
3. **Every node must be real.** Each node comes from something you found in the person's connected app. Never invent items, counts, dates, or links. If a field is unknown, omit it.
4. **People are sensitive data.** If nodes are people, include only people the person asked for, and put nothing in a panel the person would not show on a shared screen. When in doubt, ask before writing.

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

### SOURCES and SOURCE_LEGEND (optional second filter)
When the map draws from more than one place (two apps, or an app plus the web), define `SOURCES` and give every node a `src` key. The person gets a second chip row to filter by source, each node's panel shows a source badge, and any source with a `ring` style ("solid", "dashed", or "dotted") wears that outline on the map; a source with no ring is a plain dot. Use one ring style per source, never two sources with the same style: plain vs solid vs dotted is what a reader can tell apart at a glance. Write `SOURCE_LEGEND` as one short line explaining the rings (follow the shipped example's "plain dot = ... · solid ring = ..." pattern). If everything comes from one place, set `SOURCES = {}` and the source row hides itself.

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
| `prompt` | no | copy-able prompt text; renders as a block with a working Copy button. Use for nodes that teach prompting. Any prompt that builds a map must end by instructing the agent to save a new file and leave node-app-template.html untouched |
| `note` | no | small print at the panel bottom |

Layout is computed automatically from `cluster` membership. Do not add `x`/`y`.

### EXTRA_LINKS
Every node is linked to the hub automatically. Add `["idA","idB"]` pairs only for real relationships between items worth showing.

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
4. Read the panels once as a stranger: any number you did not count, any claim you did not see in the source, any name the person might not want on a shared screen comes out now.
5. Tell the person the file name, the node count, and what you scoped out, in plain sentences.
6. If the person asks for changes, edit the same map file in place; do not rebuild from scratch and do not touch the template.
