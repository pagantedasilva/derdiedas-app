---
name: mobile-ci-cd-and-release
description: >
  Use when setting up or changing CI, build pipelines, code signing, beta distribution, release candidates, store
  release checklists, or crash monitoring for the iOS and Android apps.
---

# Mobile CI/CD and release

## Pipeline targets

| Stage | iOS | Android |
|---|---|---|
| Pull request | build, unit tests, lint (SwiftLint) | build, unit tests, lint (Android lint, ktlint or detekt) |
| Merge to main | signed build to TestFlight | signed bundle (.aab) to Play internal testing |
| Release candidate | tagged build, release notes | tagged bundle, release notes |
| Store release | App Store Connect submission | Play Console staged rollout |

Use GitHub Actions unless the board chooses another system. Cache dependencies. A pull request pipeline should finish in under 15 minutes.

## Secrets and signing

- Secrets live only in the CI secret store. Refer to them by name (for example `APP_STORE_CONNECT_API_KEY`, `PLAY_UPLOAD_KEYSTORE_BASE64`). Never print their values or paste them in a task.
- When a secret is needed, create a task for the board listing the secret name, what it is for, and where to add it.
- iOS: prefer automatic signing with an App Store Connect API key, or fastlane match with a private certificate repo. Android: use Play App Signing; keep only the upload key in CI.
- Never rotate or revoke credentials without board approval.

## Versioning

- Semantic version `MAJOR.MINOR.PATCH` for the user-visible version on both platforms.
- Build number (iOS) and versionCode (Android) increase automatically on every CI release build and never repeat.
- Tag releases `v1.2.3`.

## Release checklist (for a release candidate)

1. All tasks in the release are closed and approved by the CEO.
2. CI green on main; no open crash in the previous beta with more than 1% of sessions.
3. Release notes drafted by the UX Copy Expert.
4. Store listing, screenshots, privacy label, and Data safety form match the build (ask the Marketing Manager and CEO).
5. QA Tester has run the release smoke test and regression list on both platforms and given a **go** recommendation in writing. A no-go blocks the release until the CEO decides.
6. **Board approves submission** in the task. Only then submit.
7. After release: watch crash-free sessions for 48 hours and report to the CEO.

Android uses staged rollout (for example 10%, 50%, 100%) with a pause if crash-free sessions fall under 99%.

## Monitoring

- Crash reporting on both platforms (board approves the provider). No personal data in crash reports.
- Alert the CEO when crash-free sessions drop under 99% or when store review rating drops by 0.3 or more in a week.

## Repository hygiene

- Protected main branch, required passing checks, no force pushes.
- `docs/release.md` explains how to cut a release, with every command.
- `.gitignore` excludes keystores, provisioning profiles, `.env`, build output.
- Dependency updates grouped weekly; major version bumps go through the owning developer.

## Task closing comment

Link the green run, describe what changed in the pipeline, list secrets the board must add (names only), and state the rollback step.
