# AGENTS.md

<!--
Groot guidance snapshot:
- Source: engineering/languages/zig/base.md
- Source: engineering/languages/zig/versions/0.14.md
- Snapshot date: 2026-07-26
- Groot revision: unavailable
-->

These instructions apply to this repository tree.

This file is a portable project-local snapshot. The repository must not require Groot, symlinks to Groot, or external language-guidance files to build, test, review, package, or submit.

## AGENTS.md Scope

- This `AGENTS.md` applies to files in this directory and its subdirectories.
- A deeper `AGENTS.md` may add to or override these instructions for its own subtree.
- Instructions from unrelated directories do not apply.
- Markdown links do not import instructions. Linked guidance is inactive unless its relevant text is copied here.

## Zig Guidance Snapshot

The canonical Zig guide has not been written yet.

For now, use this section only as a placeholder for copied Zig-wide guidance once Groot establishes it. Do not infer extra Zig standards from the existence of the placeholder.

## Zig 0.14 Delta Snapshot

No Zig 0.14-specific guidance has been established yet.

## Matching Engine Project Guidance

- Correctness comes before latency optimization.
- Keep matching behavior deterministic and covered by fixtures.
- Preserve a simple reference path for validating optimized code.
- Treat order book state transitions as behavioral changes that require tests.
- Prefer explicit names for price, quantity, side, order id, and time-priority concepts.
- Document benchmark results separately from correctness claims.

## Portability

- Do not add symlinks to Groot.
- Do not require Groot paths in build scripts, tests, editor settings, or CI.
- If language guidance is refreshed from Groot, update the snapshot metadata above.
