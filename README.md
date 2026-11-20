# engine-exec-cranelift

The Cranelift backend for the eval operation: compiles a node's schemes to
native code (JIT in-process, or an object file for a standalone binary) instead
of walking them.

An `engine-*` crate: a concrete eval engine — the fastest `EvalEngine`
implementation, checked value-for-value against `engine-exec-tree-walk` (the
oracle). Arrow bodies fall back to the reference interpreter — that is the one
documented dependency on a sibling backend.

```rust
use hnl_engine_exec::EvalEngine;
use hnl_engine_exec_cranelift::CraneliftEngineV2;

let value = CraneliftEngineV2::new().eval(&lang, &request)?;
```

## Development

```bash
cargo xtask gate        # fmt --check → clippy -D warnings → test → doc
```

`cargo xtask` wraps the repo's `xtask/` crate (`fmt`, `clippy`, `test`, `doc`,
`check`, `gate`); `ci.sh` is the gate entry. Deps resolve from git, so no
sibling checkouts are needed; a plain clone test-runs as-is.

## License

MIT.

## Documentation

<https://handl-lang.github.io/docs/engine-exec-cranelift/>
