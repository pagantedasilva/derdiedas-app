---
name: mobile-qa-and-accessibility
description: >
  Use when writing test plans, testing iOS and Android builds, checking accessibility, filing defects, running the
  release smoke test, or giving a go or no-go recommendation. Don't use to fix code.
---

# Mobile QA and accessibility

## Device matrix (minimum)

| Platform | Small | Large | Older OS |
|---|---|---|---|
| iOS | small iPhone | large iPhone, one iPad | oldest supported iOS |
| Android | small phone (about 5 in) | large phone and one tablet | oldest supported API level |

Use simulators and emulators for most cases; run the release smoke test on at least one real device per platform if the board provides them. Say in the report what was real and what was emulated.

## Test plan template

```
Feature / build:
Spec and task links:
Risks:
Cases: id, steps, expected result, platform(s)
Out of scope:
```

## Core cases every release

1. Fresh install, onboarding, skip and complete.
2. Practice session: correct answer, wrong answer, rule shown, session summary.
3. Review queue: due nouns appear, order sensible, empty queue state.
4. Persistence: kill the app mid-session, relaunch, progress intact.
5. Offline: airplane mode, practice still works.
6. Settings: reminders, sound, haptics, text size, theme, data delete.
7. Interruptions: incoming call, background and return, rotation (tablet), low battery mode.
8. Upgrade from the previous version keeps progress.

## Cross-platform parity

Take a script of 20 answers (mix of right and wrong). Run it on iOS and Android from a fresh install with the same noun list. The resulting intervals and due dates must match the table in `docs/scheduling.md`. Any difference is a **high** severity defect.

## Content check

Compare the in-app article for sampled nouns with the German Content Editor's file: at least 50 per release plus every entry changed since the last build. A wrong article is a **high** defect and goes to the German Content Editor, not a developer.

## Accessibility checklist

- Screen reader: VoiceOver and TalkBack can complete a full session; answer buttons read "der", "die", "das"; focus order is logical; feedback is announced.
- Text scaling to the largest system setting without truncation of key content.
- Contrast meets WCAG AA in light and dark themes.
- Color is never the only signal.
- Reduced motion respected.
- Touch targets at least 44 pt (iOS) and 48 dp (Android).
- Works with hardware keyboard or switch access where the platform allows.

## Defect format

```
Title: <symptom> on <platform>
Severity: high (blocks learning, data loss, crash, wrong German) | medium | low
Build / OS / device:
Steps to reproduce:
Expected:
Actual:
Reproducible: always / sometimes / once
Evidence: screenshot or recording reference
Owner: iOS Developer | Android Developer | German Content Editor | UX Designer
```

One defect per task. If unsure which platform, test both before filing.

## Severity and go or no-go

- **No-go:** any open high defect, crash on launch or in the core loop, data loss, a wrong article in sampled content, failed accessibility on the core loop.
- **Go with note:** only medium or low defects, listed in the report.
- The CEO makes the final call; you give a clear recommendation and the reasons.

## Release smoke test (about 15 minutes per platform)

Install, onboard, complete a session, force quit, relaunch, offline session, change text size, switch theme, open settings. Report pass or fail per step.

## Regression

Every escaped bug gets a case in `docs/qa/regression.md` with a link to the defect. Re-run the regression list before each release candidate.

## Report format

```
Build: <version and build number>
Devices: <list, real or emulated>
Passed: <count>   Failed: <count>
Defects: <links, with severity>
Accessibility: pass / issues
Parity: pass / issues
Content sample: <n checked, n wrong>
Recommendation: GO | NO-GO, <reason>
```
