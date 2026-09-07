# Agile Redesign — JooC

## Critique of TaskBoard Pro (Waterfall-style plan)

1. Full spec sign-off before any building begins violates "responding to change over
   following a plan" and Principle 2 ("welcome changing requirements, even late in
   development"). Locking the spec in Phase 1 and banning changes once design starts
   assumes you can know everything upfront, which Agile explicitly rejects.

2. No demos until the build phase is fully complete violates "working software over
   comprehensive documentation" and Principle 1 (satisfying the customer through early
   and continuous delivery) plus Principle 7 (working software as the primary measure
   of progress). Nine weeks of building with zero visibility means nobody can course
   correct if something's wrong.

3. One giant QA pass across all features simultaneously (Phase 4) means bugs and
   misunderstandings compound for nine weeks before anyone tests anything, the opposite
   of iterative, continuous delivery. Testing this late massively increases risk and rework.

4. Launch to all users at once (Phase 5) is a single big-bang release with no earlier
   customer feedback loop, violating "customer collaboration over contract negotiation."
   There's no chance to learn from real users before everyone is exposed to whatever went wrong.

## Agile Redesign — First Two Iterations (JooC)

**Iteration 1 (Week 1–2):** Build the smallest working version: a simple weekly view
where I fill in what I'm cooking each day, plus a flat, uncategorized shopping list I
fill in manually. No reminders yet, no categorization. Ship it, use it for real that
week, see what's missing.

**Iteration 2 (Week 3–4):** Based on actually living with Iteration 1, add whatever
proved genuinely necessary, likely a reminder or notification for shopping day, and
maybe basic list persistence week to week (carrying over unbought items). Skip
anything I didn't miss in practice.