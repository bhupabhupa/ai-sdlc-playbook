# SPEC — AI-SDLC Playbook (Documentation Repo)

## 1. URS
- URS-1: As an engineering leader, I can hand a team a concrete playbook for adopting AI in their SDLC without quality risk.
- URS-2: As a skeptical engineer, I can read the guardrails and see that human judgment stays in charge.
- URS-3: As a hiring manager reading Bhupendra's GitHub, I see EM-level thinking, not just code.

## 2. Content Requirements (chapters = FRs)
- FR-1 README: the story — team of 15+, PRs at 3–5 review rounds, the pilot, the outcome (1–2 rounds, ~60% faster), lessons.
- FR-2 workflow.md: the AI-assisted development loop (author runs AI first-pass review before requesting human review; AI-generated unit tests reviewed by author; humans own design/domain decisions).
- FR-3 guardrails.md: "AI drafts, humans decide" rules — never merge unexplained code; AI output is a proposal; security-sensitive and compliance-touching code gets full human review; data/confidentiality rules (no proprietary code into unapproved tools).
- FR-4 prompts.md: 6–8 battle-tested prompt templates (code review pass, unit-test generation, refactor proposal, API docs, commit message, incident summary) with before/after examples.
- FR-5 rollout.md: 4-week adoption plan for a team — volunteers first, metrics chosen up front, weekly retro, handling skeptics (a real anecdote), when NOT to use AI.
- FR-6 metrics.md: what to measure (review rounds to merge, time-to-merge, test coverage delta, defect escape rate) and honest measurement caveats.

## 3. Design Spec
- Pure markdown repo; clean navigation from README; one diagram (workflow) as ASCII or image.
- Voice: practical, first-person experience, no hype. Every claim tied to the Scitara story or clearly marked as recommendation.
- Length discipline: each chapter ≤ 2 pages; this is a playbook, not a book.

## 4. Review checklist (in place of tests)
- Every chapter answers "what would a skeptical senior engineer object to?"
- No tool-vendor marketing language; tools named only where the practice depends on them.
- README top has a 5-line TL;DR; a busy hiring manager gets the value in 30 seconds.
