# Prompt Templates That Survived Contact With Real Work

*The difference between a weak and a strong prompt is the difference between
a review round and three. Pattern behind all of these: give the AI a **role, a
scope, constraints, and an output contract** — the same way you'd brief a new
team member. Several of these run as slash-commands in my project template
(`.claude/skills/` in the companion repos), so nobody retypes them.*

## 1. Implement one requirement

> Implement **FR-{n} only** from docs/SPEC.md. Before writing code, state the
> FR in one line and list the files you'll touch. Follow the design section;
> if you deviate, say why in one sentence. Do not fix adjacent problems —
> list them at the end as follow-ups. Finish with 3 "key decisions" bullets
> I can defend in review.

**Weak version:** "implement the spec" → 800-line diff nobody can review.
**This version:** one reviewable diff, pre-labeled with its own rationale.

## 2. First-pass code review

> Review this diff as a skeptical senior engineer. Only flag things you'd
> block a merge for: correctness bugs, missed error paths, security issues,
> and violations of the conventions in CLAUDE.md. For each finding:
> file:line, the risk, and a suggested fix. Do NOT rewrite the code. If you
> find nothing blocking, say so — do not invent nitpicks.

The last sentence matters most: without it, AI reviewers manufacture noise to
seem useful, and humans learn to ignore them.

## 3. Unit-test generation

> Write tests for {module} covering the Test Plan cases T-{x}..T-{y} in
> docs/SPEC.md. Test through the public interface, not internals. Every test
> name states the expected behavior ("returns 403 when viewer calls create").
> Mock external dependencies at {seam}. Then RUN the tests and report
> results. Do not touch any file outside test directories.

**Weak version:** "write tests for this file" → 40 assertions of `toBeDefined()`.
**This version:** tests tied to named requirements, runnable proof included.

## 4. Refactor proposal (proposal — not execution)

> Propose a refactor of {area} to address {pain}. Output: the target
> structure, the ordered steps (each independently shippable), what each step
> risks breaking, and what should be tested after each. Do NOT write the
> code yet.

Separating proposal from execution keeps the design decision visibly human.
Approve the plan, then feed steps back one at a time through template #1.

## 5. API documentation from code

> Document the endpoints in {files} for an integrator who has never seen the
> codebase: method, path, auth requirement, request/response examples
> (realistic values, not "foo"), and every error envelope with when it fires.
> Where behavior is surprising, add a "note" — surprising means anything you
> had to read twice.

## 6. Commit message

> Write a conventional commit for this diff: type(scope): summary referencing
> FR-{n}, then 2–4 body bullets — what changed and WHY, not a file list.
> No adjectives. If the diff does more than one thing, tell me to split it
> instead of writing the message.

The refusal clause is the useful part — the AI is an incorruptible enforcer
of "one change per commit."

## 7. Incident summary

> From this timeline/log, draft a blameless incident summary: impact (who,
> how long, how bad), timeline of detection→mitigation→resolution, root
> cause chain (technical, then process), and 3–5 action items each with an
> owner-shaped description. Flag every place where you are inferring rather
> than reading facts — mark those [ASSUMED] for me to verify.

The [ASSUMED] convention is the transferable trick: make the AI label its own
guesses, in any prompt where facts matter.

## 8. Spec review / planning

> Read docs/SPEC.md fully. List ambiguities as questions; where an ambiguity
> doesn't block, state your assumption inline and continue. Produce an
> implementation plan: FR checklist with affected files, recommended order
> with one-line rationale, and shared foundations to build first. Write NO
> implementation code.

## The meta-template

```
[ROLE]        Review this as a skeptical senior engineer…
[SCOPE]       …FR-3 only / this diff only / these files only…
[CONSTRAINTS] …don't rewrite, don't touch tests, follow CLAUDE.md…
[CONTRACT]    …output: file:line findings / plan / 3 bullets…
[HONESTY]     …if nothing found, say so / mark guesses [ASSUMED]…
```

Every template above is that shape. The honesty clause is the one people
forget, and it's the one that keeps trust in the loop.

## The objection a skeptical senior engineer will raise

*"Prompt templates are cargo-culting — good engineers just write clearly."*
They do — once. The template's job is making the tenth, tired, 6-pm ask as
rigorous as the first: that's why these live as slash-commands in the repo
(`.claude/skills/`), versioned and reviewed like code, instead of in anyone's
memory. A prompt in the repo is a team standard; a prompt in your head is a
personal habit that leaves when you do.
