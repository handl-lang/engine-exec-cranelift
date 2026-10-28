# engine-exec-cranelift

The Cranelift backend for eval: compiles schemes to native code (JIT in-process, or an object file for a standalone binary).

## What it is

A **eval engine** in the `engine-*` family. Speed is the only thing it may change: it must agree value-for-value with the reference tree-walk interpreter, and the conformance suite enforces that. Arrow bodies fall back to the reference interpreter.

## Start here

- **Reference** — [public API](/engine-exec-cranelift/reference/)
- **How-to** — [task recipes](/engine-exec-cranelift/how-to/)
- **Explanation** — [design and rationale](/engine-exec-cranelift/explanation/)

No tutorials: this repo is a building block used from Rust. End-to-end
walkthroughs live with the product that composes it — see the
[Handl platform](/handl/).
