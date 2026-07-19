# skill-prose

Write clear, brief, accurate prose for a human reader. Use when writing or
editing anything a person will read: a message, technical docs, a code comment,
or a commit message. Applies guidance tuned to the context, and can also clean
up existing text.

## Why

Anything a person reads should be clear, brief, and accurate. That is the goal.
This skill used to frame its job as stripping "AI tells," which turned into a
brittle, model-specific fight over em-dashes and curly quotes. The new framing
is positive: write well for the reader. The habits that genuinely hurt reading
(a buried answer, hedging, inflated vocabulary) still get fixed, but because
they cost clarity or brevity, not because they look machine-made. Glyph policing
is demoted to a footnote.

The core (clarity, brevity, accuracy) always applies. On top of it, profiles
tune the guidance for the four things worth distinguishing: direct
communication, technical documentation, code comments, and commit messages. A
trimmed always-on subset lives in the user's global `AGENTS.md` under Prose
Style, so every response gets some benefit without invoking the skill.

## Modes

The full pass runs in three modes: `detect` (flag only), `rewrite` (return a
clean version), and `edit` (change a file in place). Default is `rewrite`.

## Usage

This is an [Agent Skills](https://agentskills.io/) compatible skill. Load it
with your agent harness and invoke via `skill:prose`.

## Structure

- `SKILL.md` — skill instructions and frontmatter
