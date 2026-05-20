# Kotlin

Kotlin was created by JetBrains (the company behind IntelliJ IDEA) and released in 2016. It compiles to JVM bytecode, making it fully interoperable with Java — you can call Java libraries from Kotlin and vice versa. Google officially adopted Kotlin as a first-class language for Android development in 2017. Kotlin fixes many of Java's pain points: null safety is built in, data classes eliminate boilerplate, and the syntax is significantly more concise.

## Prerequisites

**Option 1 — Install the Kotlin compiler:**

```bash
# macOS (Homebrew)
brew install kotlin

# Check version
kotlinc -version
```

**Option 2 — Use the JVM (if you already have Java):**

Kotlin compiles to `.jar` files that run on any JVM.

**Option 3 — Kotlin Playground:**

Try Kotlin instantly at [play.kotlinlang.org](https://play.kotlinlang.org) — no installation needed.

## The program

Create a file named `hello.kt`:

```kotlin
fun main() {
    println("Hello, World!")
}
```

## Explanation

**`fun main()`** — Declares the `main` function. `fun` is Kotlin's keyword for functions. The entry point is `main` with no required arguments (compare Java's mandatory `String[] args`).

**`println("Hello, World!")`** — A top-level standard library function. It prints its argument followed by a newline. Notice: no `System.out.`, no class, no `static`. Kotlin makes the common case simple.

The curly braces delimit the function body. Semicolons are optional (and idiomatic to omit).

## Compare with Java

The same program in Java requires 5 lines. Kotlin needs 3:

```java
// Java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

```kotlin
// Kotlin
fun main() {
    println("Hello, World!")
}
```

Both compile to the same JVM bytecode and produce identical output.

## Running it

**Compile to a JAR and run:**

```bash
kotlinc hello.kt -include-runtime -d hello.jar
java -jar hello.jar
```

**Run as a script (no compilation step):**

```bash
kotlinc -script hello.kt
```

Output:

```
Hello, World!
```

## String templates

Kotlin uses `$` for string interpolation:

```kotlin
val name = "World"
println("Hello, $name!")
```

For expressions, use `${}`:

```kotlin
println("Hello, ${"World".uppercase()}!")
// Output: Hello, WORLD!
```

## Notes

Kotlin's null safety is enforced by the type system. Every type is non-null by default — to allow null you must write `String?`. This eliminates `NullPointerException` at compile time, which was historically one of Java's most common runtime errors. Tony Hoare, who invented the null reference in 1965, called it his "billion-dollar mistake." Kotlin charges you for it at compile time instead.
