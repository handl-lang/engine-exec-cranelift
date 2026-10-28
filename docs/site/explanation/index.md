# Explanation

## Why this crate exists

Speed is the only thing it may change: it must agree value-for-value with the reference tree-walk interpreter, and the conformance suite enforces that. Arrow bodies fall back to the reference interpreter.

## Where it sits

This crate belongs to the `engine-*` family. Plugins, kits and hosts reach it
through the kit's slot, so it can be swapped without touching a language
definition.

See the [reference](/engine-exec-cranelift/reference/) for the API and the
[how-to guides](/engine-exec-cranelift/how-to/) for tasks.
