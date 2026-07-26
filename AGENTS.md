# AGENTS.md

These instructions apply to the entire Groot repository.

## Scope

Groot is a long-lived personal knowledge system. Keep changes focused on durable knowledge architecture, reusable guidance, templates, and decision records.

Do not expand the system into unrelated implementation work unless explicitly requested.

## Documentation

- Prefer clear Markdown documents with one primary audience.
- Keep canonical knowledge in one authoritative location.
- Avoid duplicating full guides across files.
- Use links for navigation, not instruction inheritance.

## Project Independence

When documenting reusable guidance for external projects:

- Projects may copy guidance from Groot.
- Copied guidance is a snapshot, not a live dependency.
- Standalone projects must not require symlinks or runtime access to Groot.
- Include source paths and snapshot dates when guidance is copied.

## AGENTS.md Inheritance

- This file applies to this directory tree.
- A deeper `AGENTS.md` may add or override instructions for its subtree.
- Markdown links do not import or activate instructions.

