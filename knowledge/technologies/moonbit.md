# MoonBit

Language and toolchain from IDEA (Shenzhen). Apache-2.0 for `moon`. Backends:
wasm, wasm-gc, js, native. Registry: mooncakes.io. Release v0.10.19
(2026-11-05); docs call it "beta-preview", `core` README calls it
"experimental". Syntax is moving (derive moved to `#derive(...)` attributes in
v0.10.19; `Int` renamed `Int32` with an alias). `moon ide` provides semantic
navigation commands (peek-def, find-references, rename, hover, outline, doc,
codelens, ...). `.mbtx` script mode. SeekMoon's token/AST diff is listed in
release notes (v0.10.14); its structural search is unlocated. `moon prove`
appears in a blog post but not in the docs.

Sources: https://docs.moonbitlang.com/ , https://tour.moonbitlang.com/ ,
https://www.moonbitlang.com/updates/
