---
name: ux-mobile-learning-design
description: >
  Use when designing flows, screens, feedback, progress, onboarding, or the visual system for the language-learning
  app. Don't use for writing final user-facing copy; hand that to the UX Copy Expert.
---

# UX design for a mobile learning app

## Design brief

A learner practices der, die, das in short sessions, one handed, often on the move. The core loop must feel fast, calm, and fair.

## Core practice screen

- One noun, large. Three answer buttons in a row or stacked: der, die, das. Large, thumb-reachable, equal size.
- Optional context line (an example sentence or the English meaning) below the noun; never above, so the noun stays the focus.
- After tapping: the chosen button resolves immediately, the correct article is shown with the noun ("die Zeitung"), and a **Next** action sits where the thumb already is.
- If a reliable pattern applies, show one short rule line and a "More" affordance. Never a wall of text.
- Target: a fluent learner completes a card in under three seconds.

## Feedback principles

- Right: brief confirmation, no fanfare that slows the loop.
- Wrong: show the correct answer plainly, keep the learner's choice visible for contrast, offer the rule. No red-screen failure, no sad sounds.
- Never use color as the only signal. Pair color with the article word and an icon or shape.

## Flows to design (in this order)

1. First launch and onboarding (goal, level, optional reminder; skippable; no account required).
2. Practice session (core loop, session end summary).
3. Review queue and "weak nouns".
4. Progress by level and by pattern.
5. Settings (reminders, sound, haptics, text size, theme, data export or delete).
6. Empty, offline, and error states for each of the above.

## Visual system

- Three article accent colors that meet WCAG AA contrast on both light and dark backgrounds, with a color-blind-safe check (verify with deuteranopia and protanopia simulation).
- Type scale of 5 to 6 steps; the practice noun is the largest element in the app.
- 8-point spacing grid; touch targets at least 44 pt on iOS and 48 dp on Android.
- One component library shared by both platforms with platform-appropriate behavior (navigation, back gesture, system sheets).

## Accessibility checklist (required in every spec)

- Contrast, focus order, labels for screen readers, text scaling to the largest setting, reduced motion alternative, no information by color alone, touch target sizes.

## Spec format

For each screen: purpose, entry and exit, layout at small and large widths, every state, interactions and motion, accessibility notes, and a **copy slot table** with key, location, max length, and context. Placeholders are marked `[copy]`.

## Avoid

Streak guilt ("you'll lose your streak!"), loss-aversion pop-ups, countdown pressure, notification spam, hidden close buttons, and any dark pattern around subscription.
