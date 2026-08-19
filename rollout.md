# Rolling It Out: Four Weeks, Volunteers First

*How to take a team from "AI tools are a toy/threat" to a working practice —
without a mandate. On my own team, adoption happened more organically than
this (willing engineers first, tools evolving under us — Cursor, then Claude
Code); this chapter is that experience distilled into the deliberate plan I'd
run today.*

## Before week 1: three preconditions

1. **Guardrails written and visible** ([guardrails.md](guardrails.md)) —
   skeptics need to see the brakes before they'll get in the car.
2. **An approved tool** with an enterprise agreement (prompts not retained
   for training). Rolling out on personal accounts is how you create a
   compliance incident instead of a practice.
3. **Metrics chosen up front** ([metrics.md](metrics.md)). If you pick
   metrics after the pilot, nobody — including you — will believe the results.

## Week 1 — Volunteers and a baseline

- Ask for **2–3 volunteers**; never draft people. The right first cohort is
  neither the hype-maximalists nor the hard skeptics — take the pragmatists.
- Measure the **baseline first**: review rounds/PR and time-to-merge for the
  previous 4–8 weeks. Without a before, there is no after. (This is the step
  I under-invested in — we had review-round history from PRs, but I wish
  we'd captured a fuller baseline. Learn from that.)
- Volunteers adopt exactly two practices to start: **AI first-pass review
  before requesting human review**, and the **key-decisions bullets** on
  every PR. Not the whole playbook — two practices you can actually inspect.

## Week 2 — Widen the surface, keep the gate

- Add AI-drafted unit tests (author reviews every assertion —
  [guardrails rule 5](guardrails.md)) and the prompt templates
  ([prompts.md](prompts.md)) so nobody is inventing prompts from scratch.
- First **weekly retro** (30 min, standing agenda): what did the AI catch /
  miss / hallucinate this week? Keep a shared log of misses — it becomes
  your team-specific "when not to trust it" list, which is worth more than
  any generic advice.

## Week 3 — The skeptic checkpoint

This is where it's decided. Every team has a senior engineer whose objection
is some form of *"this ships code nobody understands."*

In my experience the turn comes not from argument but from artifact: show a
PR where the AI's first-pass review caught real issues *and* the author's
key-decision bullets prove a human still owns the change. Invite the skeptic
to review that PR as harshly as they like. A skeptic who can't find the
quality drop they predicted becomes your most credible advocate — precisely
because everyone knows they weren't sold, they were convinced.

Rules for this week:
- Never argue adoption in the abstract; argue over a specific PR.
- Let skeptics opt out of *using* AI but not out of *reviewing* AI-assisted
  PRs — their scrutiny is the quality system working, not resistance.

## Week 4 — Decide with data

Compare against the baseline: review rounds, time-to-merge, and the misses
log. Three honest outcomes:

- **Better + no quality regression** → open adoption to everyone (still no
  mandate; the volunteers' PRs are the advertisement).
- **Mixed** → keep the two core practices, drop what didn't earn its place,
  run two more weeks.
- **Worse** → stop and say so publicly. Killing a failed pilot loudly buys
  more credibility for the next attempt than any success theater.

## When NOT to use AI (tell the team explicitly)

- **Unplanned work.** The clearest pattern from our own misses: every bad AI
  outcome traced back to an incomplete or wrong ask — which really means work
  we hadn't scoped for ourselves yet. If you can't write the requirement
  clearly, the AI amplifies your confusion with confidence. Plan first.
- Novel domain logic where the team is still forming its own understanding
- Security/compliance-critical paths — full human process, always
  ([guardrails rule 3](guardrails.md))
- Debugging unfamiliar production incidents — confident wrong hypotheses are
  worse than slow right ones
- Anything an engineer is deliberately learning — outsource typing, never
  learning

## The objection a skeptical senior engineer will raise

*"Four weeks with volunteers proves nothing — volunteers are self-selected
enthusiasts."* Correct, and that's by design: the pilot's job is not
statistical proof, it's producing **inspectable artifacts** (PRs, review
threads, the misses log) that let every engineer judge the practice against
their own bar — plus a baseline comparison honest enough to survive the
team's harshest reviewer. Certainty comes later, from
[metrics that keep being measured](metrics.md) after everyone's using it.
