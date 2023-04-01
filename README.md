# unreachable_checked!
A fork of [Kixunil/dont_panic](https://github.com/Kixunil/dont_panic)

Ensures that code can't panic at compile time.

Example
-------

This code will compile and (not) run just fine:

```rust
let should_panic = false;
if should_panic {
    unreachable_checked!("This will never execute.");
}
```

However, this code will cause a linking error:

```rust
let should_panic = true;
if should_panic {
    unreachable_checked!("This will never execute.");
}
```

Caveats
-------

* This works only when the appropriate opt_level is specified - it may require release build. You can use the `panic`
    cargo feature to panic instead
* The error message is a weird link error. You don't get line number, etc.
* There may be situations in which you know that the code is unreachable but the compiler can't prove it.

