# Rust

Rust was created at Mozilla by Graydon Hoare and released in 2015. Its defining feature is memory safety without a garbage collector — a property it achieves through a compile-time ownership system. No null pointers, no data races, no use-after-free bugs, all guaranteed by the compiler. Rust has been the most loved programming language in the Stack Overflow Developer Survey every single year since 2016.

## Prerequisites

Install Rust using `rustup`, the official toolchain installer:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

This installs `rustc` (the compiler) and `cargo` (the build tool and package manager). Restart your terminal, then verify:

```bash
rustc --version
cargo --version
```

## The program

Create a file named `hello.rs`:

```rust
fn main() {
    println!("Hello, World!");
}
```

## Explanation

**`fn main()`** — Declares the `main` function. `fn` is the keyword for functions in Rust. Like Go, the entry point is always `main`.

**`println!(...)`** — Note the exclamation mark. In Rust, `!` means this is a **macro**, not a function. Macros are expanded at compile time and can do things functions cannot, like accept a variable number of arguments of different types. `println!` formats its arguments and prints them with a trailing newline.

**`"Hello, World!"`** — A string literal. Rust string literals are UTF-8 encoded by default.

The curly braces `{}` delimit the function body. Unlike Python, indentation is style — it is the braces that define scope.

## Running it

**Compile and run directly:**

```bash
rustc hello.rs
./hello
```

**Using Cargo (recommended for any real project):**

```bash
cargo new hello-world
cd hello-world
# src/main.rs already contains Hello World
cargo run
```

Output:

```
Hello, World!
```

## Notes

Rust's ownership system feels unfamiliar at first — the compiler rejects programs that would cause memory bugs in other languages. This can be frustrating early on, but it means that if your Rust program compiles, an entire class of runtime bugs is already ruled out. The community calls this "fighting the borrow checker," and eventually you win.
