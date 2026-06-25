---
name: strip-ai-tells
description: Audit, rewrite, or edit text to strip AI writing tells and tighten prose. Use when cleaning up AI-generated text, comments, docs, commit messages, or markdown, or when you want a full prose pass. Fixes dashes, inflated vocabulary, hedging, over-bolding, and structural tells.
---

The always-on subset of these rules lives in `~/.agents/AGENTS.md` under Prose
Style and applies to every response. This skill is the full pass: invoke it when
you want to audit or clean a specific piece of text.

The goal is prose that reads like a person wrote it: direct, concrete, short. AI
tells make writing feel stiff and templated. Stripping them is about readability,
not disguising authorship.

Signals, not proof. These patterns are more common in AI text, but humans writing
fast produce the same shapes. Use them to improve writing, not to judge authorship.

## When to trigger

- User asks to "de-AI", "clean up", or tighten text
- Reviewing AI-written comments, docs, commit messages, or markdown
- Any post-generation cleanup pass

## Modes

- `detect` — flag tells only, quote the offending text, don't rewrite. Use when the
  user wants to decide for themselves or is auditing text they don't want altered.
- `rewrite` — return a clean version with the tells removed, then list what changed.
- `edit` — change the file in place with minimal, targeted edits. Leave passages
  that are already clean untouched. Don't rewrite quoted material, code blocks, or
  text attributed to someone else; flag those instead. After editing, re-read and
  confirm the tells are resolved.

Default to `rewrite` unless the user names a file to fix (`edit`) or asks to flag
only (`detect`). When writing about AI tells, quoted examples are exempt: only fix
the author's own prose, not cited examples of bad writing.

## Formatting rules

### Dashes

- Avoid em-dashes (`—`) and en-dashes (`–`); they're a dead giveaway
- Don't fake the same dramatic pause with a spaced hyphen (` - `) either. The tell
  is the aside, not the glyph. Restructure into two sentences, a comma, or parentheses
- Exception: code comments where the author's existing style uses them

### Arrows

- Replace `→` and emoji arrows with `=>`
- `EC P-256 => ES256` not `EC P-256 → ES256`

### Bullets and lists

- Use `-` for unordered lists, not `*` or `•`
- Don't add trailing periods to list items unless every item is a full sentence
- Don't mix periods and no-periods in the same list

### Bold and emphasis

- Don't bold every key term on first mention
- Don't bold list item leads (`**Word:** explanation`) unless it's a definition list
- Prefer backticks for code and identifiers over bold

### Headers

- Don't add unnecessary section headers for short content; a 3-line answer doesn't
  need an `## Answer` header
- Sentence-case headings, not Title Case
- More than 3 headings in under 300 words is structure for its own sake; use prose

### Sentence spacing

- One space after periods, not two

### Quotes and punctuation

- Use straight quotes (`"`, `'`), not curly/smart quotes, in plain-text and code
- Commas and periods go inside quotes (American English)

### Emoji

- No emoji in technical writing; no checkmarks, warning signs, or decorative emoji

## Sentence and structure tells

- Lead with the answer. Cut throat-clearing openers ("Great question!", "Certainly!",
  "In this section we'll explore") and padding closings ("Let me know if...")
- State it; don't hedge. Drop "it's worth noting", "I think", "perhaps", "arguably"
- Don't stack hedges: "could potentially", "may eventually" cancel out. Pick one
- "It's not X, it's Y" / "isn't about X, it's about Y" => a direct positive statement
- Don't avoid "is" and "has" with inflated verbs ("serves as", "boasts", "features")
- Don't force the rule of three. Vary groupings; two or four items are fine
- Vague attributions ("experts believe", "studies show") => cite the source or cut
- Rhetorical-question openers ("But what does this mean?") => just say the answer
- Significance inflation ("a pivotal moment", "the future looks bright") => state what
  happened and let the reader judge
- "This is because..." as an opener => just state the reason

## Inflated vocabulary

Replace on sight when used as filler. Plain words are usually right.

| Replace | With |
|---|---|
| delve / dive into / deep dive | look at, explore, dig into |
| leverage / utilize | use |
| robust | strong, reliable, solid |
| comprehensive | thorough, complete, full |
| seamless / seamlessly | smooth, easy |
| cutting-edge | latest, newest |
| pivotal / crucial | important, key |
| underscores | highlights, shows |
| testament to | shows, proves |
| meticulous | careful, precise |
| showcase / showcasing | show, demonstrate |
| unpack | explain, break down |
| holistic | complete, whole |
| actionable | practical, concrete |
| impactful | effective, significant |
| learnings | lessons, findings |
| best practices | what works, standard approach |
| in order to | to |
| due to the fact that | because |
| serves as | is |
| boasts / features (verb) | has, includes |
| facilitate | help, enable, run |
| streamline | simplify, speed up |
| foster | encourage, build |
| empower | enable, let |
| myriad / plethora | many |
| ecosystem (metaphor) | system, network, market |
| realm / landscape (metaphor) | area, field, space |
| paradigm | model, approach |
| embark / commence | start, begin |

## Rhythm

Uniform sentence and paragraph length is a bigger tell than any single word. Mix
short sentences with long ones. Some paragraphs should be one line. If the text
reads at a single metronomic pace, vary it.

## Before / after

- "This is because the cache is cold." => "The cache is cold."
- "It's worth noting that the API rejects empty input." => "The API rejects empty input."
- "**Speed:** the new path is faster." => "The new path is faster."
- "We leveraged a robust, comprehensive solution to streamline the pipeline." => "We simplified the pipeline."
- "But what does this mean for users? It means faster loads." => "Users get faster loads."
- "The migration serves as a testament to the team's meticulous work." => "The migration shows the team's careful work."
