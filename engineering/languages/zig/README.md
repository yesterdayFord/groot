# Zig Guidance

This directory is the canonical home for reusable Zig guidance in Groot.

## Structure

```text
engineering/languages/zig/
    README.md
        This map.
    base.md
        Durable Zig-wide guidance.
    profiles/
        tigerstyle.md
            Strict deterministic-systems profile.
    versions/
        0.13.md
        0.14.md
        0.17.md
            Version-specific deltas only.
```

## Layering

- Put TigerStyle-inspired default Zig philosophy and stable practices in `base.md`.
- Put stricter or specialized engineering profiles in `profiles/`.
- Put only verified version-specific behavior in `versions/<version>.md`.
- Put concrete capacities, limits, topology, persistence rules, and exceptions in the project repository.

Where a standalone project copies guidance from Groot, record source paths and snapshot dates in that project.
