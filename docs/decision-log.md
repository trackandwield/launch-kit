# Decision log

## 2026-10-19: practice on a real product, Loom by Atlassian
- **Choice:** build the kit against a real company's public facts and brand rules instead of a fictional company.
- **Why:** writing in a real brand's voice is the actual job, and Atlassian publishes its voice, tone and grammar rules ([voice and tone](https://atlassian.design/foundations/content/voice-tone), [language and grammar](https://atlassian.design/foundations/content/language-and-grammar)). Loom has public plans, prices and an AI feature list to build launches on.
- **Trade-off:** the launches are invented, so every asset carries an "unofficial concept, not an Atlassian announcement" footer, invented numbers are marked hypothetical in the brief, and contacts are fictional roles. Atlassian's marketing voice guide is internal, so marketing-specific style comes from published Loom launch posts.
- **Rejected:** a fictional company (Acme Observe, from the model bench). Easier, but it would only show generic copywriting.

## 2026-10-19: brand rules live in one folder per company
- **Choice:** `brand/<company>/` (now `companies/<company>/brand/`, see below) holds the voice rules and style references; the writer and reviewer skills read whichever brand the brief names.
- **Why:** the same skills can write for another company by adding a folder, which is the point of a kit.

## 2026-10-19: company-agnostic layout
- **Choice:** split the repo into `kit/` (rules, templates and, later, specs and skills that work for any company) and `companies/<company>/` (brand rules, disclaimer, and one folder per product with its framework and briefs). Each brief names its company and product.
- **Why:** Hal wants to run the same workflow on other products. With this split, adding a product means adding files, not changing the kit.
- **Rule of thumb:** if a file mentions a specific company or product, it belongs under `companies/`; otherwise it belongs under `kit/`.

## 2026-10-19: foundation and launch assets, intel from the engine
- **Choice:** two layers of assets. Foundation assets (ICP, personas, battlecards, competitive landscape, framework facts) are built per product from intel; launch assets are built per brief on top of them. Added landing page copy, sales talk track, internal FAQ, demo video script, press release and pitch deck to the original six.
- **Why:** launch assets are only as good as what they know about the buyer and the competition. Building that once per product means every launch reuses it.
- **Intel:** the competitive-intel-engine only gathers and tracks facts. The kit builds every asset, battlecards included, so everything goes through the same review and approval. The kit reads an export (`docs/intel-contract.md`), not the engine's internals.

## 2026-10-19: design for a project manager agent from the start
- **Choice:** every asset names an owner role and approver roles (`kit/assets.yaml`), and each launch will have a manifest that tracks state, versions and every decision (`docs/workflow.md`).
- **Why:** Hal wants an agent to run the process later: tracking progress, who is responsible, and getting human sign-off. If the kit records state the same way from day one, that agent reads the manifest instead of the kit being rebuilt around it.

## 2026-10-19: pitch decks fill the company's own template
- **Choice:** map a sample deck's layouts and text boxes once, write content to fit each box, and replace text in place (`docs/deck-templates.md`).
- **Why:** generated slides drift from the brand; filling the real template keeps it. To be proven in a spike before the deck asset is built.

## 2026-10-19: Test deck filling on a stand-in Atlassian template

No official Atlassian slide template is public (shared on request; partner templates need sign-in), and GitHub's published one is staff-only. We built a stand-in in Atlassian's public colors, structured like a designer deck, and proved map, fill and check on it with the Loom auto-translate deck. A real company template replaces it when one is available.
