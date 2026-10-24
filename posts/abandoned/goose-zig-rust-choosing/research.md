# Research Dossier

## Article

Goose, Zig, or Rust: Choosing a Systems Language When One of the Options Is
Weeks Old

## Thesis

For a team choosing a systems language today, the decision turns less on peak
performance or the memory-safety mechanism than on maturity risk and
ecosystem, which makes Rust the default for production work where safety
matters, Zig a fit for teams that want explicit control and C interop, and
Goose not yet a production candidate but worth tracking for what it shows
about safety without lifetime annotations.

---

# Claim 1

Rust enforces memory safety at compile time through ownership and lifetimes,
with no GC and no runtime cost for the checks. (factual)

## Supporting evidence

The Rust Book states three ownership rules: each value has an owner, only
one owner at a time, and the value is dropped when the owner goes out of
scope. Violations mean "the program won't compile" [S3]. Lifetimes are "the
scope for which that reference is valid"; the borrow checker compares scopes
to find dangling references, and "all of this analysis happens at compile
time" [S4]. The book states that none of ownership's features slow the
program at runtime [S3].

## Contrary evidence

None on the mechanism. Note a nuance that affects the thesis (see Claim 5):
lifetimes are mostly inferred, and annotations are needed only where
relationships between references are ambiguous [S4].

## Assessment

Well supported by the primary documentation. "No runtime cost" is the
book's own claim about its features; it is not an independent measurement.

## Confidence

High

---

# Claim 2

Zig does not guarantee memory safety; it gives explicit control (allocators,
no hidden allocations) plus build-mode-dependent runtime safety checks.
(factual)

## Supporting evidence

Zig's overview: "Zig programmers must manage their own memory," functions
that allocate accept an allocator parameter, and there are "no hidden memory
allocations" [S5]. Safety-checked build modes turn errors such as integer
overflow into panics; with safety disabled the same operations are undefined
behavior [S5]. The page does not claim memory safety in general; its
protections depend on build mode [S5]. Pointers are non-nullable by default;
`@cImport` imports C headers without hand-written bindings [S5].

## Contrary evidence

None.

## Assessment

Supported. The "does not claim memory safety" reading is my inference from
what the page does and does not say, not a quoted statement; phrase it that
way in the article.

## Confidence

High (mechanism), Medium (the "no safety guarantee" framing)

---

# Claim 3

Zig is pre-1.0 (the current stable release is 0.17.0). (factual)

## Supporting evidence

The download page lists 0.17.0 as the latest stable release, dated
2026-10-01, with a 0.18.0-dev build dated 2026-10-23 [S6]. The page mentions
no 1.0 milestone or stability guarantee [S6].

## Contrary evidence

None.

## Assessment

The version number establishes pre-1.0. The absence of a stability promise
is "not stated on the page", not proof that none exists elsewhere; check the
Zig language reference or release notes before asserting "no compatibility
guarantee".

## Confidence

High (pre-1.0), Low (anything about compatibility policy)

---

# Claim 4

Goose is a very new, experimental language whose safety and speed claims are
self-reported and not independently verified. (factual)

## Supporting evidence

Per the project page [S1]: memory-safe, no heap, GC, refcounting, or
lifetime annotations; dynamic values live on compiler-managed data stacks;
the compiler infers each reference's "root" and rejects references that could
outlive their owner; no `unsafe` keyword. It compiles whole programs to one
C file; Apache-2.0. Stated limitations: no escaping closures, no function
pointers or dynamic dispatch beyond ADT tags, whole-program compilation
only, at most one resizable value per struct, and more [S1]. Benchmarks:
16, run by the author. The intro says 3.3x idiomatic C++, 1.16x hand-
optimized C++, 1.12x best safe Rust; the table says 3.51x/3.54x, 1.24x/1.26x,
1.13x/1.19x (MSVC/clang), unexplained [S1]. Timing is whole-process
wall-clock including teardown [S1]. The author says the repository was
produced "almost entirely with AI, from a human language design" [S1].
A search found no independent review or safety audit; one directory listing
reports repo creation in August 2026, last push 2026-10-10, no releases [S8].
HN commenters called the benchmark claim implausibly precise and
possibly tuned, disputed the "no heap" framing, and raised a concern about
reuse of freed slots leaking data between users [S2].

## Contrary evidence

The author states results include losses and links the full data [S1]. No
independent source contradicts the design claims either; they are simply
unverified.

## Assessment

Everything about Goose rests on the author's own page plus community
reaction. Treat performance and safety as claims, not findings. The
unexplained intro/table discrepancy is itself worth noting in the article.

## Confidence

High (what the project claims), Low (that the claims are true)

---

# Claim 5

Goose's removal of lifetime annotations is a real advantage over Rust.
(interpretive; tests the thesis's counterargument)

## Supporting evidence

Goose has no lifetime syntax and infers reference roots [S1].

## Contrary evidence

Rust lifetimes are mostly inferred already; annotations are written only
where reference relationships are ambiguous [S4]. Goose also gives up
capabilities to get there: no escaping closures, no dynamic dispatch beyond
ADT tags, whole-program compilation [S1]. Whether Goose's restrictions cost
more than Rust's annotations is untested.

## Assessment

The thesis's counterargument is too strong as written ("removes Rust's
largest adoption cost"). Annotation burden is real but narrower than the
phrase suggests, and Goose trades it for expressiveness limits. Revise the
counterargument's framing rather than the thesis.

## Confidence

Medium

---

# Claim 6

Rust has far wider adoption than Zig. (factual; supports "Rust is the default")

## Supporting evidence

Stack Overflow 2025 Developer Survey, "extensive development work in the
past year": Rust 14.8% and Zig 2.1% of all respondents; Rust 14.5% and Zig
1.9% of professional developers [S7].

## Contrary evidence

Usage share is not suitability. The search summary also reported admiration
of 72% for Rust and 64% for Zig, which suggests Zig has enthusiasm without
scale; I could not confirm those two figures from the survey page itself.

## Assessment

Supports "wider adoption", not "default for production where safety
matters". The latter is an OPINION and should be labeled as such.

## Confidence

High (usage figures), Low (admiration figures, unverified)

---

# Useful examples

- The `longest<'a>` example in the Rust Book shows what an annotation
  actually does: it describes a relationship, it does not extend lifetimes [S4].
- Goose's intro-versus-table benchmark discrepancy is a concrete example of
  why to read claims against the data.

# Useful quotes

- "None of the features of ownership will slow down your program while it's
  running." (Rust Book) [S3]
- "produced almost entirely with AI, from a human language design" (Goose
  author) [S1]

# Open questions

- No independent verification of Goose's benchmarks, memory-safety claims,
  or the reported leak concern.
- Zig's compatibility and stability policy beyond version number.
- Hiring and package-ecosystem data for Rust and Zig beyond survey usage.
- A fork named "gust" (appdoze/gust) and another mirror appeared in search
  results; not fetched, so no claim is made about them. They may indicate
  early community interest.
- Whether Goose's AI-built implementation is a materially different risk
  from a human-built one is argued in the HN thread but has no evidence
  either way.

# Claims requiring author judgment

- Verdict on Goose: skip, watch, or pilot (thesis Response).
- Whether "Rust is the default" is a position you will own, given it is an
  opinion supported only by adoption share.
- Whether to engage the AI-authorship question at all, or keep the article on
  engineering criteria.
- Real-world Rust/Zig experience for the examples.
