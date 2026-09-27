# skill-prose

Write clear, brief, accurate prose for a human reader. Use when writing or
editing anything a person will read: a message, technical docs, a code comment,
or a commit message. Applies guidance tuned to the context, and can also clean
up existing text.

## Why

Anything a person reads should be clear, brief, and accurate. Habits that hurt
reading (a buried answer, hedging, inflated vocabulary) get fixed because they
cost clarity or brevity, not because they look a certain way.

The core (clarity, brevity, accuracy, and what it is) always applies.
What it is applies when the sentence is there to say what a thing is.
A negative stays when it carries a fact the reader would miss.
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
