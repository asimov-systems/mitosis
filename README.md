# mitosis

[![Build Status](https://github.com/asimov-systems/mitosis/workflows/Tests/badge.svg)](https://github.com/asimov-systems/mitosis/actions)

<!-- [![License: MIT/Apache-2.0](https://img.shields.io/crates/l/mitosis.svg)](#license) -->
<!-- [![Current Version](https://img.shields.io/crates/v/mitosis.svg)](https://crates.io/crates/mitosis) -->

> "AWS Lambda for your local machine"
>
> -- [@jdm](https://github.com/jdm)

This crate provides `mitosis::spawn()`, which is similar to `thread::spawn()` but will spawn a new process instead.

## The fork

Changes to the original repository:

- Updated `ipc-channel` to `0.20.2` to fix building and add support for Windows;
- Removed unused dependencies;
- Made CI run on Windows & MacOS too;
- Extended the CI to run both tests and examples;
- Fixed `kill` example;
- Fixed clippy warnings;

## Example

```rust

fn main() {
    // Needs to be near the beginning of your program
    mitosis::init();

    // some code
    let some_data = 5;
    mitosis::spawn(some_data, |data| {
        println!("hello from another process, your data is {}", data);
    });
}
```
