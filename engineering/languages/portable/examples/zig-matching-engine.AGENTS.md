# AGENTS.md

<!--
Groot guidance snapshot:
- Source: engineering/languages/zig/base.md
- Source: engineering/languages/zig/profiles/tigerstyle.md
- Source: engineering/languages/zig/versions/0.17.md
- Snapshot date: 2026-07-27
- Groot revision: unavailable
-->

These instructions apply to this repository tree.

This file is a portable project-local snapshot. The repository must not require Groot, symlinks to Groot, or external language-guidance files to build, test, review, package, or submit.

## AGENTS.md Scope

- This `AGENTS.md` applies to files in this directory and its subdirectories.
- A deeper `AGENTS.md` may add to or override these instructions for its own subtree.
- Instructions from unrelated directories do not apply.
- Markdown links do not import instructions. Linked guidance is inactive unless its relevant text is copied here.

## Engineering Profile

This project applies:

- `engineering/languages/zig/base.md`
- `engineering/languages/zig/profiles/tigerstyle.md`
- `engineering/languages/zig/versions/0.17.md`

Compiler target:

- Zig development version: record exact `zig version` output in the project copy.
- Do not describe the target as released Zig 0.17.0 unless that release exists.

Where guidance conflicts:

1. Verified compiler behavior
2. Project requirements
3. TigerStyle profile
4. Zig base guidance
5. General repository guidance

## Zig Guidance Snapshot

- Design the core system as self-contained and bounded.
- Keep the resources and state required for correctness local to the core data plane.
- Avoid accidental dependence on external services for correctness.
- Make ownership and lifetimes visible at API boundaries.
- Pass allocators, buffers, handles, and context explicitly.
- Design for zero dynamic allocation during steady-state runtime operation.
- Treat allocation as an architectural decision, never an incidental implementation detail.
- Prefer fixed resource bounds, deterministic state transitions, local replay, assertions at state boundaries, bounded loops and queues, and no runtime recursion.
- Use `const` unless mutation is required.
- Handle error unions intentionally with propagation, recovery, translation, or documented invariants.
- Verify layout and alignment with target-aware tests when they matter.

## TigerStyle Profile Snapshot

- Tighten the base memory policy toward no allocation anywhere after initialization.
- Define concrete capacities, limits, topology, persistence, recovery, and exceptions in the project repository.
- Give queues, buffers, pools, batches, and in-flight work explicit bounds.
- Avoid runtime recursion.
- Use explicit loop and batch bounds for external input or queued work.
- Assert important preconditions and postconditions around state transitions.
- Prefer deterministic replay, simulation, fuzzing, and fault injection for critical state behavior.

## Zig 0.17 Delta Snapshot

No durable Zig 0.17-specific guidance has been established yet.

When using a Zig 0.17 development build, record the exact compiler revision in the project.

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
