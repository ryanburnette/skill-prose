---
name: prose
description: Write clear, brief, accurate prose for a human reader. Use when writing or editing anything a person will read, such as a message, technical docs, a code comment, or a commit message. Applies guidance for the specific context and can also clean up existing text.
---

Anything a person will read should be clear, brief, and accurate. Different kinds
of writing weight those three differently, so this skill has a core that always
applies and profiles that tune it for the context.

Fix a habit when it costs clarity or brevity, not because it looks a certain
way. That keeps the guidance useful across models, which each have their own tics.

## Core

Always on, under every profile. Each principle comes with a test you can run on
a sentence.

**Clarity.** Lead with the point; keep each sentence to one main idea. The
strongest lever is grammatical: make the real actor the subject and the action
the verb, and undo nominalizations, where a verb is hidden inside a noun.
Passive voice is fine when the thing acted on is what you want to talk about
("the row was already deleted"); convert it only when it hides who acted. Test:
if the reader stopped after your first sentence, would they have the answer? If
not, move it up.

- "The guide provides a description of the API." => "The guide describes the API." (verb un-buried)
- "The migration was run by the on-call engineer." => "The on-call engineer ran the migration." (actor as subject)

**Brevity.** Write the shortest version that keeps the meaning. Run the deletion
test: drop each word or qualifier, and if the sentence still means the same
thing, leave it out. But brevity never removes load-bearing content: the reason,
the number, the ticket link, anything the reader can't reconstruct. Cutting a
needed clause is a worse error than one extra sentence. For inflated verbs to
replace, see Inflated vocabulary in the Quick reference.

- "It's worth noting that the API will reject any input that happens to be empty." => "The API rejects empty input."
- Too far: "Reverted." => "Reverted the cache change; it broke prod login (#482)."

**Accuracy.** Say only what you can stand behind. Keep a qualifier when it
changes what is true; cut it when it only softens tone. "Usually" in "the cache
is usually cold" carries information and stays; "I think" in "I think the API
rejects empty input" does not and goes. Don't inflate significance. Verify names,
paths, and facts before asserting them.

- "This groundbreaking fix dramatically improves everything." => "This fix cuts p99 latency by 40%."

Brevity and accuracy pull against each other sometimes. Accuracy wins: a needed
qualifier is not padding.

## Pick the context

Figure out what you are writing, then apply that profile on top of the core. If
none fits, the core alone is enough. Getting this wrong is cheap: the core is
always on and carries the high-value rules, so a misread costs you a mismatched
structure at worst, not a bad answer. When two profiles fit, don't pick one. Take
the primary from the delivery channel and borrow from the other: a PR
description is direct-communication intent in docs structure (what, why,
how-to-test).

### Direct communication

Chat, PR replies, Slack, email to a person who shares your context.

- Answer first (bottom line up front). Say the conclusion or the ask in the
  opening line, then support it.
- Assume shared context. Don't recap what they just said.
- Terseness reads as respect for their time, not rudeness, but don't cut context
  the reader needs to act. Skip pleasantries, not substance.
- Match courtesy to the reader. A peer in a thread needs none; an external or
  non-technical reader still gets a brief, warm frame. Cut ceremony, not the
  warmth that is the substance for them.
- No headers on a three-line reply. No structure for its own sake.

Example: "Can't repro on main. What commit are you on?" not "Thanks for
flagging this! I attempted to reproduce the issue you described but was unable
to. Could you let me know which commit you're on?"

### Technical documentation

READMEs, guides, reference docs. Ask what the reader needs, then serve one need
per section. Those needs map to four kinds ([Diátaxis](https://diataxis.fr/)):

- *tutorial*: teach a beginner by doing; take them by the hand to a result.
- *how-to*: steps to accomplish one task for someone who has the basics.
- *reference*: dry, complete facts to look up; describe, don't narrate.
- *explanation*: the why and the tradeoffs; background, not steps.

A whole document often mixes these (a README has a bit of each), but a single
section should not. Blurring them within one section is the most common docs
failure. Then:

- Clarity and completeness outrank brevity here. Structure, lists, and examples
  earn their space when they help the reader.
- Accuracy matters most in this profile; wrong docs are worse than no docs.
  Verify commands, flags, paths, and versions against the current code, and run
  examples before claiming they work.
- State prerequisites and the gotchas that bite.
- A recognized pattern (cause and fix, what/why/how-to-test) earns light
  structure. That is not the decoration the core warns against.
- Skip marketing tone and significance inflation.

#### Simplified Technical English (optional)

For steps, how-tos, troubleshooting, runbooks, and READMEs aimed at a broad or
non-native audience, or whenever the author asks, apply a flexible adaptation of
Simplified Technical English: short imperative sentences, one instruction each,
active voice, one term per concept. Load `references/simplified-technical-english.md`
for the full rules and examples. Skip it for prose that needs a voice: design
rationale, explanation, a persuasive overview.

### User-facing text

Error messages, CLI output, empty states, changelogs: prose a person reads at a
bad moment or while scanning.

- State the cause and the next action. "FOO_TOKEN is not set. Set it and re-run."
  not "An error occurred."
- No blame, no apology theater, no filler ("Please", "in order to", "kindly").
- Plain words over internal jargon; the reader didn't write your code.
- Changelogs and release notes: group by change type, describe the user-visible
  effect, don't narrate the implementation ("empty bodies no longer 500", not
  "added a nil check").

### Code comments

- Explain why, not what. The code already says what.
- Match the file's existing comment density and idiom. Don't impose a new style.
- Comment the non-obvious: intent, a tradeoff, a gotcha, a link to the issue.
- Don't restate the line below it, and don't add decorative comments.

### Commit messages

- The repo's conventions win. The AGENTS.md "Commit Messages" section is the
  source of truth: lowercase start, scope prefix, one logical change, no AI
  attribution.
- Where it is silent, follow the common defaults: imperative subject ("add", not
  "added"), roughly 50 characters or less, a blank line, then a body that
  explains what and why rather than how ([Beams' seven rules](https://cbea.ms/git-commit/);
  scope prefix from Conventional Commits).
- The subject should read cleanly in a log: "fix: reject empty payloads before
  enqueue", not "update code".

## Modes

How to apply the skill to a specific piece of text.

- `detect`: flag issues only, don't rewrite. Output one line each: quote the
  text, name the issue, suggest the fix. Use when the author wants to decide, or
  is auditing text they don't want altered.
- `rewrite`: return a clean version, then list what changed and why.
- `edit`: change the file in place with minimal, targeted edits. Leave clean
  passages alone. Don't rewrite quoted material, code blocks, or text attributed
  to someone else; flag those instead. Re-read after to confirm.

Default to `rewrite` unless the author names a file to fix (`edit`) or asks to
flag only (`detect`). When writing *about* bad prose, cited examples are exempt;
only fix the author's own text.

## Quick reference

A scan-list for a detect or edit pass, kept complete on purpose: some items are
the Core principles turned into specific habits to catch, the rest are tells the
Core doesn't name. Fix on sight when they add nothing.

- Buried answer; throat-clearing opener ("Great question!", "In this section
  we'll explore"); padding closer ("Let me know if...").
- Hedging, especially stacked ("could potentially", "may eventually"; pick one).
- "It's not X, it's Y" framing => a direct positive statement.
- Over-bolding: don't bold every key term, and don't lead list items with
  `**Word:** explanation` unless it's a real definition list.
- Forced rule-of-three; vary groupings, two or four is fine.
- Uniform rhythm. Metronomic sentence and paragraph length is a bigger tell than
  any single word. In anything longer than a few lines, read it back: if every
  sentence runs the same length and shape, combine two or break one. Let some
  paragraphs be one line. (Skip this for a three-line reply; rhythm only shows
  over length.)
- Vague attribution ("studies show") => cite it or cut it.

Inflated vocabulary is filler: use the plainest word that keeps the meaning. Some
tells worth recognizing (examples, not a find-replace list): underscores, serves
as, testament to, showcase, leverage, utilize, delve or deep-dive, streamline,
and robust or comprehensive when they're decoration. Keep the word when it's the
precise term (robust statistics, financial leverage, a comprehensive test suite);
swap it only when it adds nothing.

Glyphs, last and least: em-dashes, curly quotes, and double spaces read as
machine defaults to some people. Swap them if you care, but don't spend real
energy on it.
