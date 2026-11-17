---
name: german-content-curation
description: >
  Use when creating, editing, validating, or auditing the noun database, example sentences, pattern tags, or rule
  statements used by the app. Don't use for UI wording; that is the UX Copy Expert's job.
---

# German content curation

## Data model (one file, shared by iOS and Android)

Each noun entry:

| Field | Required | Notes |
|---|---|---|
| `id` | yes | Stable, never reused (for example `n-000123`) |
| `lemma` | yes | Singular, capitalized, correct umlauts: `Zeitung` |
| `article` | yes | `der`, `die`, or `das` |
| `plural` | yes | Full plural form, or `null` if none (and flag `no_plural`) |
| `level` | yes | `A1`, `A2`, or `B1` at first |
| `meaning_en` | optional | One short gloss; other UI languages later |
| `example_de` | yes | One natural sentence using the noun with its article |
| `patterns` | optional | Tags such as `ending-ung`, `compound`, `weekday` |
| `exception_of` | optional | A pattern the noun breaks, such as `ending-e` |
| `variants` | optional | For nouns with a regional or accepted second gender, list both and mark `variable` |
| `source` | yes | Reference used (Duden, DWDS, Goethe-Institut word list) |

Version the file (`content_version` integer, bump on every delivery) and keep a `CHANGELOG` in `docs/content/`.

## Selecting nouns

1. Start from a published level list (for example the Goethe-Institut word lists) so levels are defensible.
2. Prefer concrete, everyday nouns first, plus the nouns that best illustrate each pattern.
3. For each pattern in the curriculum, include at least eight typical examples and every common exception at the same level.
4. Exclude nouns with unstable gender unless flagged `variable`, and exclude offensive vocabulary by default.

## Example sentences

- One short sentence, B1 or below grammar, natural, uses the noun in the nominative or accusative so the article is easy to read.
- No sentences that stereotype or stigmatize a group.
- No invented proper names tied to real people.

## Rule statements

For each pattern, produce: the pattern, the gender, the confidence tier (`always`, `very-reliable`, `usually`) from `german-gender-reference`, and 3 to 5 examples plus known exceptions. The UX Copy Expert writes the learner-facing text from this.

## Validation checklist (run before every delivery)

- No duplicate `lemma` + `article` pairs.
- Every entry has all required fields.
- `article` is one of der, die, das.
- Each `patterns` tag exists in the pattern list; each `exception_of` references a real pattern.
- Nouns tagged with an `always` rule actually follow it (for example every `-chen` noun is `das`).
- Compound nouns match the article of their last part.
- Sampled spelling check: 20 random entries re-verified against the named source.
- Counts: entries per level and per pattern are reported.

## Handling a content-error report

1. Reproduce: find the entry by lemma.
2. Verify in the named source (and a second source if they disagree).
3. Outcome: *app wrong* → fix, bump version, add changelog line, tell the QA Tester which entry to re-check; *user wrong* → write the explanation for the Support Specialist; *contested or regional* → set `variable`, tell the CEO.
4. Reply on the task with the source and the decision.

## Delivery comment

Version number, counts added, changed, and removed, validation result, sources used, and anything the developers must do (for example schema changes).
