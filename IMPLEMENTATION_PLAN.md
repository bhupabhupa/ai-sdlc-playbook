# Implementation Plan — AI-SDLC Playbook

Chapters are FRs. The Review Checklist in docs/SPEC.md replaces tests:
every chapter must (a) answer the skeptical-senior-engineer objection,
(b) contain zero vendor marketing, (c) make every experience claim owner-confirmed.

## Chapters

- [ ] FR-2 workflow.md — the AI-assisted development loop (drafted from the
      actual workflow used to build secure-portal and labdocs-ai)
- [ ] FR-3 guardrails.md — "AI drafts, humans decide" rules
- [ ] FR-4 prompts.md — 6–8 battle-tested prompt templates with examples
- [ ] FR-1 README.md — the story + TL;DR + navigation (**needs owner facts**)
- [ ] FR-5 rollout.md — 4-week adoption plan (**needs owner anecdote**)
- [ ] FR-6 metrics.md — what to measure + honest caveats (**needs owner numbers**)

## Order & rationale

Practice chapters first (FR-2/3/4): they document the workflow actually used
across the two companion repos — material exists today. Story chapters
(FR-1/5/6) wait for an owner interview: team size, review-round numbers,
pilot shape, outcome metrics, skeptic anecdote. NOTHING first-person is
invented; unconfirmed claims carry [VERIFY] and block commit.

## Owner interview — facts needed before FR-1/5/6

1. Team size and shape at Scitara (the "15+" in the spec — accurate?)
2. Review rounds before AI adoption (spec says 3–5 — real number?)
3. What the pilot actually was: which team/project, how many volunteers, duration
4. Outcome numbers you can stand behind (spec's "1–2 rounds, ~60% faster" — real?
   measured how?)
5. The skeptic story: who objected (role, not name), what the objection was,
   what changed their mind (or didn't)
6. What you measured (or wish you'd measured) — for metrics.md honesty
7. Which AI tools were approved/used at Scitara (named only where needed)
8. When did AI clearly NOT help — a real example (this is what earns trust)
