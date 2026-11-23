# How-to guides

Task recipes for `exec-cranelift`.

## Run the gate

```bash
./ci.sh          # fmt -> clippy -D warnings -> test -> doc -D warnings
./ci.sh test     # one stage
```

## Use it from Rust

```bash
cargo add --git https://github.com/handl-lang/exec-cranelift --branch main
```

See the [reference](/exec-cranelift/reference/) for the types involved and the
[explanation](/exec-cranelift/explanation/) for why the crate is shaped this way.
