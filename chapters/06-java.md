# Java

Java was released by Sun Microsystems in 1995 with the promise of "write once, run anywhere." It compiles to bytecode that runs on the Java Virtual Machine (JVM), which is available on virtually every platform. Java is the dominant language in enterprise software, Android development (historically), and large-scale backend systems. It introduced object-oriented programming to an entire generation of developers.

## Prerequisites

Install the Java Development Kit (JDK):

```bash
# macOS (Homebrew)
brew install openjdk

# Ubuntu / Debian
sudo apt install default-jdk

# Windows — download from adoptium.net
```

Verify:

```bash
java --version
javac --version
```

## The program

Create a file named **`HelloWorld.java`** (the filename must exactly match the class name):

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

## Explanation

**`public class HelloWorld`** — In Java, all code lives inside a class. `public` means it is accessible from anywhere. The class name must match the filename.

**`public static void main(String[] args)`** — This is the entry point. It must have this exact signature:
- `public` — accessible from the JVM launcher
- `static` — can be called without creating an instance of the class
- `void` — returns nothing
- `String[] args` — command-line arguments (an array of strings)

**`System.out.println("Hello, World!")`** — `System` is a class in `java.lang` (auto-imported). `out` is a static field of type `PrintStream`. `println` is a method on that stream that prints a line and adds a newline. The semicolon is required.

## Running it

```bash
# Compile
javac HelloWorld.java

# Run (no .class extension)
java HelloWorld
```

Output:

```
Hello, World!
```

Modern Java (11+) can also run a single file directly without a separate compile step:

```bash
java HelloWorld.java
```

## Notes

Java's verbosity is intentional — every piece of the signature (`public static void main`) carries meaning and can be changed. This explicitness is a feature in large teams where code is read far more often than it is written. If you find it ceremonious, Kotlin (Chapter 13) compiles to the same JVM bytecode with a fraction of the boilerplate.
