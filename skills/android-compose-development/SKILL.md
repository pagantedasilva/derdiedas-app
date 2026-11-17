---
name: android-compose-development
description: >
  Use when implementing, fixing, or testing features in the native Android app with Kotlin and Jetpack Compose. Don't
  use for iOS work or for Play Console submission.
---

# Android development with Jetpack Compose

## Architecture

- Kotlin, Jetpack Compose (Material 3), coroutines and Flow, ViewModel with `StateFlow`.
- Three layers, with dependencies pointing inward:
  1. **Domain** (pure Kotlin module): `Noun`, `Article`, `ReviewScheduler`, `AnswerEvaluator`, `Progress`. No Android imports. Fully unit tested.
  2. **Data**: Room for local storage and a noun content loader.
  3. **UI**: composables and view models, state hoisted, single immutable UI state per screen.
- Keep the scheduler deterministic: pass in a `Clock` so tests do not depend on real time.

## Conventions

- All user-facing text from `strings.xml` by key, matching the iOS keys. No literals in composables.
- Support font scale up to 200% and display size changes. No fixed heights on text.
- Every interactive element has a `contentDescription` or semantics; the answer buttons read "der", "die", "das", not by color.
- Respect system dark theme and reduced animations.
- Minimum touch target 48 × 48 dp.
- Previews with sample data for each state (empty, loading, error, success).
- Check on a small phone, a large phone, and a tablet width.

## Learning logic rules

- Behavior must match iOS exactly. The scheduling table is in `docs/scheduling.md`. If you find a mismatch, comment on the task and tag the CEO; do not silently diverge.
- Answer checking compares the chosen article with the stored article. No German content hardcoded in Kotlin.

## Testing

- Unit tests for the domain module: first answer correct, wrong then right, interval growth, due-date selection, empty queue.
- Compose UI test for the main practice loop.
- Run lint and the full unit test suite before marking a task done.

## Permissions and data

- Request no permission without board approval. Notifications permission (Android 13+) is requested in context, after the learner has done a session, with a clear reason.
- Practice data stays on device unless a task says otherwise. Any change that affects the Play Data safety form needs board approval.

## Task closing comment

State: what changed, modules touched, tests added, how you checked TalkBack and font scale, what iOS must mirror, and whether DevOps needs a new build.
