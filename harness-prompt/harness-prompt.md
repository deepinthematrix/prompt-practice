# Harness docs bootstrap

You are setting up a new project so that any coding agent can work on it well. Your deliverable is a small set of markdown files, the **harness docs**, that capture the project's purpose, vocabulary, stack, and working rules. You write markdown only: no source code, no package manifests, no config files, no empty directories, no installs.

## Already known

<!-- Optional. Paste anything already decided: purpose, stack, rules. The interview skips whatever is settled here. Leave empty if nothing is decided yet. -->

## Organisation rules

<!-- Optional. Paste organisation-level rules that must appear in AGENTS.md verbatim: approved stacks, data handling, compliance. Leave empty for a personal project. -->

## Step 0: Look around

List what is already in the working directory. If any harness doc named in Step 2 already exists, read it and treat its contents as settled; you will update it, never replace it. Report what you found in two lines, then start the interview.

## Step 1: Interview

Interview the human in **rounds**. In each round, number the questions and give your recommended answer under each one, then stop and wait for replies. Ask only what earlier answers have unblocked; a question that depends on a question still open belongs to a later round. Facts you can find by looking (files present, tools installed) are yours to find, never the human's to answer.

Cover, at minimum:

- **Purpose**: who it is for, the problem, what the first release looks like (and in a line or two where it is heading afterwards), non-goals, hard constraints
- **Vocabulary**: the five to ten nouns the project will use constantly, and the synonyms to retire
- **Stack**: languages, frameworks, runtime, hosting, and why each was chosen (the why is what the ADR records)
- **Deviations**: the working practices in `AGENTS.md` below are defaults; ask only where the human wants to depart from them

The interview is done when you can fill every file in Step 2 without guessing. Anything still unknown at that point goes under an `## Open questions` heading in the file it belongs to, phrased as a question. Invent nothing.

## Step 2: Write the files

Write exactly these six files, following the skeletons. Keep each one short. Every line of `AGENTS.md` is read on every turn, so it carries steps and pointers; the detail lives in the file each pointer names. A file restates nothing that another file, or the repo itself, already says.

### `AGENTS.md`

```markdown
# <Project name>

<One sentence: what this project is, taken from docs/purpose.md.>

## Before working

- Read `CONTEXT.md` and use its terms. When a term is resolved in conversation, add it there.
- Read `docs/purpose.md` before proposing scope or features.
- Read the ADRs in `docs/adr/` that touch the area you are changing. Record a new ADR when a decision is hard to reverse, surprising without context, and the result of a real trade-off.

## Working practices

- Tests alongside code, in every change.
- Small, reviewable changes. Plan before a large one and confirm the plan first.
- <Deviations the human asked for, and organisation rules, verbatim. Omit the line if there are none.>

## Maintaining these docs

These files are living. Add terms, add ADRs, and delete lines that stop being true.

## Open questions

<Only if any remain. Otherwise omit the heading.>
```

### `CLAUDE.md`

```markdown
Read `AGENTS.md` before doing anything else. It is the canonical agent instructions file for this project.
```

### `CONTEXT.md`

```markdown
# <Project name>

<One or two sentences: what this context is and why it exists.>

## Language

**<Term>**:
<One or two sentences defining what it IS, not what it does.>
_Avoid_: <synonyms to retire>

**<Term>**:
...
```

Rules: be opinionated, one term per concept, synonyms under `_Avoid_`. Only terms specific to this project; general programming concepts stay out. No implementation detail.

### `docs/purpose.md`

```markdown
# Purpose

## Who it is for

## The problem

## What the first release looks like

<The first shippable version. Measurable where possible.>

## Beyond the first release

<One or two lines on where it is heading. Omit the heading if there is no vision beyond the first release.>

## Non-goals

## Constraints

<Hard constraints only: legal, technical, budgetary, contractual.>
```

### `docs/adr/0001-tech-stack.md`

```markdown
# Tech stack

<One to three sentences: the context, what was decided, and why.>

## Considered options

<Only when a rejected alternative is worth remembering. Otherwise omit the heading.>
```

### `README.md`

```markdown
# <Project name>

<One paragraph for a human reader: what it is and who it is for.>

- Purpose and scope: `docs/purpose.md`
- Working with agents on this repo: `AGENTS.md`
- Decisions: `docs/adr/`
```

## Step 3: Check, then report

Before finishing, check every item:

- Exactly the six files exist, and nothing else was created or installed.
- `AGENTS.md` fits on one screen, and every practice says what to do.
- Every glossary term has a definition and an `_Avoid_` line.
- The ADR says why, not only what.
- Every gap is under an `## Open questions` heading; nothing was invented.
- No file restates what another file, or the repo, already says.

Then end with three things: the list of files written, the open questions collected across all files, and one line telling the human where the next decision gets recorded.
