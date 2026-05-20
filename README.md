# Hello, World! — A Boring College Sample Book

This repository is a working example of a [Boring College](https://github.com/boringcollege/boringcollege) book. It demonstrates the exact file structure and format the sync tool expects, and serves as a template for authors who want to publish their own books.

The book itself covers **Hello World in 12 popular programming languages**: Python, JavaScript, Go, Rust, Java, C, C++, TypeScript, Ruby, PHP, Swift, and Kotlin.

---

## Book structure

Every Boring College book is a directory with this layout:

```
your-book-slug/          ← directory name becomes the URL slug
  book.yaml              ← book metadata and chapter list
  chapters/
    01-first-chapter.md  ← numbered markdown files
    02-second-chapter.md
    ...
```

### `book.yaml`

```yaml
title: Your Book Title
description: A short, one or two sentence description.
cover: https://example.com/cover.jpg   # optional — omit the line if you have no cover
chapters:
  - 01-first-chapter.md
  - 02-second-chapter.md
```

| Field | Required | Notes |
|---|---|---|
| `title` | Yes | Displayed everywhere in the UI |
| `description` | Yes | Used in meta tags and the book listing |
| `cover` | No | Public image URL; omit the field entirely if none |
| `chapters` | Yes | Ordered list of filenames in `chapters/` |

### Chapter files

- Filename: `NN-chapter-slug.md` — two-digit zero-padded index, then a kebab-case slug
- The **first line must be `# Chapter Title`** — an H1 heading. The syncer reads this as the chapter title. Everything after it is the chapter content.
- Content is standard [GitHub Flavored Markdown](https://github.github.com/gfm/). Code blocks with language hints get syntax highlighting.

```markdown
# Chapter Title

Chapter content goes here. Standard GFM Markdown.

```python
print("code blocks are syntax highlighted")
```
```

---

## Syncing to a Boring College instance

Clone the book repo into your `$BOOKS_DIR`:

```bash
cd $BOOKS_DIR
git clone https://github.com/boringcollege/hello-world.git
```

Run the sync tool from your Boring College installation:

```bash
# Sync this book only
./bin/sync --books-dir $BOOKS_DIR --book hello-world

# Sync all books
./bin/sync --books-dir $BOOKS_DIR

# Preview changes without writing to DB
./bin/sync --books-dir $BOOKS_DIR --book hello-world --dry-run
```

After a successful sync the book appears in the admin panel at `/admin/books`. Set the category, adjust chapter access (free vs. paid), and publish.

---

## Claude skill: `/transform-book`

This repo ships a Claude Code skill that converts any Markdown into Boring College format automatically. If you have an existing document — a long single Markdown file, a folder of notes, an exported Notion page — open this repository in [Claude Code](https://claude.ai/code) and run:

```
/transform-book path/to/your-document.md
```

Or for a directory of Markdown files:

```
/transform-book path/to/your-chapters/
```

The skill:
- Splits content into chapters on `# H1` headings
- Strips YAML frontmatter and extracts title/description from it
- Generates `NN-slug.md` filenames
- Writes `book.yaml` with the correct chapter list
- Reports what was created and the next sync command to run

See [`.claude/commands/transform-book.md`](.claude/commands/transform-book.md) for the full specification.

---

## Writing your own book

### Start from scratch

1. Fork or duplicate this repository
2. Edit `book.yaml` — change `title`, `description`, and the `chapters` list
3. Replace the files in `chapters/` with your own
4. Each chapter file must begin with `# Chapter Title`
5. Commit and push

### Convert existing Markdown

1. Clone this repo
2. Open it in Claude Code
3. Run `/transform-book path/to/your-markdown`
4. Review the output, then push

### Guidelines

- **One idea per chapter.** Chapters can be short — 300 words is fine.
- **Start with the H1.** Every chapter file must begin with `# Title`. This is not optional; the syncer uses it.
- **Filenames are slugs.** `01-getting-started.md` → chapter slug `01-getting-started`. Keep them lowercase, kebab-case, no spaces.
- **Images.** Link to publicly accessible URLs. Uploading images is supported if Cloudflare R2 is configured on the Boring College instance.
- **Code blocks.** Always specify the language hint for syntax highlighting: ` ```python `, ` ```go `, ` ```bash `, etc.

---

## Contributing

To add a language chapter to this book:

1. Fork the repo
2. Create `chapters/NN-language.md` following the pattern of existing chapters
3. Add the filename to `book.yaml` in the right position
4. Open a pull request

The chapter should include: a brief language history/description, prerequisites and installation, the complete Hello World code, a line-by-line explanation, how to run it, the expected output, and a closing note.

---

## License

[MIT](LICENSE)
