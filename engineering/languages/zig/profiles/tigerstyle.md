# TigerStyle Profile

This profile captures a stricter deterministic-systems engineering style inspired by TigerBeetle's TigerStyle and architecture.

Groot's Zig base guide is already TigerStyle-inspired by default. Apply this profile when a project wants to tighten that default into a more explicit deterministic-systems discipline because its correctness, latency, durability, or operational requirements justify the constraints.

## Use When

- The system must be highly deterministic.
- Runtime resource growth would create correctness, latency, or overload risks.
- The project benefits from strict upper bounds, replayability, simulation, and aggressive invariant checking.
- The team is willing to trade generality and convenience for predictability.
- The project is ready to document concrete capacities, limits, topology, persistence, recovery, and exceptions in its own repository.

## Memory and Resources

- Tighten the base memory policy toward no allocation anywhere after initialization.
- Give queues, buffers, pools, and in-flight work explicit bounds.
- Size bounded resources from documented limits or configuration.
- Treat overload behavior as part of the design, not an afterthought.
- Avoid hidden unbounded allocation in hot paths.

## Control Flow

- Avoid runtime recursion.
- Give loops and batches explicit bounds when they process external input or queued work.
- Keep event loops deterministic when replay or simulation depends on ordering.
- Separate data-plane work from control-plane work when that clarifies latency and failure behavior.
- Ensure control-plane failure cannot corrupt the data plane.

## Invariants

- Assert preconditions and postconditions around important state transitions.
- Prefer deterministic failure over silent corruption.
- Keep invariants close to the code that owns the state.
- Use assertions to clarify impossible states, not to paper over uncertain behavior.

## Batching and Scheduling

- Batch work deliberately when it improves throughput, amortizes fixed costs, or simplifies ordering.
- Make batch limits explicit.
- Preserve deterministic ordering across equivalent inputs.
- Document fairness and backpressure decisions.

## Layout and Alignment

- Verify size, layout, and alignment for the actual target when they matter.
- Do not infer cache-line alignment from struct size.
- Use target-aware tests or comptime assertions for layout-sensitive structures.
- Keep cache-line and ABI claims tied to measured or compiled facts.

## Validation

- Prefer deterministic replay for state-machine behavior.
- Use fuzzing, simulation, and fault injection where state transitions, storage, IO, or recovery are critical.
- Keep a simple reference path when optimized paths become complex.
- Treat benchmark data as evidence about performance, not correctness.
