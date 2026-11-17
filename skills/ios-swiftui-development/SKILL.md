---
name: ios-swiftui-development
description: >
  Use when implementing, fixing, or testing features in the native iOS app with Swift and SwiftUI. Don't use for
  Android work or for store submission.
---

# iOS development with SwiftUI

## Architecture

- SwiftUI for UI, Swift Concurrency (`async/await`) for async work, `@Observable` view models.
- Three layers, with dependencies pointing inward:
  1. **Domain** (pure Swift package): `Noun`, `Article`, `ReviewScheduler`, `AnswerEvaluator`, `Progress`. No UIKit or SwiftUI imports. Fully unit tested.
  2. **Data**: persistence (SwiftData or a local database) and the noun content loader.
  3. **UI**: views and view models.
- Keep the scheduler deterministic: it takes the current date as a parameter so tests do not depend on the clock.

## Conventions

- All user-facing text comes from the String Catalog by key. No literals in views.
- Support Dynamic Type up to the largest accessibility size. No fixed heights on text containers.
- Every interactive element has an accessibility label; the three answer buttons read as "der", "die", "das", not by color.
- Respect Reduce Motion and Dark Mode.
- Haptics are optional and light; provide a setting to turn them off.
- Minimum touch target 44 × 44 pt.
- Prefer small views and previews with sample data for each state (empty, loading, error, success).

## Learning logic rules

- A correct answer moves the noun to a longer interval; a wrong answer shortens it. The exact table lives in `docs/scheduling.md`; if it does not exist, create it in a task for the CEO to approve and share it with the Android Developer.
- Answer checking compares the chosen article with the noun's stored article. Do not hardcode German content in Swift.

## Testing

- Unit tests for the domain layer cover: first answer correct, wrong then right, interval growth, due-date selection, empty queue.
- UI tests only for the main practice loop.
- Run the full test suite before marking a task done.

## Privacy and data

- Practice data stays on device unless a task says otherwise.
- No third-party SDK without board approval. Analytics, if approved, never includes free text or identifiers beyond an anonymous install ID.

## Task closing comment

State: what changed, files or modules touched, tests added, how you verified accessibility, anything the Android Developer must mirror, and whether DevOps needs a new build.
