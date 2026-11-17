# Der Die Das Studio: Paperclip company package

A ready-to-import [Paperclip](https://docs.paperclip.ing/) company (Agent Companies `agentcompanies/v1` format) for building and growing a mobile app that teaches the German articles der, die, das.

## Contents

```
paperclip-derdiedas/
├── COMPANY.md                  company goal, org chart, operating rules
├── .paperclip.yaml             adapter and env overrides (edit models here)
├── agents/
│   ├── ceo/AGENTS.md
│   ├── ios-developer/AGENTS.md
│   ├── android-developer/AGENTS.md
│   ├── devops-engineer/AGENTS.md
│   ├── german-content-editor/AGENTS.md
│   ├── qa-tester/AGENTS.md
│   ├── ux-designer/AGENTS.md
│   ├── ux-copy-expert/AGENTS.md
│   ├── marketing-manager/AGENTS.md
│   └── support-specialist/AGENTS.md
└── skills/
    ├── derdiedas-product-context/        shared: fill in the TODOs first
    ├── german-gender-reference/          shared: verified gender rules
    ├── ceo-prioritization-and-delegation/
    ├── ios-swiftui-development/
    ├── android-compose-development/
    ├── mobile-ci-cd-and-release/
    ├── german-content-curation/
    ├── mobile-qa-and-accessibility/
    ├── ux-mobile-learning-design/
    ├── ux-copy-for-german-learners/
    ├── app-marketing-and-aso/
    └── user-support-triage/
```

## Before you import

1. Open `skills/derdiedas-product-context/SKILL.md` and replace each `TODO` (app name, repos, business model, languages, content source).
2. Open `.paperclip.yaml` and set the adapter `type` and `model` you actually run. All agents default to `claude_local` with `claude-sonnet-4-6`.
3. Have the German gender rules in `skills/german-gender-reference/SKILL.md` reviewed by a German speaker once. A few "exception" entries are flagged "check" on purpose.

## Import

Preview first (nothing is created):

```bash
paperclipai company import ./paperclip-derdiedas --target new --new-company-name "Der Die Das Studio" --dry-run
```

Then import for real:

```bash
paperclipai company import ./paperclip-derdiedas --target new --new-company-name "Der Die Das Studio"
```

To add it to a company you already have:

```bash
paperclipai company import ./paperclip-derdiedas --target existing --company-id <your-company-id> --include agents,skills
```

You can also push this folder to a GitHub repository and import it with `paperclipai company import <owner>/<repo>`.

## After import

1. Check each agent's attached skills (agents list their skills in `AGENTS.md`; confirm in the Paperclip UI).
2. Give the DevOps Engineer the optional `GH_TOKEN` secret only when you want it to open pull requests.
3. Give the CEO its first task: "Plan the v1.0 scope and create the first set of tasks."
4. Approve budgets per agent in Paperclip before turning heartbeats on.

## Notes

- iOS and Android have separate agents so they can work in parallel. If you prefer one mobile developer, merge the two `AGENTS.md` files and attach both skills.
- Every agent must ask the board before spending, publishing, submitting to a store, or touching secrets. Those gates are written into each `AGENTS.md`.
- The spec and file names were checked against the Paperclip docs on the day this was created. If an import reports a schema error, run with `--dry-run` and compare with the [export/import guide](https://docs.paperclip.ing/guides/power/export-import).
