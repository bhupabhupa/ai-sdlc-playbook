---
name: spec-review
description: Review docs/SPEC.md and produce an FR-by-FR implementation plan. Use at project start or when the spec changes.
---

Read docs/SPEC.md fully. Then:

1. List ambiguities or missing details in the URS/FRs as questions. If an
   ambiguity blocks implementation, wait for answers; otherwise note your
   assumption inline and continue.
2. Create or update IMPLEMENTATION_PLAN.md with:
   - A checklist of every FR: "- [ ] FR-1: <title> -> files/components affected"
   - Recommended implementation order with one-line rationale
   - Shared foundations to build first (scaffolding, config, folders)
3. Do NOT write implementation code in this step.
