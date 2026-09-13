Q1

For TrackFlow, Skye (the instructor) plausibly holds Product Owner, since she sets direction and priorities for the class. Scrum Master is more likely to rotate or fall to whichever trainee is coordinating that sprint, and the rest of the class is the Dev Team.

For JooC, I'm all three roles at once. I expect to neglect Scrum Master first, not because I'll forget it exists, but because I tend to plan ambitiously and won't notice when I've drifted from the plan mid-sprint. The concrete habit to stop that: a short daily check against the Sprint Backlog before starting work each day. If what I'm about to do isn't on it, I stop and ask why before continuing.

q2. 
## Definition of Ready - Weekly Planning
An item is ready to pull into a sprint if:
- It's written as a specific, single action (not "improve planning")
- It's scoped to one screen or one function, not the whole epic
- I know what "it works" looks like without having to design it mid-sprint
- It doesn't depend on an item that isn't built yet

## Definition of Done - Weekly Planning
An item is done if:
- I can create a Board (week), add Columns (days), and add Cards (meals/items) end to end
- Data survives an app restart (persists locally)
- I tested it myself on a real device/emulator, not just read the code
- No crash on the basic empty state (new week, no cards yet)

Q3

The Sprint Backlog is most at risk of being skipped or faked in a solo, daily-cadence project. With no one to report to, it's tempting to just work off the full Product Backlog in whatever order feels natural that day instead of committing to a fixed, ready-checked slice. The real cost is losing the discipline the Sprint Backlog is meant to enforce. Without it, every day becomes its own mini-decision about what to build, scope creeps invisibly, and there's no clear boundary to measure whether I actually finished what I said I would.

ASSIGMNENT 2.3
==============

Question 1: List as primary (day-to-day triage), Board for standups/status checks, Timeline just before sprint kickoff to sanity-check dependencies.

## Assignment 2.3 — Submission Summary

**Sample project (QuickNotes):** Built as a throwaway Asana project from the given backlog — 
few items organized into sections, "sign up with email and password" broken into 3 subtasks 
(validation, confirmation-email, error-handling) assigned to myself with due dates, 2 custom 
fields (Priority, Type) populated across all tasks, one dependency set ("filter by tag" depends 
on "tag a note"), and a `needs-design` tag applied to 3 tasks with a saved filter for 
"needs-design + unassigned."

**JooC project:** Full Product Backlog migrated from `product-backlog.md`, organized into 
sections by epic — Weekly Planning, Shopping List, Reminders, Carry-Over & History, and Auth 
(Auth left unresolved pending the v1 scope decision, per my Question flags). A distinct Sprint 1 
section was added matching `sprint-1-backlog.md` exactly: all six Weekly Planning items plus 
"view all items marked needed across the week" from Shopping List. Everything else — 
Reminders, Carry-Over & History, and the remaining Shopping List items — stayed in their 
backlog sections since none met my Definition of Ready yet (each depends on Weekly 
Planning/Shopping List existing first).

**Fields and structure:** Custom fields from Question 2 applied and populated on every task. 
[One Sprint 1 item] broken into subtasks. One real dependency set within Sprint 1: 
[e.g. "Add a Card to a day" depends on "Add a Column for each day"].


Assignment 2.4
==============

## Assignment 2.4

### Question 1 — Rewrite Sprint 1 as real user stories

1. As a home cook planning my week, I want to create a new week board, so that I have a fresh place to plan meals without last week's clutter.
2. As a home cook, I want each day of the week to appear as its own column, so that I can see my whole week's meal plan at a glance.
3. As a home cook, I want to add a card to a specific day, so that I can record what meal or shopping item I'm planning for that day.
4. As a home cook, I want to edit a card's text after I've created it, so that I can correct or update a meal plan without deleting and re-adding it.
5. As a home cook, I want to delete a card, so that I can remove a meal plan I've decided against.
6. As a home cook, I want to mark a day as "no meal planned," so that I can distinguish a deliberate skip from a day I just haven't planned yet.
7. As a home cook preparing to shop, I want to view all items marked "needed" across the whole week in one list, so that I don't have to check every day individually before I go to the store.

### Question 2 — Acceptance criteria

**1. Create a new week board**
- Tapping "New Week" creates a board with today (or a chosen start date) as the anchor
- The new board has zero cards and is empty of any prior week's data
- The board is immediately selectable/visible without a restart or refresh

**2. Days as columns**
- All 7 days appear as columns in correct calendar order
- Day labels show both weekday name and date
- Columns render correctly on first load of a new board with no manual setup

**3. Add a card to a day**
- Tapping "add" on a day column creates a card attached to that day only
- Card requires at least a title/text field to save
- New card appears in the correct column immediately, no refresh needed

**4. Edit a card**
- Existing card text is editable in place (or via an edit view)
- Saved edits persist after navigating away and back
- Canceling an edit leaves the original text untouched

**5. Delete a card**
- Card can be removed via an explicit delete action (not accidental swipe-only)
- Deleted card no longer appears in the column after the action
- Deletion is either confirmed with a prompt or easily undoable

**6. Mark day "no meal planned"**
- A day can be explicitly flagged "no meal planned" distinct from an empty column
- The flagged state is visually distinguishable from both "has a card" and "genuinely empty/unplanned"
- Flag can be removed/undone if the user changes their mind

**7. View needed items across the week**
- A dedicated view aggregates all cards/items marked "needed" from every day in the current week
- List updates when a new needed item is added to any day
- List is empty (with a clear empty state) when nothing is marked needed

### Question 3 — INVEST check

Story checked: **"Add a card to a specific day"**

- **Independent** — Pass. It only needs the board and day columns to already exist, which happens earlier anyway.
- **Negotiable** — Pass. How the input looks (popup, inline box, etc.) isn't decided yet, so there's room to change it later.
- **Valuable** — Pass. This is a core feature — the app doesn't work without it.
- **Estimable** — Pass. It's a simple, familiar type of task (basically "create a record"), so it's easy to size.
- **Small** — Fail. On its own it's small, but it's quietly hiding extra work: a card also needs to know if it's a *meal* or a *shopping item*, since that distinction is needed later for the Shopping List feature. That's really a second decision bundled into this story.
- **Testable** — Pass. I can check it against clear, specific conditions (listed in Question 2).

**Fix:** Split this into two stories — one for just adding a card (title, body, which day), and a separate one for marking whether it's a meal or a shopping item. Keeps each story doing one thing.
### Question 4 — Estimating alone, again

| Story | Points |
|---|---|
| Edit a card's text | 1 |
| Delete a card | 1 |
| Add a card to a day | 2 |
| Mark day "no meal planned" | 2 |
| Create a new week board | 3 |
| Days as columns | 3 |
| View needed items across the week | 5 |

The estimate that surprised me most was **"view needed items across the week."** As a raw backlog phrase it read as trivial — just "view needed items" — but writing the full story and acceptance criteria made clear it's actually the first feature that queries across every day on the board at once, not a single-day operation like the rest. That cross-cutting aggregation is what pushed it up to a 5 instead of feeling like a 2.

