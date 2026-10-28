# Reference

## Public API

Run `cargo doc --no-deps` for the full surface; the entry points are the ones
the `engine-*` contract for this slot exposes.

## Crate

| crate | role |
|---|---|
| `hnl-engine-exec-cranelift` | eval engine |

## Build and test

```bash
cargo test     # deps resolve from git; no sibling checkouts needed
```

Dependencies are git deps on `branch = "main"`; there is no crates.io release
and no `[patch]` table in the manifest, so a plain clone test-runs as-is.
