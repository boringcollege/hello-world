# What's Next

You have written Hello World in 12 programming languages. Take a moment to notice the patterns.

## What you observed

**Compiled vs. interpreted** — C, C++, Go, Rust, Java, Kotlin, and TypeScript require an explicit compilation step (or a tool that handles it for you). Python, JavaScript, Ruby, PHP, and Swift can run scripts directly. Compiled languages tend to be faster at runtime; interpreted languages tend to be faster to iterate on.

**Verbosity vs. simplicity** — Java's five lines vs. Python's one. Neither is wrong — Java's verbosity serves a purpose in large teams with long-lived codebases. Python's simplicity serves a purpose in exploration, data science, and rapid prototyping.

**Type systems** — Go, Rust, Java, C, C++, Kotlin, and TypeScript catch type errors at compile time. Python, JavaScript, Ruby, and PHP discover them at runtime (or not at all). TypeScript adds compile-time types to JavaScript without changing how it runs.

**Memory management** — Python, Ruby, PHP, JavaScript, Go, Java, Kotlin, and Swift all have garbage collectors. Rust and C++ manage memory without GC; C gives you full manual control. Garbage collection trades predictable latency for programmer convenience.

## Where to go from here

**Pick one language and go deep.** Hello World is a first step. The real learning happens when you build something: a command-line tool, a web server, a game, a data pipeline. Pick the language that fits your goal:

- **Web backend** — Go, Python, Ruby, PHP, Java, Kotlin, TypeScript
- **iOS / macOS apps** — Swift
- **Android apps** — Kotlin
- **Systems / embedded** — C, C++, Rust
- **Data science / ML** — Python
- **Frontend web** — JavaScript or TypeScript
- **General purpose, learning** — Python, Go

## Contributing to this book

This repository is open for contributions. To add a new language:

1. Fork the repo on GitHub
2. Create `chapters/NN-<language-slug>.md` following the format of existing chapters:
   - Start with `# Language Name`
   - Include: intro, prerequisites, the code, line-by-line explanation, how to run, output, a note
3. Add the filename to `chapters:` in `book.yaml` at the correct position
4. Open a pull request

The only rule: the chapter must show a complete, runnable Hello World program with a real explanation. No placeholder text.

## Adding your own book to Boring College

This repository demonstrates the format expected by the Boring College sync tool. To publish your own book:

1. Create a repository with this structure:
   ```
   your-book-slug/
     book.yaml
     chapters/
       01-first-chapter.md
       02-second-chapter.md
   ```

2. Write your `book.yaml`:
   ```yaml
   title: Your Book Title
   description: A short description.
   chapters:
     - 01-first-chapter.md
     - 02-second-chapter.md
   ```

3. Each chapter file must begin with an `# H1` heading — the syncer uses this as the chapter title.

4. Run the sync tool to import into a Boring College instance:
   ```bash
   ./bin/sync --books-dir /path/to/parent --book your-book-slug
   ```

## Using the transform-book Claude skill

If you have existing Markdown that is not yet in this format, this repository includes a Claude Code skill that converts it automatically. Open the repository in Claude Code and run:

```
/transform-book path/to/your-book.md
```

Or for a directory of Markdown files:

```
/transform-book path/to/your-chapters/
```

The skill splits the content into chapters, generates the correct filenames, and writes `book.yaml` — ready to sync. See `.claude/commands/transform-book.md` for how it works.

---

Thanks for reading. The best way to learn a language is to use it. Go build something.
