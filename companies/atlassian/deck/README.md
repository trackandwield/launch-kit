# Atlassian deck template (stand-in)

No official Atlassian slide template is public: Atlassian shares its own on request, and partner templates sit behind sign-in. `sample-template.pptx` is a stand-in in Atlassian's public colors, built the way designer decks usually are (free text boxes with default names, shapes, a grouped element, tables, a footer on every slide), so the fill-in test meets the same problems a real deck has.

Rebuild it with `python tools/make_sample_deck.py companies/atlassian/deck/sample-template.pptx`. Swap in a real company deck the same way: drop the `.pptx` here and map it (see `docs/deck-templates.md`).

Its sample content is about a made-up product, "Pipeline Pulse", so any leftover sample text in a filled deck is easy to catch.
