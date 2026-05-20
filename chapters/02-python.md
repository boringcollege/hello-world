# Python

Python was created by Guido van Rossum and first released in 1991. It is designed around readability — the language uses indentation instead of braces and reads almost like plain English. Python is the most popular language in data science, machine learning, scripting, and education, and it consistently ranks first or second in every major survey.

## Prerequisites

Check if Python is already installed:

```bash
python3 --version
```

If not, download it from [python.org](https://www.python.org/downloads/) or install it with your system package manager:

```bash
# macOS (Homebrew)
brew install python

# Ubuntu / Debian
sudo apt install python3

# Windows — download the installer from python.org
```

## The program

Create a file named `hello.py`:

```python
print("Hello, World!")
```

That is the entire program.

## Explanation

`print` is a built-in function. You call it with parentheses and pass the string you want to output. The string is enclosed in double quotes (single quotes work too). Python adds a newline at the end automatically.

There is no `main` function, no class, no import, no semicolon. Python executes a script top-to-bottom.

## Running it

```bash
python3 hello.py
```

Output:

```
Hello, World!
```

You can also run it interactively in the Python REPL:

```bash
python3
>>> print("Hello, World!")
Hello, World!
```

## Notes

Python's philosophy is captured in **The Zen of Python** (`import this`). The guiding principle: *Readability counts.* Hello World in Python is about as readable as it gets.
