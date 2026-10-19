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
