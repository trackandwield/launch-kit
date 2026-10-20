# Filling a company's own deck without losing its style

**Goal:** take a sample deck in a company's branding, and reliably replace its content with a launch's content while keeping every layout, font, color, logo and image placement.

**Approach (tested in the spike below):**

1. **Map the template once.** Read the sample `.pptx` with python-pptx and list each slide layout and every text placeholder or text box on it (its name, position, size, font size and how much text it holds). Save that as `companies/<company>/deck/template-map.yaml`. A person confirms which slides are reusable (title, agenda, problem, solution, proof, pricing, comparison, CTA) and what each box is for.
2. **Write content to fit the boxes.** The writer agent gets the map, not the deck: for each slide it fills each named box, within a word limit derived from the box's size and font. It never adds or removes boxes.
3. **Replace text in place.** Copy the template slide, then replace the text in each box run by run, keeping the original run's formatting. Images, shapes and masters are never rebuilt, only copied.
4. **Check before a person sees it.** Render each slide to an image and flag overflow (text past its box), leftover sample text, and missing boxes. The reviewer agent also checks the words against the brand rules, like any other asset.

**Why not generate slides from scratch:** generated slides drift from the brand. Filling the company's own template keeps the design team's work intact, and design only has to approve the template map once.

**Open questions:** decks built from images of text (not editable), charts that need new data, and Google Slides (export to `.pptx` first, or use the Slides API).

## Spike result (2026-10-19)

It works on a stand-in template. `tools/deck.py` maps, fills and checks; the Loom auto-translate deck went from template to a clean check in two versions.

| Step | Command | Output |
|---|---|---|
| Map | `python tools/deck.py map TEMPLATE MAP` | `companies/atlassian/deck/template-map.yaml`: 126 boxes on 9 slides, including table cells and boxes inside groups |
| Mark | a person edits the map | `use` per slide; `keep: true` on boxes to leave alone (step labels, agenda numbers); `chrome: true` boxes are set once per deck |
| Write | the writer fills a content file | `launches/loom-auto-translate/pitch_deck/v2.content.yaml`: text per box key, `null` deletes a box, `chrome` sets logo text, footer and page numbers |
| Fill | `python tools/deck.py fill TEMPLATE CONTENT OUT` | the `.pptx`; unused slides dropped, slides in the content's order |
| Check | `python tools/deck.py check TEMPLATE MAP CONTENT OUT REPORT` | a JSON report; fails on overflow, a one-line box that now wraps, a box left unfilled, leftover sample words, or a box whose font, size, weight or color changed |

What the check caught on the way:
- **v1:** the CTA button's URL wrapped onto two lines (`v1.check.json`). v2 puts the URL in the text above and the button says "Try auto-translate".
- **YAML trap:** a table cell written as `Yes` was read as true and printed "True". `fill` now refuses true/false values and asks for quotes.
- **Sample text matching new text** (for example "How it works") is not leftover; the check flags boxes the content didn't fill, plus words from the sample content listed in `leftover_words`.

Limits found, for the next round:
- Sizes are measured with Arial metrics. A template in its own font needs that font file for measuring.
- Slides can be dropped and reordered but not repeated yet (two comparison slides need slide copying).
- Page numbers are plain text boxes here; real templates often use a field in the master, which needs no filling.
- Rendering for review needs LibreOffice (`soffice --headless --convert-to pdf`).
- Not yet tried on a real company template. The stand-in is built like designer decks (default box names, groups, tables), but a real one will have its own surprises.
