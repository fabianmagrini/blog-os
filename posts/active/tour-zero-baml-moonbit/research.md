# Research Dossier

> **Revision note (2026-11-07, second):** the article is now an explainer and
> tour of Zero, BAML and MoonBit, and the thesis is awaiting approval. Claims
> 1-6 are the core case-study evidence. Claims 7-9 (language effects, training
> data, TypeScript tooling) are background for the closing section. New
> research needed: the MoonBit language itself, and real code and workflow
> examples for all three (see Open questions).


> **Revision note (2026-11-07):** the thesis was broadened to the general
> question of languages for coding agents and is awaiting re-approval. The
> claims below remain valid as evidence about three case studies and the
> surrounding tooling. New evidence needed for the broader frame is listed
> under "Open questions" (language-level effects on agent performance;
> training-data and ecosystem effects).


## Article

Three Languages Built for Coding Agents: A Tour of Zero, BAML and MoonBit

## Thesis

The next gain for coding agents is likely to come from a structured, queryable
and checked interface to the program rather than from new syntax, and because
much of that interface can be built over existing languages, Zero, BAML and
MoonBit are best read as three experiments in where to put that structure
(the representation, the language semantics, or the tooling) rather than as
replacements for mainstream languages.

---

# Claim 1

Zero makes a semantic graph the authoritative program representation, with
text as a reviewable projection, and ships checked structural patches.
(factual)

## Supporting evidence

The docs state "the graph is the program database"; `.0` text files are
review views that `zero import` can rebuild from [S1]. The README's "What
Exists Today" lists `zero.graph` as compiler input, `.0` projections, `zero
patch`, `zero query/inspect/check/test/run`, and `zero import/export` [S2].
Patches name a node, an expected value and a new value, and carry an
`--expect-graph-hash` stale-state guard; shape, edge, type-fact and hash
checks run before the package becomes compiler input [S1].

## Contrary evidence

The README labels the project a "Vercel Labs Experiment" and warns that it
is "experimental", with breaking changes and security issues expected [S2].
No version number is shown [S2].

## Assessment

Implemented as described, but experimental. Apache-2.0, owned by Vercel Labs
(5.4k stars, 1,188 commits at time of reading); individual maintainers are
not named on the page [S2].

## Confidence

High (design and existence), Low (production readiness)

---

# Claim 2

Zero's patch operations are "transactional" in the sense the brief assumes
(atomic, rollback-safe, safe under concurrent edits). (factual)

## Supporting evidence

The README says stale hashes, unexpected field values, invalid shapes and
type errors "fail before the store is written" [S2], which implies
validate-then-write.

## Contrary evidence

Neither source describes atomicity, rollback or concurrent-edit behavior,
and the docs do not use the word "transactional" [S1, S2]. A stale-hash
check detects a concurrent change; it does not by itself say what happens to
two agents editing at once.

Update 2026-11-07: the CLI docs also show `zero patch --check-only` and
`--dry-run --json` on a patch file, a `--expect-graph-hash` guard, and several
patch forms (`--op`, a patch file with an `expect graphHash` line,
`--replace-fn`, `--replace-in-fn`) [S22]. That adds a preview-before-apply
step; it still does not document atomicity, rollback or concurrent edits.

## Assessment

Not supported. The article may say Zero validates a patch before writing,
offers a dry run, and rejects stale state; it must not say transactional or
imply multi-agent safety without reading the implementation.

## Confidence

High (that it is unsupported by these sources), Low (about the actual behavior)

---

# Claim 3

BAML is moving from a DSL for typed model calls to a general programming
language for agents, and the new language is shipped. (factual)

## Supporting evidence

The main docs describe typed functions that call models, plus general
computation, errors and concurrency, run via CLI or generated SDKs
(TypeScript listed) [S3]. The canary README calls BAML "the programming
language for agents" with TypeScript-like syntax, Rust-like types, typed
errors, green threads, a built-in test/eval framework, an agent standard
library, and incremental adoption from TypeScript, Python, Go, C# and Java
[S4]. The repo has a `baml_language` directory [S5].

## Contrary evidence

The docs make no general-purpose claim and give no stability labels beyond
"Install Canary" [S3]. The README gives no stability caveats and states
features in the present tense; its compile-speed-versus-Go claim has no
benchmark [S4]. The repo page shows no releases and does not say whether
canary or `baml_language` is released [S5].

Update 2026-11-07: the developer docs do document the new language's
features (typed errors with `throws`/`catch`/`catch_all`, `spawn`/`await`
concurrency, interfaces, a TypeScript bridge that generates `baml_sdk/`, a
`baml test` command), but every guide says to install Canary [S23]. The CLI
and packages pages state: "No stable release has been published in this
catalog. Canary and nightly entries are labeled explicitly and are not stable
releases"; v0.25.2 is listed as canary, published Nov 6, 2026 [S24]. The
book is "being published chapter by chapter": classes/enums, testing, prompts
and evals chapters are not yet published [S24]. The older BAML (v0) README
says it is stable and used in production, and the relationship between the
two languages is not explained on any page read; blog titles mention an
unexplained "BAML v1" [S26].

## Assessment

The new language exists and is documented, but only in canary, with no stable
release. The "general-purpose language" direction is claimed in the README
and visible in the docs. Say "canary, documented, not stable". Apache-2.0;
BoundaryML (Seattle per README footer); 9.5k stars [S5].

## Confidence

High (what is claimed), Low (that it is implemented and stable)

---

# Claim 4

MoonBit's SeekMoon provides syntax-tree search and syntax-aware diff review
for agent-written code. (factual)

## Supporting evidence

The 2026-09-01 post describes syntax-tree search with placeholders (an
example found 43 matches in the `core` project), results added to agent
context, and Diff Review with line, token and syntax-tree views plus
go-to-definition and find-references. It states a task is complete only when
the developer understands and accepts the code [S6]. The post links to
`moonbitlang/openseek` as the place to explore and build it [S6].

## Contrary evidence

That repository's README describes a "DeepSeek-backed MoonBit coding agent"
with a headless CLI, TUI, MCP server, skills and a compiler-grounded review
engine, and never mentions SeekMoon, structural search or diff review. No
release or version is listed [S7].

## Assessment

Unresolved. The shipped features are reported by the vendor's post but not
confirmed by the linked repository's README. Either the README is
incomplete, the features live elsewhere, or the post overstates. A further
search of the desktop docs (UX guidelines, design notes), the desktop and
editor directory listings, and the 2026-10-10 MoonBit post "Building Agents,
MoonBit is all you need" found no mention of syntax-tree search, Token Diff,
Syntax Tree Diff or Diff Review [S21]. The only lead is an unopened
`editor/syntax` directory and a "DiffEditor" facade, both unconfirmed. Do not
describe the structural search as available until verified in the code.

Update 2026-11-07: a second look found that `moonbitlang/openseek/desktop`
is itself titled "SeekMoon" ("a Proton + Rabbita desktop client for the
OpenSeek agent, written in MoonBit"), so SeekMoon is the desktop client over
the OpenSeek agent. Its README still does not mention syntax-tree search,
Token/Syntax Tree Diff or Diff Review, and the post names no package or
command for them [S7, S19]. The `editor/` README mentions a "DiffEditor"
facade, an unconfirmed lead. Docs/ files and the 2026-10-10 MoonBit blog post
were not read.

Update 2026-11-07 (second pass): the MoonBit release notes for v0.10.14
(2026-09-21) list under SeekMoon: "Integrated diff algorithms based on
MoonBit tokens and ASTs, with support for ignoring differences in tests and
comments", and v0.10.19 (2026-11-05) adds "cloud agents" and "local pull
request review" [S29]. That corroborates the token/AST diff part of the post
(vendor-reported). Separately, the documented `moon ide` command set provides
semantic navigation (see Claim 12) but no syntax-tree pattern search. The
post's structural search with placeholders is still not located in any
documentation or repository read.

## Confidence

Medium (diff corroborated by changelog), Low (structural search)

---

# Claim 5

Much of the proposed interface already exists in standard tooling. LSP
provides versioned and optionally atomic workspace edits. (factual)

## Supporting evidence

LSP 3.17: a `WorkspaceEdit` can carry text edits and file operations; with
`failureHandling: transactional` the operations "either all succeed or no
changes at all are applied"; text document edits can carry a document version
that clients check before applying; servers can advertise code actions and
`referencesProvider`; rename and call hierarchy requests are listed [S8].

## Contrary evidence

Atomicity depends on the client's `failureHandling` setting; `abort` and
`undo` are weaker [S8]. I could not verify what the TypeScript language
service or compiler API expose: the wiki page fetched covers diagnostics and
incremental snapshots only, not rename, refactors or edit objects [S11].

## Assessment

LSP supports the stale-edit and transactional ideas on paper, which backs
Argument 3. Whether TypeScript's tooling can serve as the semantic editing
layer is unverified and needs the TypeScript API reference.

## Confidence

High (LSP), Low (TypeScript specifically)

---

# Claim 6

Agent edit failures depend heavily on edit format and model, so some are
harness limits rather than limits of text. (interpretive)

## Supporting evidence

Aider documents several edit formats (whole-file, search/replace diff,
fenced, udiff) and says different models work better with different ones
[S9]. The Diff-XYZ benchmark (arXiv 2510.12487, v2 2025-11-17) found the
best format depends on use case and model size: search-replace performed best
for larger models across most tasks, structured udiff variants were similar
but slightly worse, and smaller open models gained little from any format
[S10].

## Contrary evidence

Aider's early GPT-3.5/GPT-4 benchmark, via a search summary I did not read on
the page, found whole-file output most reliable, function-call-based edits
worse, and said complex edit formats can make models write worse code and
fail at formatting [S9]. That cuts against the idea that more structured
interfaces help, at least for those models. Those results are old and may not
transfer to current models.

## Assessment

Supports separating "text is the problem" from "the harness is the problem",
and warns that structure is not automatically better. The article must
acknowledge this as the strongest evidence against the thesis's direction.

## Confidence

Medium

---

# Claim 7

A language's properties (static typing, diagnostics) change coding-agent
success, so the feedback loop matters more than syntax. (interpretive; load-
bearing for the broadened thesis, Argument 1)

## Supporting evidence

Type-constrained decoding (Mündler, He, Wang, Sen, Song, Vechev; arXiv
2504.09246, submitted 2025-04-12) uses a language's type system to steer
generation and, per its abstract, "reduces compilation errors by more than
half and significantly increases functional correctness in code synthesis,
translation, and repair tasks across LLMs of various sizes and model
families", formalized on a simply-typed language and extended to TypeScript
[S12]. This is direct evidence that putting static checking in the loop
helps model output.

## Contrary evidence

The paper evaluates on HumanEval and MBPP (function-level tasks), not
repository-level agent work, and the abstract gives no exact figures or
whether the TypeScript experiments used those benchmarks [S12].
Multilingual agent benchmarks do not show a clean typing effect. In SWE-bench
Multilingual (300 tasks, 42 repos, one model, SWE-agent with Claude 3.7
Sonnet, ~42-44 tasks per language group), resolution rates were: Rust 58.14%,
Java 53.49%, PHP 48.84%, Ruby 43.18%, JS/TS 34.88%, Go 30.95%, C/C++ 28.57%
[S13]. A different benchmark, Multi-SWE-bench (ByteDance Seed, arXiv
2504.02605; 1,632 instances from 39 repositories, 7 languages; 9 models x 3
agent methods), was read from the paper's HTML (Table 4). The authors write
that "TS and JS consistently yield the lowest resolved rates", attributing it
to "dynamic typing, asynchronous execution, and diverse runtime behaviors"
and, for C, C++, Rust and Go, to manual memory management, "complex build
systems, and intricate type systems" [S14]. The best resolved rates in the
table are Python 52.20, Java 23.44, Rust 15.90, C++ 14.73, TS 11.61, C 8.59,
Go 7.48 and JS 5.06 [S14].

Reading the table against that statement (my observation, not the authors'):
JS is lowest, but TypeScript's best rate (11.61, and 11.16 for another
method) is higher than Go's and C's best, and TS swings widely for the same
model: Claude 3.7 Sonnet scores 11.16 under one agent method and 2.23 under
another [S14]. Instance counts per language are uneven and come from few
repositories: TypeScript 224 instances from 3 repositories, Go 428 from 3,
JavaScript 356 from 6, Rust 239 from 10, Java 128 from 9 [S14]. TypeScript is
statically typed, so the authors' "dynamic typing" explanation fits JS better
than TS. The authors also list "intricate type systems" as a source of
difficulty for other languages, which is not what a simple "static typing
helps agents" story predicts.

## Assessment

Static checking in the generation loop helps in the one controlled study
found. Cross-language benchmark results are confounded by repository, task
mix and model, rely on small per-language counts, and the two benchmarks
disagree on which languages are hard. They do not isolate language
properties. The article may claim a plausible link and cite the decoding
result, but must not say benchmarks show typed languages do better.

## Confidence

Medium (type checking helps generation), Low (language properties explain
cross-language agent differences; the two benchmarks disagree, results are
repo-confounded, and even the authors' own table only partly matches their
"TS and JS lowest" statement)

---

# Claim 8

Training-data and ecosystem scarcity lowers model performance for a
language, which favors incumbents. (factual, for low-resource languages)

## Supporting evidence

Giagnorio, Martin-Lopez and Bavota (ICPC 2025, arXiv 2501.19085) studied R
and Racket with six LLMs and report poorer code generation than for high-
resource languages, with the best remedy depending on model size: fine-
tuning usually best for smaller models, in-context learning increasingly
effective for larger ones, and fine-tuning very large models can hurt [S15].

## Contrary evidence

The abstract describes the gap only qualitatively, with no numbers or model
names on the page [S15]. It concerns two low-resource languages and
code-generation tasks, not coding agents, and not languages as new as Zero,
BAML or MoonBit. Larger models and in-context learning narrow the gap.

## Assessment

Supports the direction of the incumbency argument for low-resource
languages in general. It does not measure how a brand-new language fares with
current frontier models or agents, so keep that part of Argument 3 as an
inference.

## Confidence

Medium (low-resource gap exists), Low (applies to new agent-oriented languages)

---

# Claim 9

TypeScript's compiler and tooling already provide a transactional semantic
editing layer. (factual; tests thesis Argument 3)

## Supporting evidence

The compiler API exposes program creation, diagnostics, a type checker
(`getSymbolAtLocation`, `getTypeAtLocation`), AST construction through
`ts.factory`, a printer, and a language service with semantic diagnostics
and per-file `version` tracking [S16]. ts-morph adds node manipulation
(`replaceWithText`, `addStatements`, `removeStatement`), code fixes
(`organizeImports`, `fixMissingImports`, `fixUnusedIdentifiers`), and
batches file-system changes until `project.save()`, noting that on a
mid-run error "the files won't be in a halfway state" [S17].

## Contrary evidence

The compiler API page covers TypeScript 6.0 and earlier and says "TypeScript
7.1 will have a completely different API" [S16], a stability risk for any
layer built on it. Neither source documents atomic or versioned multi-file
semantic edits; the ts-morph save batching is advice, not a documented
transaction guarantee [S17]. Follow-up reading found that ts-morph does provide
`rename` ("rename all usages ... across all files", with `renameInComments`
and `renameInStrings` options), `findReferences()` and `getDefinitions()`
[S20]. But its docs describe no refactor or code-action API beyond the code
fixes noted above, expose the language service only as `compilerObject`
("Generally you won't need to use the language service"), call AST transforms
"not a typical scenario", and say "Manipulation support is lacking" for parts
of the language [S20]. The tsserver wiki page names only `open`, `quickinfo`,
`completions` and `geterr` [S18]; the protocol file that would list the edit
commands could not be read (the URL tried returned 404), so tsserver's
refactor and code-action commands, and any version or batching semantics,
remain unverified.

## Assessment

Parts of the interface clearly exist (types, diagnostics, AST edits, rename
and find-references through ts-morph, code fixes), but a transactional, versioned semantic edit layer for TypeScript is
not established by these sources, and the compiler API is about to change.
Argument 3 should say "partly available, with gaps", and the experiment's
purpose is to find the gaps.

## Confidence

Medium (pieces exist), Low (that they compose into a checked transaction)

---

# Claim 10

Zero: what it is, how it works, and where it stands. (factual; tour material)

## Supporting evidence

"A programming language where the graph is the program. Humans ask for
outcomes. Agents query the program graph, submit checked edits, and prove the
result." [S22]. Agents author through `zero query` and `zero patch`; humans
review through `.0` projections and may edit them as an escape hatch [S22].
Explicit capabilities: `world: World` is a capability parameter and
`world.out.write(...)` writes through it; hosted APIs (filesystem, network,
HTTP) "require target capabilities" [S22]. Errors are explicit: `fn ...
raises` and `check`; "There is no hidden exception system." Numeric types do
not implicitly narrow or widen; `.value` reads need a visible `.has` guard
[S22]. Stated runtime goals: token-efficient inspection, low memory, fast
startup, explicit capabilities, small dependency-free artifacts [S22].
Install: `curl -fsSL https://zerolang.ai/install.sh | bash`, then `zero
--version`, `zero doctor` [S22]. Apache-2.0, Vercel Labs, ~5.4k stars [S2].

## Contrary evidence

Marked "Experimental"; the docs say "Expect breaking changes. Run it in a
safe environment, not against production systems" [S22]. No version number or
release date on the pages read. No maintainers named. No non-goals stated.
The docs show `zero patch` results as narrated text rather than captured
terminal output; captured output exists only for `zero query` (a graph dump).
Generics, inference and effect-system semantics are not described on the pages
read.

## Assessment

Enough to tour accurately. Present Zero as an experimental design with a real
CLI and docs, not as a production tool, and do not show narrated results as
real output.

## Confidence

High (design as documented), Low (maturity and behavior beyond the docs)

---

# Claim 11

BAML: what the new language is, how it works, and where it stands. (factual;
tour material)

## Supporting evidence

README: "BAML is the programming language for agents", TypeScript-like
syntax, typed errors, built-in tests/evals, callable from TypeScript, Python,
Go, C# and Java [S4]. Model-backed functions declare a `client` and a `prompt`
and must satisfy their declared return type; `ctx.output_format()` injects the
output schema [S23]. Errors are declared with `throws`, raised with `throw`,
handled with `catch` and an exhaustive `catch_all`; "Omission doesn't mean
`throws never`" [S23]. Concurrency: `spawn` creates "a logical BAML thread,
not a dedicated operating-system thread", `await` joins, "BAML keeps
concurrency at the call site" [S23]. `baml run`, `baml check`, `baml test`
exist; the TypeScript bridge generates `baml_sdk/` via `baml generate`
[S23, S24]. The 0.23.0 release notes add `structured_output = true` for
OpenAI clients [S25]. Standard packages include `ai`, `anthropic`, `assert`,
`aws`, `baml`, `claude_code`, `google`, `log`, `openai`, `reflect`, `testing`,
`trace`, `typesafeai`, `vercel` [S24].

## Contrary evidence

Canary only, no stable release (Claim 3). No test or eval example exists on
any page read, and the testing and evals chapters are unpublished. The only
class-as-return-type example is a snippet in the 0.23.0 post, using
`ChatClient` where the docs use `ResponsesClient`, so syntax is moving
[S23, S25]. Package names are listed without descriptions. The README's
compile-speed claim has no benchmark [S4].

## Assessment

Good tour material for the language's shape (typed model calls, typed
errors, call-site concurrency), as long as every example is labeled canary and
attributed. Do not describe testing or evals beyond "the README and CLI say
they exist".

## Confidence

High (as documented), Low (stability and testing features)

---

# Claim 12

MoonBit: what the language and toolchain are, and where they stand. (factual;
tour material)

## Supporting evidence

"An end-to-end programming language toolchain for cloud and edge computing
across wasm, wasm-gc, js, and native backends", with an "AI native" framing
and claims of small WASM output and fast compilation (vendor claims, no
benchmarks on the pages read) [S27]. Language status: "currently in
beta-preview", "can already be used in production, with backwards-incompatible
changes evaluated seriously" [S27]. Current release: v0.10.19, 2026-11-05;
earlier v0.10.14 (2026-09-21) and v0.10.0 (2026-06-08) [S29]. Package
registry: mooncakes.io [S27]. Tooling: `moon` (build, check, test, fmt, run,
doc, publish and more) [S27]; `moon ide` ("MoonBit Agent IDE") provides
`peek-def`, `find-references`, `rename`, `hover`, `outline`, `analyze`, `doc`,
`workspace-symbols`, `codelens`, `gen-symbols`, and the docs say they "use
semantic analysis rather than text matching" [S27]. `.mbtx` script mode with a
frontmatter import header and `moon run script.mbtx` [S27]. A `moonbitlang/
skills` repository of agent skills (`SKILL.md` folders) installable with `npx
skills` [S30]. Apache-2.0 for `moon`; organization IDEA (International
Digital Economy Academy), Shenzhen [S27, S31].

## Contrary evidence

Pre-1.0 (0.10.x). The `core` README says "It is experimental and under active
development" and "The API is subject to change", which conflicts with
"beta-preview" and "can be used in production" [S31]. Syntax is moving: the
v0.10.19 notes move trait derivation from `derive(...)` after a type to a
`#derive(...)` attribute above it, and rename `Int`/`UInt` to `Int32`/`UInt32`
(with `Int` remaining as an alias), so the official tour's examples already
use older syntax [S28, S29]. `moon prove` (Why3 and SMT solvers) is described
in the 2026-10-10 blog post but appears in no documentation page, and the
documented `moon` command list has no `prove` [S21, S27]. The `moon help`
output on the download page omits `ide`, `prove`, `cram` and `moonx`, so it
looks out of date [S27]. No syntax-tree pattern search in `moon ide`. No
named maintainers.

## Assessment

MoonBit is the most conventional of the three and the best documented, but
fast-moving. Tour examples must carry the version they were taken from and
avoid `derive` forms. Do not present `moon prove` as available without
verification.

## Confidence

High (language and toolchain as documented), Low (`moon prove`, structural
search, production readiness)

---

# Useful examples

Verbatim code taken from official pages, for the tour. Do not edit it; label
each sample with its source and the date read (2026-11-07). The fetch tool
relays pages through a model and some blocks lost whitespace, so re-copy each
block from the live page before publication.

## Zero

From the Zero README, `.0` projection (also on zerolang.ai) [S2, S22]:

```
pub fn main(world: World) -> Void raises {
    check world.out.write("hello from zero\n")
}
```

Creating and running it with checked patch operations, from the README [S2]:

```
zero init
zero patch --op 'addMain' --op 'addCheckWrite fn="main" text="hello from zero\\n"'
zero run
```

An edit guarded by the graph hash, from zerolang.ai [S22]:

```
zero patch \
  --expect-graph-hash graph:a7f7e6899a73f3b4 \
  --op 'set node="#expr_653eeb6e" \
    field="value" \
    expect="hello from zero\n" \
    value="hello graph\n"'
```

Graph query output, from zerolang.ai [S22]:

```
zero-graph v1
origin source-text
module "hello"
hash "graph:a7f7e6899a73f3b4"

node #decl_ad8d9028 Function name:"main" type:"Void" public:true fallible:true
node #param_4610ae76 Param name:"world" type:"World"
node #expr_c403020c MethodCall name:"write" type:"Void"
node #expr_653eeb6e Literal type:"String" value:"hello from zero\n"
edge #expr_c403020c arg #expr_653eeb6e order:0
```

Caveat: the docs show the result of `zero patch` as narrated text; only the
`zero query` dump above is captured output.

## BAML (canary)

A model-backed function returning an enum, from the "Classify support tickets"
example [S23]:

```
enum Category {
  Refund
  CancelOrder
  TechnicalSupport
  AccountIssue
  Question
}

function classify_message(input: string) -> Category {
  client: openai.ResponsesClient.new(model = "gpt-4.1-mini", api_key = env.OPENAI_API_KEY)
  prompt: `
    ${role("system")}
    Classify the support message into one category.
    ${ctx.output_format()}

    ${role("user")}
    ${input}
  `
}
```

Run with `baml check` then `baml run classify_message -- --input "I was
charged twice for my order"` [S23].

Typed errors, from the "Handle errors" chapter [S23]:

```
function handle_bad_input(
    tool: string,
) -> string throws ToolUnavailable | baml.errors.InvalidArgument {
    invoke_tool(tool) catch (e) {
        BadToolInput => `invalid tool input: ${e.message}`,
    }
}
```

Concurrency, from the "Run work concurrently" chapter [S23]:

```
function read_two_documents_all(first_path: string, second_path: string) -> string[] {
    let first_future = spawn { baml.fs.read(first_path) };
    let second_future = spawn { baml.fs.read(second_path) };
    await baml.future.all([first_future, second_future])
}
```

Calling it from TypeScript, from the TypeScript bridge page [S23]:

```
import { classify_message, type Category } from "./baml_sdk/index.js"

export async function classify(input: string): Promise<Category> {
  return classify_message(input)
}
```

## MoonBit (v0.10.19 era; tour syntax predates the derive change)

Hello world and enum with pattern matching, from the official tour [S28]:

```
enum Color {
  Red
  Green
  Blue
  RGB(Int, Int, Int)
  CMYK(Int, Int, Int, Int)
}

fn print_color(color : Color) -> Unit {
  match color {
    Red => println("Red")
    Green => println("Green")
    Blue => println("Blue")
    // Take the three Int values from RGB and print them.
    RGB(r, g, b) => println("RGB: \{r}, \{g}, \{b}")
    CMYK(c, m, y, k) => println("CMYK: \{c}, \{m}, \{y}, \{k}")
  }
}
```

A test block, from the tour's test lesson [S28]:

```
test "fibonacci" {
  inspect(fib(5), content="5")
  inspect(fib(6), content="8")
}

fn fib(n : Int) -> Int {
  if n < 2 {
    n
  } else {
    fib(n - 1) + fib(n - 2)
  }
}
```

Run with `moon test`; `moon test --update` inserts results [S28].

A script, from the docs' `.mbtx` page, run with `moon run script.mbtx` [S27]:

```
---
import {
"moonbitlang/core/list" @ls
}
---

///|
async fn main {
let xs = @ls.List(["1", "2", "3"])
debug(xs)
}
```

# Useful quotes

- "the graph is the program database" (Zero docs) [S1]
- "fail before the store is written" (Zero README) [S2]

# Open questions

- (Resolved 2026-11-07) MoonBit language, version and examples: captured in
  Claim 12 and Useful examples. v0.10.19, pre-1.0.
- (Resolved) Real code examples for Zero, BAML and MoonBit: captured above,
  all attributed; re-copy from live pages before publication.
- Still open for the tour: `moon prove` is not in the documentation; a BAML
  test or eval example does not exist in the published docs; Zero's patch
  results are narrated rather than captured; MoonBit's syntax-tree search is
  unlocated; none of the three has named maintainers on the pages read.
- First-hand trial: nothing here has been run. Every example is copied from
  documentation, so the tour cannot describe real behavior unless the author
  runs them.
- (Added with the broader thesis) Is there evidence that language properties
  such as static typing or diagnostic quality change agent success rates?
- (Added) Is there evidence that training-data volume or ecosystem size
  affects agent performance by language? Currently an assumption.
- What does Zero's patch guarantee under concurrent edits, and is it atomic?
  Read the implementation or ask the maintainers.
- Is the BAML canary language released, and which features are implemented?
- Where do SeekMoon's structural search and diff review actually live?
- What do tsserver and the language service expose for rename, references
  and refactor edits? (Partly answered in Claim 9: not found on the pages read.)
- No independent measurement of compiler speed or agent productivity for any
  of the three. This is the main evidence gap.
- The distinction between type checking, formal verification and behavioral
  correctness was not researched yet.
- No research found on graph-native or structure-editing representations for
  agents.
- Maintainer identity and governance for BAML and MoonBit were not checked.

# Claims requiring author judgment

- How strongly text stays "good enough" (thesis Response).
- Whether the article proposes the TypeScript experiment or reports results.
- How much weight to give the Aider evidence that structure can hurt.
