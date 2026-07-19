---
name: prose
description: Write clear, brief, accurate prose for a human reader. Use when writing or editing anything a person will read, such as a message, technical docs, a code comment, or a commit message. Applies guidance for the specific context and can also clean up existing text.
---

Anything a person will read should be clear, brief, and accurate. That is the
whole job. Different kinds of writing weight those three differently, so this
skill has a core that always applies and profiles that tune it for the context.

This replaces chasing "AI tells." Habits like hedging or a buried answer get
fixed because they hurt clarity or brevity, not because they look machine-made.
Glyph policing (em-dashes, curly quotes) is near the bottom of what matters and
varies by model, so it is a footnote here, not the point.

## Core

Always on, under every profile.

**Clarity.** Lead with the point. One idea per sentence. Concrete over abstract.
Name things precisely instead of gesturing at them.

**Brevity.** Write the shortest version that keeps the meaning. Cut
throat-clearing openers and padding closings. Use plain verbs ("is", "use",
"shows") over inflated ones ("serves as", "leverage", "underscores").

**Accuracy.** Say only what you can stand behind. Keep a qualifier when it
changes what is true; cut it when it only softens tone. "Usually" in "the cache
is usually cold" carries information and stays; "I think" in "I think the API
rejects empty input" does not and goes. Don't inflate significance. Verify
names, paths, and facts before asserting them.

Brevity and accuracy pull against each other sometimes. Accuracy wins: a needed
qualifier is not padding.

## Pick the context

Figure out what you are writing, then apply that profile on top of the core. If
none fits, the core alone is enough.

### Direct communication

Chat, PR replies, Slack, email to a person who shares your context.

- Dense and answer-first. Say the conclusion or the ask in the first line.
- Assume shared context. Don't recap what they just said.
- Terseness reads as respect for their time, not rudeness. Skip pleasantries.
- No headers on a three-line reply. No structure for its own sake.

Example: "Can't repro on main — what commit are you on?" not "Thanks for
flagging this! I wanted to follow up. I attempted to reproduce the issue you
described, but I was unable to. Could you let me know which commit you're on?"

### Technical documentation

READMEs, guides, reference docs.

- Goal: the reader can act correctly without you present.
- Clarity and completeness outrank brevity here. Structure, lists, and examples
  are welcome when they help the reader.
- Show a working example. State prerequisites and the gotchas that bite.
- Accuracy matters most in this profile. Wrong docs are worse than no docs.
- Still skip marketing tone and significance inflation.

### Code comments

- Explain why, not what. The code already says what.
- Match the file's existing comment density and idiom. Don't impose a new style.
- Comment the non-obvious: intent, a tradeoff, a gotcha, a link to the issue.
- Don't restate the line below it, and don't add decorative comments.

### Commit messages

- Follow the repo's conventions. The AGENTS.md "Commit Messages" section is the
  source of truth: lowercase start, scope prefix, one logical change, no AI
  attribution.
- Subject line should make sense scanning a log. Body explains why when the
  change isn't self-evident.
- "fix: reject empty payloads before enqueue" not "update code" or a paragraph.

## Modes

How to apply the skill to a specific piece of text.

- `detect` — flag issues only, don't rewrite. Output one line each: quote the
  text, name the issue, suggest the fix. Use when the author wants to decide, or
  is auditing text they don't want altered.
- `rewrite` — return a clean version, then list what changed and why.
- `edit` — change the file in place with minimal, targeted edits. Leave clean
  passages alone. Don't rewrite quoted material, code blocks, or text attributed
  to someone else; flag those instead. Re-read after to confirm.

Default to `rewrite` unless the author names a file to fix (`edit`) or asks to
flag only (`detect`). When writing *about* bad prose, cited examples are exempt;
only fix the author's own text.

## Quick reference

The habits that most often cost clarity or brevity. Fix on sight when they add
nothing.

- Buried answer; throat-clearing opener ("Great question!", "In this section
  we'll explore"); padding closer ("Let me know if...").
- Hedging, especially stacked ("could potentially", "may eventually" — pick one).
- "It's not X, it's Y" framing => a direct positive statement.
- Over-bolding: don't bold every key term, and don't lead list items with
  `**Word:** explanation` unless it's a real definition list.
- Forced rule-of-three; vary groupings, two or four is fine.
- Uniform rhythm. Metronomic sentence and paragraph length is a bigger tell than
  any single word. Mix short with long; let some paragraphs be one line.
- Vague attribution ("studies show") => cite it or cut it.

Inflated vocabulary, replace when used as filler:

| Replace | With |
|---|---|
| delve / dive into / deep dive | look at, explore, dig into |
| leverage / utilize | use |
| robust | strong, reliable, solid |
| comprehensive | thorough, complete, full |
| seamless / seamlessly | smooth, easy |
| pivotal / crucial | important, key |
| underscores | highlights, shows |
| testament to | shows, proves |
| showcase | show, demonstrate |
| in order to | to |
| due to the fact that | because |
| serves as | is |
| boasts / features (verb) | has, includes |
| facilitate | help, enable |
| streamline | simplify, speed up |
| myriad / plethora | many |
| leverage (metaphor) / paradigm | model, approach |

A word here is only wrong as filler. When it's the precise term (robust
statistics, financial leverage), leave it.

Glyphs, last and least: em-dashes (`—`), en-dashes (`–`), curly quotes, and
double spaces after periods read as machine defaults to some people. Swap them
for a comma, parentheses, or two sentences if you care. Don't spend real energy
chasing them across models — it's the lowest-value item on this page.
