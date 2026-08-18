# The AI-Assisted Development Loop

*The working loop I use and coach. It is not "prompt the AI and merge what
comes out" — it is a spec-driven loop where the AI does the typing and humans
own every decision. You can see it running in the commit histories of
[secure-portal](https://github.com/bhupabhupa/secure-portal) and
[labdocs-ai](https://github.com/bhupabhupa/labdocs-ai).*

## The loop

```
   ┌──────────────────────────────────────────────────────────────┐
   │  SPEC FIRST (human)                                          │
   │  URS → numbered Functional Requirements → design → test plan │
   └──────────────┬───────────────────────────────────────────────┘
                  ▼
   ┌──────────────────────────────┐
   │  PLAN (AI drafts, human cuts)│  AI reads the spec, proposes an
   │  implementation order + files│  FR-by-FR plan. Human trims scope
   └──────────────┬───────────────┘  and records assumptions.
                  ▼
   ┌──────────────────────────────┐
   │  IMPLEMENT ONE FR (AI)       │  One requirement per pass. AI states
   │  smallest reviewable unit    │  which FR and which files BEFORE coding.
   └──────────────┬───────────────┘
                  ▼
   ┌──────────────────────────────┐
   │  VERIFY (human-witnessed)    │  Run the real thing: tests AND a live
   │  tests + live check          │  check. "It compiles" is not done.
   └──────────────┬───────────────┘
                  ▼
   ┌──────────────────────────────┐
   │  AI FIRST-PASS REVIEW        │  A separate review pass (fresh context)
   │  before any human review     │  catches the mechanical 80% before a
   └──────────────┬───────────────┘  human spends attention.
                  ▼
   ┌──────────────────────────────┐
   │  EXPLAIN & COMMIT (human)    │  3 "key decision" bullets per FR. If the
   │  conventional commit ref FR-n│  author can't explain it, it doesn't merge.
   └──────────────────────────────┘
```

## What each side owns

| Humans own | AI does |
|---|---|
| Requirements, scope, and what "done" means | First-draft implementation of one FR at a time |
| Design decisions and trade-offs (and writing them down) | First-pass code review before human review |
| Domain judgment: what's correct *for this business* | Unit-test drafts — reviewed by the author before they count |
| The merge decision, always | Boilerplate: docs, commit messages, migration scaffolds |

## Three rules that make it work

**1. Specs before prompts.** A numbered FR list turns "build me an auth
service" into twenty small, verifiable asks. The AI is dramatically better at
"implement FR-3: RBAC middleware returning 403 with an audit entry" than at
vibes. The spec is also what makes review possible — you review *against*
something.

**2. One FR per pass.** Big prompts produce big diffs, and big diffs produce
rubber-stamp reviews. Smallest reviewable unit, verified, committed with the
FR id in the message. The commit history becomes the audit trail of who
decided what.

**3. The author explains, always.** After every FR the author writes three
"key decision" bullets — the why, the trade-off, the alternative rejected. If
you can't write them, you don't understand the change, and it doesn't merge.
This single rule prevents the failure mode skeptics rightly fear: teams
shipping code nobody understands.

## The objection a skeptical senior engineer will raise

*"AI review before human review just means humans rubber-stamp whatever the
AI approved."* — Backwards, in practice. The AI pass eats the mechanical
findings (naming, missed null checks, forgotten error paths) so the human
review, which now takes one round instead of several, is spent entirely on
what humans are uniquely good at: "is this the right design for our domain?"
The human round gets *smaller and sharper*, not lazier. The discipline that
keeps it honest is rule 3 — a human still has to explain every line they merge.

## Role separation, enforced by tooling

Don't rely on the AI remembering its role — enforce it. My project template
defines three AI agents with *restricted tools*: an *architect* that can read
but not write code, a *test-writer* that can only touch test directories, and
a *reviewer* that can flag but not fix. The same capability-over-trust
principle as RBAC — see `.claude/agents/` in either companion repo.
