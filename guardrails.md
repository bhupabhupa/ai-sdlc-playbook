# Guardrails: AI Drafts, Humans Decide

*Rules that keep AI a force multiplier instead of a liability. Each exists
because of a specific failure mode, named below. These are team rules — they
belong in your working agreement and your PR template, not in a wiki nobody
reads.*

## The six rules

### 1. Never merge code you can't explain
The failure mode: six months later, an incident, and nobody in the room
understands the code path. The rule is enforced at review: any reviewer may
ask the author to explain any line, and "the AI wrote it" is a failed answer.
Practical aid: every AI-assisted change ships with the author's "key
decisions" bullets (see [workflow.md](workflow.md)).

### 2. AI output is a proposal, not a change
The failure mode: auto-applied "fixes" that silently alter behavior. AI
suggestions land as diffs a human applies deliberately — never as direct
commits, never auto-merged. CI runs the same gates on AI-assisted commits as
on any other; there is no separate lane.

### 3. Security- and compliance-touching code gets full human review — always
The failure mode: an AI-drafted auth check that is *plausible* and *wrong*,
in exactly the code where plausible-and-wrong is most expensive. Anything
touching authentication, authorization, audit trails, e-signatures, or data
integrity gets line-by-line human review regardless of how it was written.
In regulated industries (I come from pharma platforms) this is not optional —
your auditors will ask.

### 4. Data boundaries are absolute
The failure mode: proprietary code or customer data pasted into an unapproved
tool, discovered during a compliance review. The rule set:
- Only company-approved AI tools, under enterprise agreements where prompts
  are not retained for training.
- No customer data, credentials, or PII in prompts — ever. Regex-level
  hygiene: if it looks like a connection string, it doesn't go in.
- Personal accounts and personal projects stay fully separate from company
  code and company tools — in both directions.

### 5. AI-generated tests don't count until a human reads them
The failure mode: 40 green tests that assert nothing (`expect(result).toBeDefined()`
forty times) creating false confidence. Test drafts are cheap to generate and
that's fine — but the author reviews every assertion and deletes theater.
Coverage that lies is worse than coverage that's missing.

### 6. Know when NOT to use it
AI assistance is weakest exactly where stakes are highest:
- **Unplanned work** — the clearest pattern from our own misses: every bad
  AI outcome traced back to an incomplete or wrong ask, i.e. work we hadn't
  scoped for ourselves yet. If you can't write the requirement, don't prompt it.
- **Novel domain logic** — it pattern-matches to the mainstream; your edge
  cases are not mainstream.
- **Debugging unfamiliar production systems** — confident wrong hypotheses
  burn incident time.
- **Anything you intend to learn deeply** — drafting is how understanding
  forms; outsource the typing, not the learning, on code you'll own for years.

## The objection a skeptical senior engineer will raise

*"These rules sound nice, but under deadline pressure they'll evaporate."*
Fair — which is why the load-bearing rules are structural, not aspirational:
restricted-tool agents (the architect has read-only tools, the reviewer has
no edit tools; the test-writer is scoped to test directories, and any diff it
makes outside them is a review blocker), CI gates that don't know or care
whether AI was involved, and a PR-template checkbox for the explanation rule. Culture decays
under pressure; tooling doesn't.

## What this buys you

A team where AI makes the *fast parts faster* (drafting, boilerplate,
first-pass review) while the *slow parts stay deliberately slow* (design,
domain decisions, security review). That asymmetry is the entire point.
