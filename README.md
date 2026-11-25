# skill-prose

Writing and editing guidance for messages, technical docs, code comments, and
commit messages. Activate it by explicitly requesting the `prose` skill by name.

## Why

Anything a person reads should be clear, brief, and accurate. Habits that hurt
reading (a buried answer, hedging, inflated vocabulary) get fixed because they
cost clarity, brevity, or readability, not because they look a certain way.

The core (clarity, brevity, rhythm, accuracy, and what it is) always applies.
Rhythm is the counterweight to brevity: applied sentence by sentence, a
brevity pass strips the words that join one claim to the next and leaves a
wall of short declaratives. What it is applies when the sentence is there to
say what a thing is. A negative stays when it carries a fact the reader would
miss.
On top of the core, profiles tune the guidance for five contexts: direct
communication, technical documentation, user-facing text, code comments,
and commit messages. Each core principle carries a concrete test, and
the profiles anchor to established
standards (Diátaxis for docs and Beams' rules for commits) rather than inventing guidance from
scratch.

## Modes

The full pass runs in three modes: `detect` (flag only), `rewrite` (return a
clean version), and `edit` (change a file in place). Default is `rewrite`.

## Usage

This is an [Agent Skills](https://agentskills.io/) compatible skill. Load it
with your agent harness and invoke via `skill:prose`.
