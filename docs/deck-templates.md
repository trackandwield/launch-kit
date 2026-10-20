# Filling a company's own deck without losing its style

**Goal:** take a sample deck in a company's branding, and reliably replace its content with a launch's content while keeping every layout, font, color, logo and image placement.

**Approach (to prove in a spike before building on it):**

1. **Map the template once.** Read the sample `.pptx` with python-pptx and list each slide layout and every text placeholder or text box on it (its name, position, size, font size and how much text it holds). Save that as `companies/<company>/deck/template-map.yaml`. A person confirms which slides are reusable (title, agenda, problem, solution, proof, pricing, comparison, CTA) and what each box is for.
2. **Write content to fit the boxes.** The writer agent gets the map, not the deck: for each slide it fills each named box, within a word limit derived from the box's size and font. It never adds or removes boxes.
3. **Replace text in place.** Copy the template slide, then replace the text in each box run by run, keeping the original run's formatting. Images, shapes and masters are never rebuilt, only copied.
4. **Check before a person sees it.** Render each slide to an image and flag overflow (text past its box), leftover sample text, and missing boxes. The reviewer agent also checks the words against the brand rules, like any other asset.

**Why not generate slides from scratch:** generated slides drift from the brand. Filling the company's own template keeps the design team's work intact, and design only has to approve the template map once.

**Open questions:** decks built from images of text (not editable), charts that need new data, and Google Slides (export to `.pptx` first, or use the Slides API).
