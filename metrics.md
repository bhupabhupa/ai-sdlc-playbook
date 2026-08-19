# Metrics: How To Know It's Working (And How Not To Fool Yourself)

*Four numbers, chosen before the pilot starts, measured the same way after.
Plus the caveats — because AI adoption is currently a hype market, and the
fastest way to lose your team's trust is a dashboard that flatters.*

## The four core metrics

### 1. Review rounds to merge
**What:** count of review→revision cycles per PR before approval.
**Why it's the headline:** it measures the *churn* AI-assisted workflows
actually target, and it's cheap to count from PR history — you can baseline
it retroactively. This was the one number my team tracked consistently, and
it carried the whole story: **3–5 rounds before, 1–3 after.**

### 2. Time-to-merge
**What:** PR opened → merged, median (never mean — one parked PR wrecks a mean).
**Why:** the outcome leadership cares about; pairs with #1 to show *where*
time went. Honesty from my own experience: we *felt* this fall materially and
I never kept a number I'd defend — which is why the advice is "median,
measured, or don't quote it." Don't be me; instrument it on day one.

### 3. Test coverage delta
**What:** coverage trend on changed code, not the repo-wide vanity number.
**Why:** AI makes tests cheap to write, so coverage should *rise* with
adoption. If it rises while defects also rise, you have assertion theater —
see caveat 3.

### 4. Defect escape rate
**What:** bugs found after merge (prod incidents + post-merge fixes)
attributable to changes in the period.
**Why it's the honesty metric:** speed gains that raise escapes are a loan,
not a profit. This is the number skeptics watch — publish it even when it's
noisy, *especially* when it's noisy. Confession: my team tracked this
informally (incident recollection, not ticket labels), and "we didn't notice
a rise" is a weaker claim than "escapes held at N per quarter." This is the
metric I most wish we'd instrumented from day one — it's cheap (a ticket
label) and it's the difference between a story and evidence.

## Worth watching, not worth targeting

- **AI-suggestion acceptance rate** — diagnostic of prompt/tool quality;
  gameable and meaningless as a target.
- **Review quality of comments** (are humans discussing design instead of
  formatting?) — the real prize; sample threads monthly rather than scoring.
- **The misses log** (from the [weekly retro](rollout.md)) — a growing list
  of "AI got this wrong" is a *healthy* signal: it means people are checking.

## The caveats — read before celebrating

1. **Goodhart's law.** Any metric here made a target will be gamed (rounds
   drop because reviewers give up, not because PRs improved). Track trends,
   discuss in retros, tie to no one's performance review. The moment
   review-rounds hits an OKR, the number lies.
2. **Novelty effect.** Weeks 1–4 carry enthusiasm; measure again at month 3
   before claiming a new normal.
3. **Coverage can lie.** Forty green `toBeDefined()` assertions move the
   number and test nothing — pair the coverage delta with escape rate, never
   read it alone.
4. **Volunteer selection bias.** Pilot cohorts are your most motivated
   engineers; expect regression toward the mean at full rollout and don't
   promise leadership the pilot's numbers.
5. **Small n.** A team's monthly PR count is a small sample; report ranges
   ("3–5 rounds → 1–3"), not decimal places. Precision you can't defend is
   credibility you're borrowing.
6. **Confounders.** Team changes, codebase maturity, and deadline seasons all
   move these numbers. The baseline period should be boring — never compare
   a crunch quarter to a calm one.

## The objection a skeptical senior engineer will raise

*"You can't attribute any of this to AI — too many variables."* True in the
strict sense, and the answer is scope honesty: these metrics don't prove
causation, they bound the risk. What they *can* show, cheaply and
continuously, is that speed rose **while quality held** — and if quality
doesn't hold, they show that first. That's what the metrics are for: not a
victory lap, an early-warning system.
