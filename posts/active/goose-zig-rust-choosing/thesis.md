# Thesis

## Working title

Goose, Zig, or Rust: Choosing a Systems Language When One of the Options Is
Weeks Old

## Question

How should a team choose between Rust, Zig, and the new Goose language for a
new project, when the options differ this much in maturity and in how they
approach memory safety?

## Thesis

For a team choosing a systems language today, the decision turns less on peak
performance or the memory-safety mechanism than on maturity risk and
ecosystem, which makes Rust the default for production work where safety
matters, Zig a fit for teams that want explicit control and C interop, and
Goose not yet a production candidate but worth tracking for what it shows
about safety without lifetime annotations.

## Why now

Goose appeared recently with strong benchmark claims against safe Rust, and
its repository was produced almost entirely with AI from a human language
design. Teams will be asked whether to look at it before any independent
evidence exists.

## Argument 1

The three languages make different safety trade-offs, and the differences
change what a team is signing up for: Rust enforces memory safety at compile
time through ownership and lifetimes; Zig prioritizes explicitness, with
allocators passed by the programmer; Goose infers reference roots and uses
compiler-managed data stacks, with no heap and no lifetime syntax. [Each
statement about Rust and Zig must be sourced; Goose's are from its own
documentation.]

## Argument 2

Project risk is dominated by maturity, ecosystem, and bus-factor rather than
language features. Goose's own documentation lists limits that rule out many
real workloads today (no escaping closures, no dynamic dispatch beyond ADT
tags, whole-program compilation only, limited OS and library access).

## Argument 3

Self-reported benchmarks should not drive the choice. Goose's figures come
from 16 benchmarks run by the author, the page's intro and table numbers
differ without explanation, and commenters dispute both the tuning and the
"no heap" framing. A team should define what independent evidence would move
Goose from "watch" to "pilot" instead of taking the numbers as given.

## Counterargument

Dismissing a young language on maturity alone is how teams miss real shifts.
If Goose's model delivers safety without lifetime annotations, it removes
what many consider Rust's largest adoption cost, and the performance claims,
if they hold, matter. Zig was also once new.

## Response

The thesis is about committing production work, not about attention. It
recommends a cheap, bounded pilot path for Goose and names the evidence that
would justify moving it up, rather than telling readers to ignore it.
[AUTHOR OPINION: how firm to be that Goose is "not yet" versus "watch
closely".]

## Novel contribution

Most comparisons rank languages on features or benchmarks. This one gives a
decision framework that treats maturity and claim-quality as first-class
criteria, applied to a language old enough to be interesting and new enough
that no independent track record exists.

## Evidence required

- Rust: official documentation on ownership, borrowing, and lifetimes.
- Zig: official documentation on allocators and safety checks, and its
  current release/stability status (pre-1.0 status to be verified).
- Goose: primary documentation (already read), the specification, and any
  independent benchmark or review that is not the author's.
- Any independent assessment of the "no heap" and safety claims.
- Evidence on ecosystem and hiring for Rust and Zig (surveys, package counts).

## Author input required

- [AUTHOR EXPERIENCE] real experience shipping with Rust and/or Zig, and a
  stack-selection decision and what followed from it.
- [AUTHOR OPINION] where you land on Goose today: skip, watch, or pilot.
- [AUTHOR EXAMPLE] a project type you would pick each language for.
