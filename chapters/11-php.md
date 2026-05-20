# PHP

PHP was created by Rasmus Lerdorf in 1994 as a set of Perl scripts to track visits to his personal website. "PHP" originally stood for "Personal Home Page." It evolved into a full programming language and became the engine behind most of the early web — WordPress, Wikipedia, and Facebook were all built on PHP. Today, PHP powers a significant fraction of all websites, largely through WordPress which runs roughly 40% of the web.

## Prerequisites

```bash
# macOS (Homebrew)
brew install php

# Ubuntu / Debian
sudo apt install php

# Check version
php --version
```

## The program

Create a file named `hello.php`:

```php
<?php
echo "Hello, World!\n";
```

## Explanation

**`<?php`** — The PHP opening tag. PHP was originally designed to be embedded inside HTML files, so the interpreter needs a tag to know where PHP code begins. A file that is pure PHP (no HTML mixing) should start with `<?php` and conventionally omit the closing `?>` tag.

**`echo`** — A language construct (not a function) that outputs one or more strings. Unlike `print`, `echo` can take multiple comma-separated arguments. Both are commonly used.

**`"Hello, World!\n"`** — A string with an explicit newline escape sequence. PHP does not add a newline automatically when using `echo`.

## Running it

**Command line:**

```bash
php hello.php
```

Output:

```
Hello, World!
```

**Built-in web server** — PHP can also serve files directly:

```bash
php -S localhost:8000
```

Create an `index.php`:

```php
<?php
echo "<h1>Hello, World!</h1>";
```

Open `http://localhost:8000` in a browser.

## Mixing PHP and HTML

PHP's original use case was embedding dynamic output inside HTML:

```php
<!DOCTYPE html>
<html>
<body>
  <h1><?php echo "Hello, World!"; ?></h1>
</body>
</html>
```

The PHP interpreter replaces the `<?php ... ?>` block with its output before sending the page to the browser.

## Notes

PHP has a complicated reputation. Its inconsistent standard library (some functions are `str_replace`, others are `strpos` — where does the needle go?) and permissive defaults led to many security vulnerabilities in early web applications. Modern PHP (8.x) is a significantly better language with named arguments, union types, and nullsafe operators. Judge PHP by its current form, not its 1999 form.
