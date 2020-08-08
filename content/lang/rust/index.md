---
title: Rust
image: logos/rust.png
---

Rust (aka. [Rust-lang](https://www.rust-lang.org/)) is a programming language boasting guaranteed memory-safety, guaranteed thread-safety, and memory-efficiency with no garbage collection.

This guide will show how to install Rust on FreeBSD.

## Installing

The Rust project uses "channels" to manage releases.
From [the docs:](https://doc.rust-lang.org/1.0.0/book/release-channels.html)

> New nightly releases are created once a day.
> Every six weeks, the latest nightly release is promoted to ‘Beta’.
> At that point, it will only receive patches to fix serious errors.
> Six weeks later, the beta is promoted to ‘Stable’, and becomes the next release of `1.x`.

FreeBSD has both `rust` and `rust-nightly` packages, but they conflict with each other.
That means we can't have more than one release on the same system at the same time.
Therefore, the best way to install Rust is to use [RustUp](https://github.com/rust-lang/rustup.rs/blob/master/README.md).

RustUp is Rust's toolchain installer.
It allows users to easily install different releases and switch between them.
To install RustUp, simply run the command below and follow the installer's instructions:

```shell
curl https://sh.rustup.rs -sSf | sh
```

After having installed RustUp, we can use it to install a different release and switch to it:

```shell
rustup toolchain install nightly
rustup default nightly
```

## Checking Install

In order to check that everything is installed correctly, let's make a small `Hello World` program.
Cargo makes this very simple.
We first create a new project with `cargo new` and then compile and run it with `cargo run`.

```shell
cargo new check-install
cd check-install
cargo run
```

There should be a bit of output from the Rust compiler, and the final line should be `Hello, World!`.

## Conclusion

For more information, check out Rust's [getting started](https://www.rust-lang.org/learn/get-started) guide or [doc.rust-lang.org](https://doc.rust-lang.org/).
