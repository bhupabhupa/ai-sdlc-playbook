---
name: commit-work
description: Group current changes into clean conventional commits referencing FR ids.
---

1. Run git status and git diff to see all uncommitted work.
2. Group changes into logical commits - one concern each. Never one
   "misc changes" dump. Typical grouping: scaffolding / per-FR feature /
   tests / docs.
3. Messages: conventional format with FR reference where applicable,
   e.g. "feat(ingest): chunk and embed uploaded docs (FR-2)"
4. Show the proposed commit plan (files -> message) BEFORE executing;
   execute after confirmation.
