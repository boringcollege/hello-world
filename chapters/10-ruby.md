# Ruby

Ruby was created by Yukihiro "Matz" Matsumoto in Japan and released in 1995. Matz designed it with a single guiding principle: developer happiness. Ruby syntax reads naturally, encourages expressive code, and hides complexity behind elegant APIs. It rose to global prominence through Ruby on Rails, the web framework that popularized convention-over-configuration and influenced almost every web framework that came after it.

## Prerequisites

```bash
# macOS (Homebrew)
brew install ruby

# Ubuntu / Debian
sudo apt install ruby

# Check version
ruby --version
```

## The program

Create a file named `hello.rb`:

```ruby
puts "Hello, World!"
```

## Explanation

**`puts`** — Short for "put string." It is a built-in method (in Ruby, everything is an object and all functions are methods) that outputs its argument followed by a newline. Parentheses are optional when calling methods in Ruby — `puts("Hello, World!")` is equally valid.

**`"Hello, World!"`** — A string literal. Ruby also accepts single quotes: `'Hello, World!'`. The difference matters for string interpolation, which only works inside double quotes.

There is no `main` function, no class, no import. Ruby scripts execute top-to-bottom just like Python.

## Running it

```bash
ruby hello.rb
```

Output:

```
Hello, World!
```

You can also use the interactive Ruby shell:

```bash
irb
irb(main):001> puts "Hello, World!"
Hello, World!
```

## String interpolation

Ruby's double-quoted strings support interpolation with `#{}`:

```ruby
name = "World"
puts "Hello, #{name}!"
```

Output: `Hello, World!`

## Notes

Ruby's philosophy is that there should be more than one way to do something. Compare that with Python's "there should be one obvious way." Both are valid philosophies that produce very different languages. Ruby's flexibility makes it feel expressive and playful; Python's consistency makes it feel predictable and teachable. The Hello World programs reflect this: both are one line, but Ruby's `puts` feels more like talking.
