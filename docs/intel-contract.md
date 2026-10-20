# Intel contract: the files the kit reads

The kit never calls the intel engine. It reads an export, so any source that writes these files can feed it:

- `companies/<company>/products/<product>/intel/` when the research is about one product (Loom), which is the usual case for a launch;
- `companies/<company>/intel/` when it's about the whole company.

The first source is [competitive-intel-engine](https://github.com/trackandwield/competitive-intel-engine):

```
python -m engine.kit_export atlassian-loom --kit ../launch-kit
```

It sends only what the launch is about (Loom's plans and stories, not Jira's) and leaves out rejected rows. Rows nobody has reviewed yet go over as `status: proposed` unless it's run with `--active-only`; the writer may use them, but the reviewer flags any claim that rests only on proposed rows.

| File | One row per | Columns the kit uses | Feeds |
|---|---|---|---|
| `companies.csv` | the company and each competitor | id, name, website, relation, tier, why, description, problem, categories, buyer, size, business_model, customers | battlecard, competitive_landscape, icp |
| `products.csv` | product | id, company, name, description, categories, competes_with, pricing_url | framework_facts, battlecard |
| `plans.csv` | pricing plan | company, product, name, price, unit, billing, audience, limits, url | framework_facts, battlecard, competitive_landscape |
| `customer_stories.csv` | case study | company, customer, industry, size, region, products, problem, outcome, champion, quote, url | icp, personas |
| `reviews.csv` | review theme | company, kind (strength or weakness), theme, claim, quotes, source_urls | battlecard, talk_track, personas |
| `compliance.csv` | certification or control | company, category, item, detail, quote, source_url | framework_facts, battlecard |
| `perspectives.csv` | thing a company's people have said | person, company, theme, claim, quote, source_url | personas |
| `brand.json` | the company | colors, fonts, logos, voice | brand folder, deck template |
| `export.yaml` | the export | source tool, exported_at, subject, row counts | freshness checks |

Every row keeps its `source` (or `url`/`source_url`) and `confidence`. The writer cites them; the reviewer drops any claim whose row has no source. `exported_at` tells the project manager agent when foundation assets are stale and should be refreshed.
