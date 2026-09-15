# ADR 0001: Use MVVM with Provider for State Management

## Status
Accepted

## Context
JooC is a Flutter app structured around a Board → Column → Card
model, where a Board is a week, a Column is a day, and a Card is a
planned meal or household item. State needs to flow cleanly between
the UI and Firebase (the chosen database) across three separate
build flavors — dev, prod, and beta.

As a solo developer, the app also needs a state management approach
that stays maintainable without a team around to enforce conventions
or catch inconsistent patterns in review. The realistic alternatives
considered were:

- **No formal pattern** — state handled ad hoc per screen
- **Bloc** — a stricter, event-driven pattern with more structure but
  significantly more boilerplate
- **Riverpod** — a more modern alternative to Provider, with compile-time
  safety but a steeper learning curve and a less mature ecosystem at
  the time of this decision
- **Provider with MVVM** — a lighter-weight pattern separating Views
  from ViewModels, with Provider handling dependency injection and
  state propagation

## Decision
Use the **MVVM (Model-View-ViewModel) pattern with the Provider
package** for state management across the app.

Views stay declarative and only read from ViewModels — they never
touch Firebase or business logic directly. ViewModels own the state
for a given screen or feature (e.g. a WeekViewModel exposing the
current Board's Columns and Cards) and expose it to the View via
Provider's `ChangeNotifierProvider` / `Consumer` mechanisms.

## Consequences

**Positive:**
- Clear separation of concerns: Views are easy to reason about and
  test in isolation from data-fetching logic.
- Provider has a smaller learning curve and far less boilerplate than
  Bloc, which matters when building and maintaining the app solo.
- ViewModels can be unit tested without spinning up widgets or
  Firebase.

**Negative / trade-offs:**
- Provider scales less predictably than Bloc or Riverpod as state
  trees grow deeper or more interconnected (e.g. once Carry-Over &
  History needs to read across multiple weeks' Boards at once).
- If JooC gains additional contributors, Provider's lighter
  conventions offer less enforced structure than Bloc — inconsistent
  ViewModel patterns could emerge without a team style guide.
- No compile-time safety benefits that Riverpod would offer.

**Revisit this decision if:** the app grows beyond solo development,
or state complexity (e.g. cross-week carry-over logic, real-time
multi-device sync) outgrows what Provider comfortably handles.