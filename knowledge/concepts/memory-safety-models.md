# Memory-safety models: Rust, Zig, Goose

- **Rust**: compile-time ownership and borrowing; lifetimes are the scopes
  references are valid for, mostly inferred, annotated only where ambiguous.
  Checks happen at compile time with no GC. (Rust Book, ch. 4 and 10.3)
- **Zig**: explicit allocators, "no hidden memory allocations", build-mode
  dependent runtime safety checks (panics in safety modes, undefined
  behavior with checks off). Does not present a general memory-safety
  guarantee (inferred from its overview). Pre-1.0: stable 0.17.0 on
  2026-10-01. (ziglang.org)
- **Goose**: no heap or GC; values on compiler-managed data stacks freed at
  scope exit; compiler infers reference "roots" and rejects references that
  could outlive their owner; no `unsafe`, no lifetime syntax. Self-reported
  benchmarks only, unverified. Restrictive (no escaping closures, no dynamic
  dispatch beyond ADT tags, whole-program compile). (aardappel.github.io/goose)

Adoption (Stack Overflow 2025, extensive use in past year): Rust 14.8%, Zig
2.1%.

Sources: `posts/active/goose-zig-rust-choosing/sources/sources.yaml` (S1-S7).
