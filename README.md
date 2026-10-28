# engine-exec-cranelift

The Cranelift backend for the eval operation: compiles a node's schemes to
native code (JIT in-process, or an object file for a standalone binary) instead
of walking them.

```rust
use hnl_engine_exec::EvalEngine;
use hnl_engine_exec_cranelift::CraneliftEngineV2;

let value = CraneliftEngineV2::new().eval(&lang, &request)?;
```

Must agree value-for-value with `engine-exec-tree-walk` (the oracle); the
conformance suite compares both. Arrow bodies fall back to the reference
interpreter — that is the one documented dependency on a sibling backend.

## Docs

- [Reference](https://handl-lang.github.io/docs/engine-exec-cranelift/reference/) — public API
- [How-to](https://handl-lang.github.io/docs/engine-exec-cranelift/how-to/) — task recipes
- [Explanation](https://handl-lang.github.io/docs/engine-exec-cranelift/explanation/) — design

## Development

```bash
cargo test     # deps resolve from git; no sibling checkouts needed
```

`ci.sh` is the gate: `fmt --check` → `clippy -D warnings` → `test` → `doc -D warnings`.

## License

MIT.
