# 📱 JooC
JooC is a weekly meal-planning and household-reminder app for people who like to plan their whole week in one sitting rather than day by day. It's built for solo home-cooks and small households who want a simple, visual way to decide what's for dinner and what needs to be bought before it becomes a last-minute scramble. In this app, a Board represents a single week, a Column represents a day of that week, and a Card represents either a meal planned for that day or a household item (like groceries or supplies) that needs to be picked up before the week is over.


## 🚀 Getting Started
The app uses **Flavor** package to target a specif environment

For Android:  flutter run --flavor dev -t lib/main_dev.dart
              flutter run --flavor prod -t lib/main_prod.dart
              flutter run --flavor beta -t lib/main_beta.dart




### Prerequisites
Flutter and Dart SDKs installed

### Installation

1. Clone the repository:
   `git clone https://github.com`
2. Install dependencies:
   `flutter pub get`
3. Start the development flavor:
   `flutter run --flavor dev -t lib/main_dev.dart`

## ⚙️ Configuration & Environment Variables

.env is not needed at this point

## 🏗️ Architecture & Tech Stack

* **Frontend:** Flutter
* **Backend:** Dart
* **Database:** Firebase
* **State Management:** Provider
* **Pattern:** MVVM

## 🔌 API Reference 
N/A at this point

## 🛠️ Testing
Only manual testing is required at this point

## 🤝 Contributing
 
* Detail branching conventions:  `feature/feature-name`.
* MVVM
* Clean Architecture

## 📄 License
* MIT

 ## ⚠️ Known Limitations

* **Auth is undecided** — v1 scope (local-only vs. account-based login) has not been finalized. Features that assume a logged-in user are not yet implemented.
* **Manual testing only** — there is no automated test suite yet; changes should be manually verified against the flows in `lib/main_dev.dart` before merging.
* **`.env` is currently unused** — configuration is hardcoded per flavor (dev/prod/beta). This will change once external services (e.g. push notifications, email) are added.

### ADR: Use MVVM with Provider for state management

**Status:** Accepted

**Context:** JooC needs a state management approach for Flutter that
handles Board/Column/Card data flowing between the UI and Firebase,
across three build flavors (dev/prod/beta). As a solo developer, the
approach also needs to stay maintainable without a team to enforce
conventions.

**Decision:** Use the MVVM pattern with the Provider package for
state management, rather than a more complex option (Bloc, Riverpod)
or no formal pattern at all.

**Consequences:** Views stay declarative and testable against
ViewModels without touching Firebase directly. Provider has a
smaller learning curve and less boilerplate than Bloc, which matters
building solo. Trade-off: Provider scales less cleanly than Bloc/
Riverpod if the app grows multiple collaborators or much deeper
state trees later — that would be a reason to revisit this ADR.
