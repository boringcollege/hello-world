Transform the markdown at `$ARGUMENTS` into Boring College book format and write the result to disk.

## Boring College book format

```
<book-slug>/
  book.yaml
  chapters/
    01-<chapter-slug>.md
    02-<chapter-slug>.md
    ...
```

**`book.yaml`** — all fields are strings/lists, no quotes needed:
```yaml
title: Book Title Here
description: One or two sentence description of the book.
cover: https://example.com/cover.jpg   # omit this line entirely if no cover
chapters:
  - 01-chapter-slug.md
  - 02-another-chapter.md
```

**Chapter file rules:**
- First non-empty line MUST be `# Chapter Title` (an H1) — the syncer uses this as the chapter title
- Filename: `NN-<chapter-slug>.md`
  - NN = 1-based index, zero-padded to 2 digits (01, 02, … 09, 10, 11, …)
  - chapter-slug = H1 text lowercased, spaces → `-`, non-alphanumeric stripped, max 60 chars
- Content is standard GFM markdown; preserve all original formatting, code blocks, images, and links exactly

## Steps

### 1. Read the input

`$ARGUMENTS` is one of:
- A **single `.md` file** — treat the entire file as one book
- A **directory** — each `.md` file inside is one chapter (sort by filename)

If `$ARGUMENTS` is empty or the path does not exist, tell the user and stop.

### 2. Detect format and extract metadata

**Title** — in priority order:
1. YAML frontmatter `title:` field
2. The first `# ` H1 heading in the file (or first chapter file)
3. Humanize the filename or directory name (strip leading digits/dashes, replace `-`/`_` with spaces, title-case)

**Description** — in priority order:
1. YAML frontmatter `description:` or `summary:` field
2. First non-empty, non-heading paragraph of the book (trim to ≤ 200 chars at a sentence boundary)
3. Leave empty string `""` — do not invent one

**Cover** — YAML frontmatter `cover:`, `image:`, or `thumbnail:` field. Omit the `cover:` line from `book.yaml` entirely if none found.

### 3. Split into chapters

**Single file:**
- Split the file on `# ` headings (top-level H1s only — NOT H1s inside fenced code blocks)
- Content before the first H1 is the book preamble (use for description if needed; do not create a chapter from it)
- Each H1 and everything after it until the next H1 = one chapter
- If the whole file has no H1s at all, treat the entire content as a single chapter; synthesize an H1 from the book title

**Directory:**
- Enumerate all `.md` files sorted by filename
- Each file = one chapter; strip its YAML frontmatter if present
- If a file has no H1, add `# <humanized filename>` as the first line

**Preserve all content exactly** — do not summarize, rewrite, or omit any text.

### 4. Generate slugs

**Book slug** from title:
- Lowercase entire string
- Replace spaces and runs of non-alphanumeric chars with `-`
- Strip leading/trailing `-`
- Deduplicate consecutive `-`
- Example: `"My Go Book (2nd Ed.)"` → `my-go-book-2nd-ed`

**Chapter slug** from H1 text using the same rules, max 60 chars, trimmed at a word boundary.

### 5. Determine output location

Write the book into a new directory named `<book-slug>/` **in the current working directory** (where the Claude Code session is running, i.e. the repo root), unless the input is already a directory with a suitable slug name — in that case, write in-place after confirming with the user.

Do not overwrite existing files without asking.

### 6. Write files

1. Create `<book-slug>/` and `<book-slug>/chapters/`
2. Write `<book-slug>/book.yaml` — list chapters in order
3. For each chapter, write `<book-slug>/chapters/NN-<chapter-slug>.md`
   - First line: `# <Chapter Title>` (the original H1, verbatim)
   - Blank line after the H1
   - Then the rest of the chapter content

### 7. Report

After writing, print:
- Output path (absolute)
- Book title and slug
- Number of chapters
- Chapter list: `  01-slug.md — Chapter Title`
- Any warnings (missing H1s fixed, frontmatter stripped, etc.)
- Next step hint: `Run: ./bin/sync --books-dir <parent-of-output> --book <book-slug>`

## Slugify rules (reference)

```
func slugify(s):
  s = lowercase(s)
  replace [^a-z0-9]+ with "-"
  strip leading/trailing "-"
  return s[:min(len(s), 60)]  # truncate at word boundary
```

## Example transformation

**Input:** `go-concurrency.md` — a single file with sections:
```markdown
---
title: Go Concurrency Patterns
description: A practical guide to goroutines and channels.
---

# Introduction
Welcome to the book...

# Goroutines
A goroutine is...

# Channels
Channels allow...
```

**Output:**
```
go-concurrency-patterns/
  book.yaml
  chapters/
    01-introduction.md
    02-goroutines.md
    03-channels.md
```

`book.yaml`:
```yaml
title: Go Concurrency Patterns
description: A practical guide to goroutines and channels.
chapters:
  - 01-introduction.md
  - 02-goroutines.md
  - 03-channels.md
```

`chapters/01-introduction.md`:
```markdown
# Introduction
Welcome to the book...
```
