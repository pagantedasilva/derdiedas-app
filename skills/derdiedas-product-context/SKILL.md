---
name: derdiedas-product-context
description: >
  Use at the start of any task to load shared context about the Der Die Das app: who it is for, what it does, its
  principles, and its current facts. Use before writing code, design, copy, marketing, or support replies.
---

# Der Die Das: product context

> Board: fill every `TODO` below once. All agents read this file first, so it is the single source of truth.

## Facts (edit these)

- App name (working): TODO (placeholder "Der Die Das")
- Platforms: native iOS (Swift, SwiftUI) and native Android (Kotlin, Jetpack Compose)
- Repositories: TODO (iOS repo URL), TODO (Android repo URL)
- Business model: TODO (free, one-time purchase, subscription, free with ads)
- UI languages at launch: TODO (for example English first, then Spanish, Portuguese, Ukrainian)
- Content source for nouns: maintained by the German Content Editor as one versioned file (article, plural, CEFR level, example sentence). TODO: board confirms file format (JSON or CSV) and where it lives in the repos
- Privacy stance: TODO (recommended: no account needed, practice data stays on device, minimal analytics)

## Who it is for

Adult learners of German at roughly A1 to B1 who know what an article is but cannot yet feel which one a noun takes. Typical situations: five minutes on a commute, a language-class student wanting extra practice, someone preparing for a move or an exam.

## What the app does

1. Shows a noun, the learner picks der, die, or das.
2. Gives immediate feedback; if a reliable pattern exists, explains it in one short line.
3. Schedules each noun with spaced repetition. Nouns the learner misses come back sooner.
4. Shows progress by level and by pattern (for example "-ung words").

## Principles

- **Short sessions.** A useful session takes two to five minutes.
- **Teach the why.** Patterns and exceptions beat memorizing words one by one.
- **Never shame.** A wrong answer is information.
- **Accurate or silent.** If a gender rule is not in `german-gender-reference`, do not state it.
- **Accessible by default.** Color is never the only signal. Text scales. Screen readers work.
- **Private by default.** Collect only what the feature needs.

## Vocabulary used across the team

- *Article*: der, die, das. *Gender*: masculine, feminine, neuter.
- *Noun card*: one noun shown for practice. *Session*: one run of cards. *Review queue*: nouns due by the schedule.
- *Pattern*: a rule such as an ending that predicts gender. *Exception*: a noun that breaks a pattern.
- Article colors in the UI are a design decision owned by the UX Designer; always paired with the article text.
