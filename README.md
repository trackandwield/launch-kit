# Launch kit

Turn company intel and a feature brief into a full launch package, written in the company's brand voice, checked by a reviewer agent, and approved by the right people.

- **Foundation assets** (one set per product, refreshed from intel): ideal customer profile, buyer personas, a battlecard per competitor, competitive landscape, and the facts in the messaging framework.
- **Launch assets** (one set per brief, sized by launch tier): positioning, blog post, release notes, sales one-pager, social posts, launch email, landing page copy, sales talk track, internal FAQ, demo video script, press release, and a pitch deck filled into the company's own slide template.

The full list, with each asset's inputs, owner and approvers, is in `kit/assets.yaml`.

> **Demo content is unofficial.** The demo uses Loom, a real Atlassian product, with public facts and Atlassian's public writing guidelines. The launches are invented for practice. Nothing here is an Atlassian announcement, and this project isn't affiliated with Atlassian.

## How it works

1. **Brief:** a product manager fills in a copy of `kit/brief-template.yaml`: what's launching, who it's for, proof with sources, limitations and availability.
2. **Positioning first:** a writer agent drafts the launch positioning from the brief and the product's messaging framework. The marketer approves it.
3. **Assets:** writer agents draft the other five assets from the approved positioning, following each asset's spec and the brand's voice rules.
4. **Review:** a reviewer agent checks voice, the spec, and that every claim traces to the brief or the framework. The writer revises once.
5. **Approval:** the marketer approves, edits or rejects each asset, and every decision is logged.
6. **Proof:** drafts are scored with [model-bench](https://github.com/trackandwield/model-bench), and the marketer rates how much editing each asset needed.

The agents state only facts from the brief or the framework. When a brief is missing something, they name the gap instead of filling it.

## What's here

The kit is company-agnostic. Everything reusable lives in `kit/`; each company and product gets its own folder, and a brief names which one it's for.

| Path | What it is |
|---|---|
| `kit/rules.md` | Rules for every company: facts only from the brief and framework, name gaps, the disclaimer, banned words |
| `kit/brief-template.yaml` | The brief every launch fills in |
| `kit/company-template.yaml` | What a new company folder needs |
| `companies/<company>/company.yaml` | Company name, brand file paths and disclaimer |
| `companies/<company>/brand/` | The company's voice, tone and style rules, plus real examples to learn from |
| `companies/<company>/products/<product>/messaging-framework.md` | The product's facts (with sources), positioning, pillars and personas |
| `companies/<company>/products/<product>/briefs/` | Launch briefs for that product |
| `kit/assets.yaml` | Every asset: inputs, tiers, format, owner and approvers |
| `docs/workflow.md` | Launch manifests, asset states and approvals, designed for a project manager agent |
| `docs/intel-contract.md` | The intel files the kit reads, so any source can feed it |
| `docs/deck-templates.md` | How decks get filled without losing the company's style |
| `docs/decision-log.md` | Why things are the way they are |

**Demo:** `companies/atlassian/products/loom/` has five practice briefs. Tier 1 gets all six assets, tier 2 skips positioning, tier 3 gets release notes and social only. Brief 5 is deliberately incomplete.

### Add a company or product

1. Copy `kit/company-template.yaml` to `companies/<company>/company.yaml` and add the brand files it points to.
2. Write `companies/<company>/products/<product>/messaging-framework.md`, using Loom's as the model.
3. Copy `kit/brief-template.yaml` into that product's `briefs/` folder and fill it in.

## Status

| Step | State |
|---|---|
| 1. Messaging framework and brief template | Drafted; awaiting PMM review |
| 2. Asset specs | Not started |
| 3. Writer agent for one asset (blog post) | Not started |
| 4. Reviewer agent | Not started |
| 5. All six assets, positioning first | Not started |
| 6. Human approval | Not started |
| 7. Evaluation | Not started |
| 8. Case study and demo | Not started |
