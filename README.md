## Building a small OS in Rust

Following the excellent [guide](https://github.com/phil-opp/blog_os) to build a small OS in Rust.

### A Freestanding Rust Binary

```
$ rustup target add thumbv7em-none-eabihf
$ cargo build --target thumbv7em-none-eabihf
```

### A Minimal Rust Kernel

```
$ cargo install cargo-xbuild
$ rustup component add rust-src
$ rustup run nightly cargo xbuild --target x86_64-rust-os.json
$ cargo install bootimage --version "^0.7.8"
$ rustup run nightly cargo bootimage
$ qemu-system-x86_64 -drive format=raw,file=target/x86_64-rust-os/debug/bootimage-rust-os.bin
$ rustup run nightly cargo xrun # similar to previous command
```
