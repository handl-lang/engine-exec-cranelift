# exec-cranelift

The Cranelift backend for the eval operation: compiles a node's schemes
to native code (JIT in-process, or an object file for a standalone
binary) instead of walking them — the fastest `EvalEngine`
implementation, checked value-for-value against `exec-tree-walk` (the
oracle). Arrow bodies fall back to the reference interpreter — that is
the one documented dependency on a sibling backend.

## Layout

| path | role |
| --- | --- |
| `src/{compile,standalone}.rs`, `src/lib.rs` | scheme→Cranelift lowering, JIT + standalone object emit |
| `build.rs` | build-time wiring (cranelift deps) |
| `tests/` | engine tests (oracle parity) |
| `xtask/` | vendored gate crate (`fmt`, `clippy`, `test`, `doc`, `gate`) |
| `docs/` | engine docs |
| `workflows/gate.yaml` | per-push gate — `handl-gates` rust campaign via bupha |

## Contract

```rust
use hnl_exec::EvalEngine;
use hnl_exec_cranelift::CraneliftEngineV2;

let value = CraneliftEngineV2::new().eval(&lang, &request)?;
```

- Deps resolve from git — a plain clone test-runs as-is.

## Verification

```bash
cargo run --manifest-path xtask/Cargo.toml -- gate   # fmt → clippy → test → doc
```

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
