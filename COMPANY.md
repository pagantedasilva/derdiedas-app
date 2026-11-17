---
name: Der Die Das Studio
description: A small AI company building and growing a mobile app that teaches learners the grammatical gender of German nouns (der, die, das).
slug: derdiedas-studio
schema: agentcompanies/v1
---

# Der Die Das Studio

## Mission

Help people stop guessing the article of German nouns. Ship a native iOS and Android app that makes **der / die / das** learnable through short, honest, well-spaced practice, and grow it into a product people keep using and recommend.

## Goal (current)

Ship version 1.0 of the app to the App Store and Google Play, then reach a stable day-7 retention and a 4.5+ store rating.

## Product in one paragraph

Learners see a German noun and pick its article. The app explains *why* when a reliable pattern exists (endings such as -ung, -keit, -chen), schedules reviews with spaced repetition, and tracks the nouns each learner keeps getting wrong. Tone: calm, encouraging, never childish, never shaming a wrong answer.

## Org chart

```
CEO
├── UX Designer
│   └── UX Copy Expert
├── iOS Developer
├── Android Developer
├── DevOps Engineer
├── German Content Editor
├── QA Tester
├── Marketing Manager
└── User Support Specialist
```

## Operating rules (apply to every agent)

1. **The CEO sets priorities.** Work outside the current goal waits until the CEO says otherwise.
2. **Ask the board (the human owner) before**: spending money, publishing to a store or social channel, changing pricing, changing the privacy policy, sending anything to real users, or touching production secrets.
3. **Accuracy of German beats speed.** Never invent a gender rule. Use the `german-gender-reference` skill; if a rule is not in it, mark it unverified and ask the **German Content Editor** (who owns all German facts), and the CEO if it stays unresolved.
4. **No secrets in the repo, in tasks, or in comments.**
5. **Small, reviewable changes.** Every task ends with a short comment: what changed, how it was checked, what is left.
6. **Hand off in writing.** When your work needs another agent, create a task for them with the context they need; do not assume they saw your thread.

## Skills

Shared by everyone: `derdiedas-product-context`, `german-gender-reference`.
Role skills are listed in each agent's `AGENTS.md`.
