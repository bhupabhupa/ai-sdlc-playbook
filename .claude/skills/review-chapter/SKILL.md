---
name: review-chapter
description: Run the Review Checklist (this repo's replacement for tests) against one chapter or all. Argument optional, e.g. /review-chapter FR-2
argument-hint: [FR-id or blank for all chapters]
---

Use the code-reviewer agent for this task.

Review $ARGUMENTS (or every chapter if blank):

1. Apply the Review Checklist in docs/SPEC.md to each chapter.
2. Check length: each chapter <= 2 pages (roughly 900 words; run wc -w).
3. Grep for [VERIFY] markers; any hit blocks commit.
4. Cross-check claims against the other chapters, docs/SPEC.md and the
   .claude/ files - the numbers and descriptions must agree everywhere.
5. Report pass/fail per chapter. Fix nothing; list fixes for the owner.
