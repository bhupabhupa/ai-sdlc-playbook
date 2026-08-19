# The AI-SDLC Playbook

**TL;DR** — I lead engineering in regulated-industry software (pharma lab
platforms). We adopted AI into our development workflow without lowering the
quality bar, on one principle: **AI drafts, humans decide**. Our measured
result: PRs that took 3–5 review rounds now merge in 1–3, and authors can
still explain every line. This repo is the playbook — the
[workflow](workflow.md), the [guardrails](guardrails.md), the
[prompts](prompts.md), the [rollout plan](rollout.md), and the
[metrics](metrics.md) — plus two companion repos where the workflow is
visible in the commit history.

## The story

I've spent recent years leading engineering work on a lab-data integration
platform in a regulated industry, on a team of 15-plus engineers (with the
usual churn of people joining and leaving). Our cycle was slow at **every
stage**. Development itself was lengthy: solution thinking only really
started after a URS was signed off, and everything was hand-written from
there. **Automation tests** were their own time sink — writing and
maintaining them often cost as much as the feature code they covered. Then
came **review churn**: a typical PR took 3–5 review rounds — round one caught
the mechanical issues (missed error paths, naming, convention drift), round
two caught what round one's noise had buried, and only around round three did
anyone discuss design. Multiply by a whole team, and the path from signed-off
requirement to merged, tested code was our bottleneck — and review was our
senior engineers' least favorite job.

When AI coding tools became viable — we started on Cursor and standardized on
Claude Code in late 2025, though nothing here is tool-specific — they
attacked all three stages. On the development side, a signed-off requirement
became a first working draft in hours instead of days, because the thinking
moved *up front* into specs the AI could implement requirement-by-requirement.
Test automation flipped from a tax into a default: AI drafts the tests, the
author reviews every assertion ([guardrails rule 5](guardrails.md)), and
suddenly "too busy to write tests" stopped being true. And on the review
side, the bet was: if an AI pass eats the mechanical 80% of review findings
*before* a human looks, the human round gets sharper and rarer.

We didn't mandate anything. Adoption started with the engineers most willing
to try, and spread because their PRs became the advertisement. The one number
we tracked consistently, straight from PR history: **review rounds per PR
went from 3–5 to 1–3.** Time-to-merge fell with it — materially, though I
didn't keep a number I'd defend in an audit, which is itself a lesson (see
[metrics.md](metrics.md) for what I'd instrument from day one next time).

The lessons that survived contact with reality:

1. **AI compresses the whole cycle — drafting, tests, and review — but
   measure at least one stage.** For us the countable win was review churn
   (it's right there in PR history); the development and test-writing
   speedups were just as real but harder to quantify. Instrument whichever
   you can count.
2. **AI fails when the ask is unplanned.** Every bad AI day we had traced
   back to an incomplete or wrong prompt — which really means work we hadn't
   scoped for ourselves. Garbage in, *confident* garbage out. The fix wasn't
   better prompting tricks; it was planning first ([workflow.md](workflow.md)
   — spec before prompts).
3. **The explanation rule is load-bearing.** "Never merge code you can't
   explain" is the single practice that kept quality flat while speed rose.
4. **Volunteers, then evidence, then everyone.** Mandates create malicious
   compliance; visible results create pull.

## Where to go

| Read | If you want |
|---|---|
| [workflow.md](workflow.md) | The development loop — who owns what, one diagram |
| [guardrails.md](guardrails.md) | The six rules and the failure modes behind them |
| [prompts.md](prompts.md) | 8 battle-tested prompt templates |
| [rollout.md](rollout.md) | A 4-week team adoption plan |
| [metrics.md](metrics.md) | What to measure and how not to fool yourself |

## Proof over claims

The workflow here isn't theoretical — it built these repos, spec-first,
FR-by-FR, with restricted-tool AI agents and honest commit histories:

- **[secure-portal](https://github.com/bhupabhupa/secure-portal)** — Keycloak
  SSO + RBAC with back-channel logout, 14 tests, CI
- **[labdocs-ai](https://github.com/bhupabhupa/labdocs-ai)** — RAG assistant
  with calibrated refusals and a tested prompt-injection guardrail, 19 tests, CI

Both contain the `.claude/` agent and skill definitions this playbook describes.
