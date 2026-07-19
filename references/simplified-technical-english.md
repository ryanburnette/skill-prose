# Simplified Technical English (flexible adaptation)

A flexible adaptation of [ASD-STE100](https://www.asd-ste100.org/) Simplified
Technical English for developer docs. Use the readability rules, not the
certification apparatus: don't enforce the ~900-word approved dictionary, and
don't drop necessary technical terms.

## When to use it

Reach for STE on:

- install and setup steps
- how-tos and procedures
- troubleshooting entries and runbooks
- reference material and READMEs aimed at a broad or non-native audience
- anything the author explicitly asks to be written this way

Skip it when the prose needs a voice:

- design rationale and explanation ("why" sections)
- an overview meant to persuade or give context
- anything narrative

The test: if the reader is *doing* a task, STE helps. If the reader is
*understanding* an idea, it flattens prose that benefits from voice.

## Rules

- One instruction per sentence. Put two instructions in one sentence only when
  the actions happen at the same time.
- Use the imperative for steps: "Run `make`", not "the build is started by
  running make".
- Short sentences: aim for 20 words or fewer in steps, 25 in descriptive text.
- Active voice. Use passive only when the actor is unknown or irrelevant.
- Simple tenses (present, past, simple future). Avoid perfect and progressive
  forms where a simple one works.
- One term per concept. Pick a name and reuse it verbatim; don't switch between
  "directory" and "folder" for the same thing.
- Break noun stacks longer than three words: "gear retraction winch handle"
  becomes "the handle for the gear-retraction winch".
- Keep paragraphs short: about six sentences or fewer in descriptive text.
- Define an abbreviation on first use, then use it consistently.
- Avoid idioms, slang, and cultural references; they trip non-native readers.

## Before and after

Procedure, buried in one long sentence:

> Once you have installed the dependencies, the configuration file will need to
> be created, after which the service can be started.

becomes:

> 1. Install the dependencies.
> 2. Create the configuration file.
> 3. Start the service.

Description, passive and noun-heavy:

> The system is designed so that incoming requests are handled by a pool of
> workers that have been pre-allocated at startup.

becomes:

> A pool of workers handles incoming requests. The service allocates the pool at
> startup.
