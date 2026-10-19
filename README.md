# Launch kit

Turn one feature brief into a full launch package (positioning, blog post, release notes, sales one-pager, social posts and launch email), written in a company's brand voice, checked by a reviewer agent, and approved by a product marketer.

> **Demo content is unofficial.** The demo uses Loom, a real Atlassian product, with public facts and Atlassian's public writing guidelines. The launches are invented for practice. Nothing here is an Atlassian announcement, and this project isn't affiliated with Atlassian.

## How it works

1. **Brief:** a product manager fills in `briefs/brief-template.yaml`: what's launching, who it's for, proof with sources, limitations and availability.
2. **Positioning first:** a writer agent drafts the launch positioning from the brief and the company's messaging framework. The marketer approves it.
3. **Assets:** writer agents draft the other five assets from the approved positioning, following each asset's spec and the brand's voice rules.
4. **Review:** a reviewer agent checks voice, the spec, and that every claim traces to the brief or the framework. The writer revises once.
5. **Approval:** the marketer approves, edits or rejects each asset, and every decision is logged.
6. **Proof:** drafts are scored with [model-bench](https://github.com/trackandwield/model-bench), and the marketer rates how much editing each asset needed.

The agents state only facts from the brief or the framework. When a brief is missing something, they name the gap instead of filling it.

## What's here

| Path | What it is |
|---|---|
| `framework/messaging-framework.md` | Loom's public facts (with sources), positioning, pillars and personas |
| `brand/atlassian/` | Atlassian's voice, tone and grammar rules, condensed for the agents, plus real launch posts to use as style references |
| `briefs/` | The brief template and 5 practice briefs. Tier 1 gets all six assets, tier 2 skips positioning, tier 3 gets release notes and social only. Brief 5 is deliberately incomplete. |
| `docs/decision-log.md` | Why things are the way they are |

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
