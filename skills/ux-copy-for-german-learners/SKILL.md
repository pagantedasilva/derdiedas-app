---
name: ux-copy-for-german-learners
description: >
  Use when writing or editing any user-facing text for the app: buttons, feedback, rule explanations, onboarding,
  notifications, error messages, store listing text, release notes, or FAQ answers.
---

# UX copy for a German gender-learning app

## Voice

Calm, encouraging, clear. Like a patient teacher who respects the learner's time. Short sentences, active voice, everyday words. No jokes at the learner's expense. No exclamation marks except for rare milestones.

## Rules

1. **Plain English first** (or the UI language of the build). Use simple words a B1 reader of that language understands.
2. **Say what happens.** Buttons name the action: "Start practice", "Next", "Skip for now".
3. **Never shame.** Don't say wrong, failed, bad, mistake. Say "It's die Zeitung" or "Not quite. This one is die."
4. **Explain the why in one line** when a rule exists, and label its strength honestly: "Words ending in -ung are feminine" vs "Words ending in -e are usually feminine." Only use rules from `german-gender-reference`.
5. **German text is exact.** Nouns capitalized, umlauts correct, article shown with the noun.
6. **Consistent terms.** Use the terms in `docs/voice.md`: *article*, *noun*, *session*, *review*. Do not alternate synonyms.
7. **Notifications** are optional reminders, not nags: one short line, no guilt, quiet by default.
8. **Errors** say what happened and what to do next, in one or two sentences, with no codes shown to users.
9. **Permission prompts** explain the benefit in the learner's words before the system prompt appears.

## Length limits (defaults)

- Button: 1 to 3 words
- Feedback line: up to 60 characters
- Rule explanation: up to 120 characters
- Notification: title up to 30, body up to 80 characters
- Store title: 30 characters; subtitle: 30 (iOS); short description: 80 (Google Play)

Allow 40% extra space for translations in the string layout.

## Deliverable format

A table with: `key`, text, context note, max length, character count. Keys are identical on iOS and Android and use the pattern `screen.element.purpose` (for example `practice.answer.der`). Provide the iOS String Catalog and Android `strings.xml` files from the same table.

## Examples

| Situation | Don't | Do |
|---|---|---|
| Wrong answer | "Wrong! Try again." | "Not quite. It's die Zeitung. Words ending in -ung are feminine." |
| Reminder | "Don't lose your streak!" | "Five nouns are ready when you are." |
| Offline | "Error 503" | "You're offline. Practice still works." |
| Rule with exceptions | "-e words are feminine." | "Words ending in -e are usually feminine." |

## Checklist before handing off

- Every string has a key, context, and length check.
- All German examples verified against `german-gender-reference`.
- No shaming words, no pressure language, terms match the voice guide.
- Strings can wrap to two lines and still make sense.
