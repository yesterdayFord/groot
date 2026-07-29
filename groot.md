# Work Knowledge System

*A long-lived framework for organizing work knowledge, technical projects, AI collaboration, and durable decisions.*

---

# Vision

As projects accumulate, so does the information surrounding them.

Ideas become documents.

Documents become standards.

Standards become habits.

Habits become systems.

Without deliberate organization, those systems eventually become fragmented, duplicated, and difficult to evolve.

This system exists to prevent that.

Its purpose is to create a coherent framework where every long-lived work artifact has an intentional place, every project can build upon accumulated experience, and technical context continues to become more valuable instead of more difficult to manage.

The system is not the person.

Greg remains Greg.

Chat knows Greg. Groot knows Greg's work. Project agents know their project.

The system is a tool for work memory, organization, reflection, and action.

Normal ChatGPT may use broad personal context to help Greg think and make decisions. Groot and project agents should receive only work-related or project-relevant context.

The goal is not organization for its own sake.

The goal is reducing friction.

Every project should be easier to start than the previous one.

Every engineering decision should become easier to repeat.

Every lesson should only need to be learned once.

---

# Problem Statement

Modern technical work produces far more than source code.

Projects generate:

- architecture
- requirements
- experiments
- prompts
- research
- documentation
- standards
- reusable components
- career material
- operational knowledge
- work administration
- decision tradeoffs
- research notes
- writing drafts
- long-running technical intentions

Most of these artifacts outlive the moment that created them.

Without a deliberate system, valuable information slowly becomes:

- duplicated
- forgotten
- inconsistent
- difficult to locate
- impossible to reuse confidently

Over time this increases cognitive load and slows future work.

This framework treats long-term work knowledge, memory, and decision context as a systems problem instead of a storage problem.

---

# Objectives

## Preserve Knowledge

Capture durable information once.

Allow it to evolve rather than be recreated.

Preserve technical knowledge and work context that may influence future engineering, writing, career, or project decisions.

---

## Reduce Friction

Make the next project easier than the last.

Reduce repeated decisions.

Reduce duplicated effort.

Reduce unnecessary searching.

Reduce the cognitive cost of reconstructing important work context from memory.

---

## Encourage Reuse

Reusable work should remain reusable.

Templates.

Standards.

Patterns.

Prompts.

Architecture.

Lessons learned.

Decision criteria.

Technical preferences.

Known project constraints.

---

## Separate Stable Knowledge from Project Work

Projects are temporary.

Knowledge is cumulative.

This framework distinguishes between the two.

This applies to work-adjacent projects as well: job searches, research, writing, portfolio work, technical evaluations, and work administration may each have project-like activity without becoming permanent organizing principles themselves.

The framework owns the durable context.

Individual projects own the temporary work.

Projects own implementation.

The framework owns long-lived guidance.

---

## Support AI Collaboration

AI becomes significantly more effective when stable context exists.

The framework provides persistent context that should not need to be recreated for every conversation.

This includes context about engineering preferences, standards, constraints, project history, and career goals that affect what good advice or good implementation actually means.

---

## Remain Technology Independent

The system should survive changes in:

- programming languages
- editors
- AI systems
- operating systems
- repositories
- tooling

Technology changes.

Good organization should not.

---

# Design Principles

## Knowledge has one canonical home.

Avoid multiple authoritative copies.

---

## Projects remain independent.

A project repository should always be portable.

No repository should depend upon this system in order to build, test, review, or submit.

---

## Evolution over perfection.

The system should improve continuously.

It does not need to be perfect before it becomes useful.

---

## Project residue should be processed.

At the end of a project, leftover notes, prompts, decisions, discoveries, and unresolved ideas should be reviewed before they are forgotten.

Some project notes are temporary and can remain with the project.

Some contain durable knowledge that belongs in the broader system.

Some reveal a reusable pattern, preference, warning, template, or open question.

The practice is not to preserve everything.

The practice is to run the last project notes through the system and see what sticks.

---

## Organization follows purpose.

Directories exist to support retrieval.

Standards exist to reduce decisions.

Templates exist to eliminate repetition.

Nothing should exist without providing measurable value.

---

## Simplicity scales.

If the correct location for new information is not obvious, the architecture should be reconsidered.

---

## Active context stays lean.

Frequently used and active projects should automatically load only the context that is routinely useful.

- Preserve heavyweight source documents and images in durable storage without making them default context.
- Create focused, structured Markdown summaries for routine retrieval.
- Keep references to the original sources so they can be consulted when verification or deeper analysis is needed.
- Prefer a short operational summary over an exhaustive replacement unless the detail is genuinely reusable.
- Remove stale attachments, instructions, and duplicated summaries gradually as the project is used.

The goal is not to discard information. The goal is to make switching topics inexpensive while keeping deeper evidence available on demand.

---

# Engineering Delivery Pipeline

This is a repeatable engineering pattern for projects where correctness, readability, and delivery judgment matter.

It is especially useful for take-home assignments, production-quality exercises, portfolio work, and focused implementation projects.

## Phase 1 - Correctness

- Freeze behavioral requirements.
- Build an independent reference implementation.
- Verify against deterministic fixtures.
- Create regression corpus before optimizing.

Correctness precedes performance.

---

## Phase 2 - Engineering

- Write the simplest architecture that satisfies the requirements.
- Optimize only measured bottlenecks.
- Prefer explicit names over clever abstractions.
- Localize complexity.

Readable code beats impressive code.

---

## Phase 3 - Validation

Every change should answer:

- Does it change behavior?
- If yes, prove correctness.
- If no, prove readability.

Behavioral changes require validation.

Readability changes require explanation.

---

## Phase 4 - Documentation

Each document should have exactly one audience.

```text
README
    What is this?

FINAL_SUBMISSION
    Did I complete the assignment?

REQUIREMENTS
    What behavior is implemented?

TESTING
    Why should you trust it?
```

Avoid duplicate explanations.

---

## Phase 5 - Polish

Only improve things that reduce reader effort.

Examples:

- Better names
- Better comments
- Better organization
- Named constants
- Remove ambiguity

Do not chase style.

---

## Phase 6 - Release

When the project is correct:

- Clean build
- Clean repository
- Fresh clone verification
- Package
- Submit

Then stop.

Do not keep polishing after release quality has been achieved.

---

# Language Guidance Architecture

Canonical language-wide engineering guidance lives in:

```text
engineering/languages/
```

Each language has a base guide plus version-specific delta files:

```text
engineering/languages/<language>/base.md
engineering/languages/<language>/versions/<version>.md
```

The base guide contains durable guidance that applies across supported versions of that language.

Version files contain only meaningful differences from the base guide. They must not duplicate the full guide.

Project repositories may copy applicable guidance into their own `AGENTS.md` files, but those copies are portable snapshots, not live dependencies on Groot.

Copied project guidance should record:

- Groot source paths
- snapshot date
- Groot revision or release identifier when available

This makes stale-snapshot detection possible later while preserving project independence.

Standalone projects must not use symlinks to Groot or require Groot paths during build, test, review, packaging, or submission.

`AGENTS.md` inheritance follows directory scope. An `AGENTS.md` applies to its directory tree, and deeper `AGENTS.md` files may add to or override instructions for their own subtrees. Markdown links do not import instructions; linked files are only navigational unless their relevant text is copied into the active `AGENTS.md`.

The detailed rules and examples live in `engineering/languages/README.md`.

---

## Delivery Philosophy

Reduce ambiguity before reducing latency.

This principle is not universal, but it aligns with the kind of engineering this system should encourage: behavior should be provably correct and understandable before effort shifts toward speed or cleverness.

---

# Scope

This system is expected to organize long-lived information related to:

- Engineering
- Software development
- AI collaboration
- Research related to work
- Writing related to work
- Career development
- Work
- Reusable templates
- Work decision history
- Technical reference material
- Work administration, including personal finances or taxes only when relevant to work administration

The exact structure will evolve as the system matures.

Personal files such as `Nata.md` may be retained as cold archival records outside Groot's active architecture. Groot should not organize, automatically retrieve, expand, or build a personal knowledge system around them.

---

# Deliverables

The completed system should include:

- Canonical directory architecture
- Engineering philosophy
- Language guides
- Workflow documentation
- Project templates
- AI prompt library
- Reusable checklists
- Documentation standards
- Knowledge classification rules
- Repository interaction model
- Work context model
- Technical project model
- Decision records for engineering, writing, research, career, and work administration
- Retention rules for sensitive work information
- AI collaboration rules for work-related context

---

# Success Criteria

The system succeeds when:

- New projects begin with minimal setup.
- Existing work is easy to locate.
- Valuable knowledge is rarely duplicated.
- AI can leverage stable context instead of rebuilding it.
- Projects remain clean and portable.
- The system becomes easier to maintain as it grows rather than harder.
- Work decisions can draw on remembered context instead of vague recollection.
- Project agents receive only the context their project needs.
- Sensitive work information is retained deliberately, not accidentally.

---

# Current Phase

Architecture.

The immediate objective is not choosing folder names.

The objective is designing a framework capable of organizing years of accumulated work without becoming another project that eventually requires replacing.
