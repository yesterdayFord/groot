# Language Guidance

This directory is the canonical home for language-wide engineering guidance in Groot.

Language guidance belongs here when it is durable across projects and should influence future repositories. Project repositories may copy a snapshot of the relevant guidance, but copied guidance is not authoritative.

## Structure

```text
engineering/languages/
    README.md
        Governing rules for language guidance.

    python/
        base.md
            Python guidance that applies across supported Python versions.
        versions/
            3.11.md
            3.12.md
            3.13.md
                Version-specific deltas only.

    zig/
        README.md
            Zig guidance map.
        base.md
            Zig guidance that applies across supported Zig versions.
        profiles/
            tigerstyle.md
                Strict deterministic-systems engineering profile.
        versions/
            0.13.md
            0.14.md
            0.17.md
                Version-specific deltas only.

    portable/
        project-guidance-snapshots.md
            Rules for copying guidance into standalone repositories.
        examples/
            zig-matching-engine.AGENTS.md
                Example project-level AGENTS.md.
```

## Governing Rules

- `engineering/languages/<language>/base.md` is the language's base guide.
- `engineering/languages/<language>/versions/<version>.md` contains only meaningful differences from the base guide.
- Version files must not duplicate the full base guide.
- If guidance applies across every supported version, it belongs in `base.md`.
- If guidance applies only to one language version, it belongs in that version delta.
- If guidance is a stricter or specialized engineering profile rather than language-wide guidance, put it under `engineering/languages/<language>/profiles/`.
- If guidance applies only to one project, it belongs in that project's repository, not here.
- If project guidance becomes reusable, process it back into Groot deliberately instead of treating the project copy as canonical.

## Single-Language Projects

For a project using one language:

1. Copy the language base guide.
2. Copy any explicitly applicable profile.
3. Copy the applicable version delta, when the project targets a specific version.
4. Merge or reference those copied sections inside the project's own `AGENTS.md`.
5. Add project-specific guidance after the copied language guidance.
6. Record the Groot source paths and snapshot date in the copied file.

The resulting project repository must remain standalone. It must not require Groot to build, test, review, or submit.

## Mixed-Language Projects

For a project using multiple languages:

1. Copy the base guide for each major language used by the project.
2. Copy only the applicable version deltas.
3. Place language-specific instructions under clear headings in the project's `AGENTS.md`, such as `Python Guidance` and `Zig Guidance`.
4. Add cross-language project rules separately, such as API boundaries, generated-code rules, or build orchestration.
5. Resolve conflicts locally in the project copy. The project copy should say which rule wins and why.

Do not make one language's guide implicitly control another language's files.

## AGENTS.md Scope and Inheritance

`AGENTS.md` instructions are inherited by directory scope.

- An `AGENTS.md` applies to files in its directory tree.
- A deeper `AGENTS.md` may add to or override instructions for its subtree.
- Instructions outside the current directory ancestry do not apply.
- Markdown links are ordinary links. They do not import, include, inherit, or activate instructions.
- Linking from one `AGENTS.md` to another is useful for human navigation only.
- To make instructions portable and active, copy the relevant text into the applicable `AGENTS.md`.

## No Symlinks or Groot Dependency

Standalone project repositories must not depend on Groot.

- Do not symlink project guidance back to Groot.
- Do not require Groot paths during build, test, lint, review, packaging, or submission.
- Do not assume reviewers, CI, editors, or AI tools can access Groot.
- Copied guidance is a snapshot, not a live dependency.

## Snapshot Metadata

Copied project guidance should record its Groot source and snapshot date.

This allows later stale-snapshot detection without making the project depend on Groot.

Recommended metadata:

```markdown
<!--
Groot guidance snapshot:
- Source: engineering/languages/python/base.md
- Source: engineering/languages/python/versions/3.13.md
- Snapshot date: YYYY-MM-DD
- Groot revision: optional commit hash or archive version when available
-->
```

If Groot is not a Git repository, use the snapshot date and exact source paths. When Groot later gains revisions or releases, include that identifier too.
