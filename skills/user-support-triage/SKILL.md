---
name: user-support-triage
description: >
  Use when handling a user email, store review, or feedback message: classify it, reply, and create well-formed tasks
  for bugs, content errors, and feature requests. Don't use to promise fixes or decide refunds.
---

# User support triage

## Step 1: Classify

| Type | Signal | Action |
|---|---|---|
| Learning question | "Why is it das Mädchen?" | Answer using `german-gender-reference` |
| Content error | "You say der but it's die" | Verify, then task or kind correction |
| Bug | crash, freeze, wrong score, missing data | Bug task for the right developer |
| Feature request | "Please add..." | Log, thank, no promise |
| Account, billing, refund | purchase, subscription | Board approval needed for refunds |
| Privacy or legal | data request, lawyer, press | Escalate to CEO immediately, do not reply in detail |

## Step 2: Reply principles

- Reply in the learner's language when you can write it well; otherwise simple English.
- First line answers the question or acknowledges the problem. No long apologies.
- Be specific about what you need (device, OS, app version, what they tapped).
- Never promise a date, a fix, or a feature. Say "I've passed this to the team."
- Never ask for passwords or payment details.
- Keep to 120 words unless the question needs more.

Reply template:

```
Hi <name>,
<one-line answer or acknowledgement>
<what we need from you / what you can try, if anything>
<closing line>
```

## Step 3: Bug task format

```
Title: <short symptom> on <platform>
App version / OS / device:
Steps to reproduce:
Expected:
Actual:
Frequency: once / sometimes / always
User count: <number of reports so far>
Owner: iOS Developer or Android Developer
```

Add "both platforms?" if unknown; the CEO decides who investigates.

## Step 4: Content error check

1. Find the noun in the content source and in `german-gender-reference`.
2. If the app seems wrong: task for the **German Content Editor** labeled `content-error` with noun, article shown, article the user expects, app version, and the CEO copied. Wait for their verdict before telling the user the app was wrong.
3. If the user is wrong: explain kindly with the rule or the exception, and thank them for checking.
4. If it is regional or contested (a few nouns vary), say so honestly; the German Content Editor decides how it is handled.

## Step 5: Reviews

- Public replies are short and kind. Never argue. Never reveal user data.
- For a negative review: thank, state what you can do, invite an email so you can help.
- Draft review replies for the board's approval until the board says replies may go out automatically.

## Weekly digest to the CEO

Top five themes with counts, new bugs, content errors found, most requested feature, one change that would reduce the most contacts.

## FAQ maintenance

When a question repeats three times, add it to `docs/faq.md` and create a task for the UX Copy Expert to polish the wording.
