# skill-strip-ai-tells

Audit, rewrite, or edit text to strip AI writing tells and tighten prose. Use when reviewing or cleaning up AI-generated text, comments, docs, commit messages, or markdown. Fixes dashes, inflated vocabulary, hedging, over-bolding, and structural tells.

## Why

The goal is to make AI-assisted text read more naturally and approachably, not to deceive anyone. AI tools have characteristic habits (em-dashes everywhere, inflated vocabulary, over-bolding, decorative emoji, "Great question!" openers) that make writing feel stiff and templated. This skill strips those habits so the result reads like something a person actually wrote, in your own voice. It's about quality and readability, not disguising authorship.

The skill is the full pass and runs in three modes (detect, rewrite, edit). A trimmed always-on subset of these rules lives in the user's global `AGENTS.md` under Prose Style, so every response gets some benefit without invoking the skill.

## Usage

This is an [Agent Skills](https://agentskills.io/) compatible skill. Load it with your agent harness and invoke via `skill:strip-ai-tells`.

## Structure

- `SKILL.md` — Skill instructions and frontmatter
