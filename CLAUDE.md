# CLAUDE.md — AI-SDLC Playbook

## What this project is
A documentation-only repo: a practical playbook for adopting AI into a team's
SDLC without quality risk. Written from Bhupendra's first-person experience
leading engineering at a regulated-industry (pharma) platform company.
Audience: engineering leaders and skeptical senior engineers — and hiring
managers reading this GitHub.

## Source of truth
- docs/SPEC.md — chapters are FRs (FR-1..FR-6); the Review Checklist replaces tests.
- IMPLEMENTATION_PLAN.md tracks chapter status.

## Working rules (adapted for prose)
1. Work chapter-by-chapter (one FR at a time).
2. **Never invent first-person facts.** Team sizes, metrics, anecdotes, and
   outcomes come from the owner — mark anything unconfirmed as [VERIFY] and
   never commit a chapter containing [VERIFY] markers.
3. Voice: practical, first-person, no hype, no vendor marketing. Short
   sentences. Concrete over abstract.
4. Every chapter must survive the question: "what would a skeptical senior
   engineer object to?" — address the objection in the text.
5. Length discipline: each chapter ≤ 2 pages. Cut before padding.
6. Real artifacts beat claims: link to the companion repos
   (secure-portal, labdocs-ai) where the practices are visible in commit
   history, .claude/ agents, and tests.

## Conventions
- Conventional commits referencing FRs: docs(scope): description (FR-n)
- Plain markdown; one ASCII workflow diagram; clean nav from README.
