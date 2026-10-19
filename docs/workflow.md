# Workflow: who does what, and how progress is tracked

This is the design the kit follows now so that a project manager agent can run it later. Nothing here is built yet.

## Three parts, kept separate

| Part | Job | Where |
|---|---|---|
| Intel engine | Gathers and tracks facts about a company and its competitors, with sources. Writes nothing customer-facing. | [competitive-intel-engine](https://github.com/trackandwield/competitive-intel-engine) |
| Launch kit | Turns intel, the framework and a brief into assets, and reviews them. | this repo |
| Project manager agent | Knows what's due, who owns it and who must approve it; asks people, chases them and records decisions. | later |

The kit reads intel only through the files described in `docs/intel-contract.md`, so any tool that writes those files can feed it.

## A launch manifest

Each launch gets `launches/<brief-id>/manifest.yaml`, created from the brief and `kit/assets.yaml`:

```yaml
brief: companies/atlassian/products/loom/briefs/01-auto-translate.yaml
tier: 1
people:            # roles from kit/assets.yaml, filled per launch
  pmm: Dana
  pm: Sam
  sales_lead: Ava
  legal: Jordan
due: 2026-11-11    # launch date minus the review buffer
assets:
  positioning:
    status: approved
    owner: pmm
    approvals: [{role: pmm, by: Dana, at: 2026-10-30, decision: approved}]
    versions: [v1, v2]
  blog_post:
    status: in_review
    waiting_on: [pmm]
    review_report: launches/loom-auto-translate/blog_post/v1.review.json
```

The manifest is the single source of truth. The kit writes drafts and review reports into it; people's decisions go into it; the project manager agent reads it to decide what happens next.

## Asset states

`not_started` → `blocked` (an input isn't approved yet) → `drafting` → `ai_review` → `in_review` (waiting on people) → `changes_requested` → back to `drafting`, or `approved` → `published`.

Rules the project manager agent will enforce:
- An asset can't start until every asset in its `inputs` is approved (so nothing is written off unapproved positioning).
- Every approver in `approvers` must approve; any one can request changes, with a comment the writer uses for the next version.
- Every decision is logged with who, when and why. Nothing is published without all approvals.
- Gaps the writer names (a missing date or proof) become questions to the brief's owner, not guesses.

## Human review

People review where they already work. The first version uses a simple review page per asset (draft, review report, claim sources, approve or request changes). Slack approval comes with the project manager agent.
