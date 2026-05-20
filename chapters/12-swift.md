# Swift

Swift was created by Chris Lattner at Apple and announced at WWDC 2014. It was designed to replace Objective-C as the primary language for iOS and macOS development — safer, faster, and with a syntax that feels modern. Swift is open source and has grown beyond Apple platforms into server-side development (via Vapor) and systems programming. It borrows ideas from Python, Rust, Ruby, and Haskell.

## Prerequisites

**macOS** — Swift ships with Xcode. Install Xcode from the App Store, or install just the command-line tools:

```bash
xcode-select --install
swift --version
```

**Linux** — Download the Swift toolchain from [swift.org/download](https://www.swift.org/download/).

**Windows** — Download from swift.org or use the official installer.

## The program

Create a file named `hello.swift`:

```swift
print("Hello, World!")
```

## Explanation

**`print`** — A global function in Swift's standard library. It writes its argument to standard output followed by a newline. Unlike C's `printf`, Swift's `print` is type-safe — it accepts any value that can be converted to a string.

**`"Hello, World!"`** — A `String` literal. Swift strings are Unicode by default and support full emoji and international text without any extra configuration.

There is no `main` function required in a Swift script — the interpreter executes the file top-to-bottom, similar to Python and Ruby.

## Running it

```bash
swift hello.swift
```

Output:

```
Hello, World!
```

For a proper app or package, use the Swift Package Manager:

```bash
swift package init --name HelloWorld --type executable
cd HelloWorld
swift run
```

## String interpolation

Swift uses `\()` for string interpolation:

```swift
let name = "World"
print("Hello, \(name)!")
```

Output: `Hello, World!`

## A typed version

```swift
func greet(name: String) -> String {
    return "Hello, \(name)!"
}

print(greet(name: "World"))
```

Swift uses named parameters — you call `greet(name: "World")`, not just `greet("World")`. This makes call sites readable without looking at the function signature.

## Notes

Swift's optionals are one of its most distinctive features. Rather than allowing `nil` anywhere (like Java's `null`), Swift forces you to explicitly declare a variable as optional (`String?`) before it can be `nil`. You then have to safely unwrap it before use. This prevents an entire class of null-pointer crashes at compile time — the same philosophy as Rust's `Option<T>`.
