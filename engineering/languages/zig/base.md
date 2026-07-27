# Zig Base Guide

This file is the canonical home for Zig engineering guidance that applies across supported Zig versions.

Keep this guide limited to durable Zig-wide practices. Do not add project-specific rules, performance profiles, or version-specific deltas here.

## Purpose

- Define stable Zig practices for future standalone projects.
- Make future Zig project guidance portable into standalone repositories.
- Keep language-wide philosophy separate from project-specific capacities, topology, persistence rules, exceptions, and version-specific changes.

## Operating Philosophy

Zig projects should be designed as self-contained, bounded systems.

The default expectation is that, once initialized, software can continue operating using local compute, preallocated memory, and explicitly managed local state without requiring external services for correctness.

External services may improve coordination, observability, distribution, or administration, but they should not become accidental dependencies of the core data plane.

Prefer:

- zero steady-state dynamic allocation
- fixed and auditable resource bounds
- minimal runtime dependencies
- deterministic state transitions
- local persistence and replay
- explicit recovery procedures
- assertions at state boundaries
- bounded loops and queues
- no runtime recursion
- control planes that can fail without corrupting the data plane

The core system should own the resources and state required to remain correct.

Projects may override these defaults when a documented use case justifies it.

## Ownership and Lifetimes

- Make ownership visible at API boundaries.
- Prefer passing allocators, buffers, handles, and context explicitly over hiding them in global state.
- Document whether a function borrows, stores, mutates, or takes ownership of caller-provided memory.
- Keep returned slices and pointers tied to a clear owner and lifetime.
- Avoid accidental copies of large structs; pass by pointer when mutation, identity, or cost matters.

## Allocators

Allocation is an architectural decision, never an incidental implementation detail.

Zig code should be designed for zero dynamic allocation during steady-state runtime operation.

Memory must normally be:

- statically sized
- caller-provided
- arena-backed and allocated during initialization
- drawn from fixed-capacity pools established before the data plane begins

Heap allocation inside hot paths, event loops, request processing, matching, routing, parsing, or other steady-state operations is prohibited by default.

Allocators may be used during initialization, control-plane work, tooling, experiments, tests, and explicitly approved project exceptions.

Projects may override this rule when the use case justifies allocation, but the override must be intentional and documented.

When allocation is allowed:

- APIs that may allocate should make the allocator visible.
- Prefer initialization APIs that receive required allocators or owned backing storage explicitly.
- Pair allocation and cleanup paths in the same abstraction when practical.
- Tests should exercise `deinit` and failure paths for owned resources.

## Memory Policy Hierarchy

- Zig base: TigerStyle-inspired by default, with no steady-state dynamic allocation.
- Project policy: may tighten the rule to no allocation anywhere after initialization and define concrete capacities, limits, topology, persistence, and recovery procedures.
- Project override: may relax individual constraints deliberately for a documented reason.
- Experiment: may temporarily override the policy to measure behavior or compare designs.

## Error Handling

- Handle error unions explicitly at the boundary where recovery, cleanup, propagation, or failure reporting is decided.
- Use `try` when propagation is the intended behavior.
- Use `catch` when adding context, choosing fallback behavior, or translating errors.
- Do not discard errors merely to silence the compiler. If an error is intentionally impossible, make that invariant obvious and keep it local.
- Keep error sets meaningful for public APIs; avoid exposing broad or accidental implementation details when a smaller error surface is clear.

## Values and Mutation

- Use `const` unless mutation is required.
- Keep mutable state local and narrow in scope.
- Prefer explicit names for domain values whose units or roles can be confused.
- Use `undefined` only when immediate, total initialization is obvious or mechanically enforced before read.
- Prefer struct literals and named fields where they make initialization auditable.

## Comptime and Generic APIs

- Use `comptime T: type` when the API is fundamentally type-parameterized and the explicit type parameter improves readability.
- Use `anytype` when structural generic behavior is clearer and the accepted surface is intentionally duck-typed.
- Do not treat `anytype` as inherently obsolete or unsafe. Choose the generic form that makes the contract clearest.
- Keep compile-time reflection code small and well tested.

## Layout and Alignment

- Treat size, field layout, and alignment as separate concerns.
- Verify layout with `@sizeOf`, `@alignOf`, and target-specific tests when layout matters.
- Do not assume cache-line alignment from object size alone.
- Avoid documenting uncompiled layout calculations as portable facts.

## Testing

- Put behavior tests close to the implementation when they describe local invariants.
- Add fixture or integration tests when behavior spans modules, persisted formats, or public APIs.
- Cover cleanup paths and allocator-backed code.
- Keep performance benchmarks separate from correctness claims.

## Build Conventions

- Keep `build.zig` simple until the project has concrete needs for extra build steps.
- Prefer standard `zig build` and `zig build test` entry points.
- Record exact compiler versions in projects that pin a development compiler.
