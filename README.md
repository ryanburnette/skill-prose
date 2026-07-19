# skill-prose

Write clear, brief, accurate prose for a human reader. Use when writing or
editing anything a person will read: a message, technical docs, a code comment,
or a commit message. Applies guidance tuned to the context, and can also clean
up existing text.

## Why

Anything a person reads should be clear, brief, and accurate. Habits that hurt
reading (a buried answer, hedging, inflated vocabulary) get fixed because they
cost clarity or brevity, not because they look a certain way.

The core (clarity, brevity, accuracy) always applies. On top of it, profiles
tune the guidance for four contexts: direct communication, technical
documentation, code comments, and commit messages. Each core principle carries a
concrete test, and the profiles anchor to established standards (Diátaxis for
docs, Beams' rules for commits) rather than inventing guidance from scratch. A
trimmed always-on subset lives in the user's global `AGENTS.md` under Prose
Style, so every response gets some benefit without invoking the skill.

## Modes

The full pass runs in three modes: `detect` (flag only), `rewrite` (return a
clean version), and `edit` (change a file in place). Default is `rewrite`.

## Usage

This is an [Agent Skills](https://agentskills.io/) compatible skill. Load it
with your agent harness and invoke via `skill:prose`.

## Structure

- `SKILL.md`: skill instructions and frontmatter
- `references/`: detail loaded on demand, kept out of the always-loaded file
  - `simplified-technical-english.md`: the STE adaptation for docs
