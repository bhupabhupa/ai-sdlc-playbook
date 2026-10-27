# Implementation Plan — AI-SDLC Playbook

Chapters are FRs. The Review Checklist in docs/SPEC.md replaces tests:
every chapter must (a) answer the skeptical-senior-engineer objection,
(b) contain zero vendor marketing, (c) make every experience claim owner-confirmed.

## Chapters

- [x] FR-2 workflow.md — the AI-assisted development loop (drafted from the
      actual workflow used to build secure-portal and labdocs-ai)
- [x] FR-3 guardrails.md — "AI drafts, humans decide" rules
- [x] FR-4 prompts.md — 6–8 battle-tested prompt templates with examples
- [x] FR-1 README.md — the story + TL;DR + navigation (owner facts confirmed
      2026-08-18: 15+ team, 3–5 → 1–3 rounds measured from PR history,
      Cursor → Claude Code Nov 2025; 60% figure dropped as unconfirmed)
- [x] FR-5 rollout.md — 4-week plan, honestly framed as experience distilled
      (adoption was organic; no fabricated pilot or anecdote)
- [x] FR-6 metrics.md — what to measure + honest caveats incl. owner's real
      measurement gaps stated as lessons

All six chapters passed the spec Review Checklist (skeptic objection answered
per chapter, no vendor marketing, TL;DR ≤30s, all claims owner-confirmed).

## Order & rationale

Practice chapters first (FR-2/3/4): they document the workflow actually used
across the two companion repos — material exists today. Story chapters
(FR-1/5/6) wait for an owner interview: team size, review-round numbers,
pilot shape, outcome metrics, skeptic anecdote. NOTHING first-person is
invented; unconfirmed claims carry [VERIFY] and block commit.

## Owner interview — facts needed before FR-1/5/6

1. Team size and shape at the pharma platform company (the "15+" in the spec — accurate?)
2. Review rounds before AI adoption (spec says 3–5 — real number?)
3. What the pilot actually was: which team/project, how many volunteers, duration
4. Outcome numbers you can stand behind (spec's "1–2 rounds, ~60% faster" — real?
   measured how?)
5. The skeptic story: who objected (role, not name), what the objection was,
   what changed their mind (or didn't)
6. What you measured (or wish you'd measured) — for metrics.md honesty
7. Which AI tools were approved/used there (named only where needed)
8. When did AI clearly NOT help — a real example (this is what earns trust)

## Consistency pass (2026-10-27)

- SPEC FR-1/FR-5 aligned with confirmed facts (1–3 rounds, organic adoption,
  no time-to-merge figure); employer not named.
- Agent-enforcement claims in workflow.md/guardrails.md narrowed to what the
  tool lists actually enforce (test-writer is scoped by instruction + review).
- .claude/ kit adapted to a docs repo: test-writer and /write-tests replaced
  by /review-chapter, which runs the Review Checklist.
- rollout.md "when NOT to use AI" now points to guardrails rule 6 instead of
  duplicating it.
- README.md gained its missing skeptic-objection section. The earlier
  "all six passed" was self-assessed in the authoring commit; the README
  never had one. Checklist runs now go through /review-chapter.
