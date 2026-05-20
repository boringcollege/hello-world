# C++

C++ was created by Bjarne Stroustrup at Bell Labs in 1983 as "C with Classes." It added object-oriented programming to C while preserving full backward compatibility — valid C is (mostly) valid C++. Over the decades it grew into one of the most powerful and complex languages in existence, adding templates, exceptions, operator overloading, lambdas, and much more. It is the dominant language in game development, high-frequency trading, embedded systems, and performance-critical applications.

## Prerequisites

```bash
# macOS — install Xcode Command Line Tools
xcode-select --install

# Ubuntu / Debian
sudo apt install g++

# Windows — install MinGW-w64 or use WSL
```

Verify:

```bash
g++ --version
```

## The program

Create a file named `hello.cpp`:

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

## Explanation

**`#include <iostream>`** — Includes the input/output stream library. `iostream` is C++'s replacement for C's `stdio.h`.

**`std::cout`** — The standard output stream. `std` is the standard namespace; `::` accesses names within it. `cout` stands for "character output."

**`<<`** — The stream insertion operator. It sends the value on the right into the stream on the left. You can chain multiple `<<` operators on one line.

**`std::endl`** — An I/O manipulator that inserts a newline *and* flushes the output buffer. You can also use `"\n"` which inserts a newline without flushing (faster in loops).

**`return 0;`** — Same as C: zero means success.

## A shorter version using `using namespace std`

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```

`using namespace std` lets you write `cout` instead of `std::cout`. It is convenient in short programs but considered bad practice in larger codebases where namespace collisions are a real concern.

## Running it

```bash
g++ hello.cpp -o hello
./hello
```

Output:

```
Hello, World!
```

## Notes

C++ is simultaneously loved for its power and feared for its complexity. The language has multiple ways to do almost everything, and the "correct" way has changed across C++98, C++11, C++14, C++17, and C++20. If you are starting with C++, aim for modern C++ (C++17 or later) and use a tool like `clang-tidy` to catch common mistakes.
