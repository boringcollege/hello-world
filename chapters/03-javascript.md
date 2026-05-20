# JavaScript

JavaScript was created by Brendan Eich in 10 days in 1995 and shipped in Netscape Navigator. It is the only language that runs natively in every web browser, which makes it impossible to avoid in web development. Since 2009, Node.js has let JavaScript run on servers too, making it one of the few languages that spans both frontend and backend.

## Prerequisites

**In the browser** — no installation needed. Open any browser, press `F12` (or right-click → Inspect → Console tab).

**With Node.js** — install from [nodejs.org](https://nodejs.org):

```bash
# macOS (Homebrew)
brew install node

# Ubuntu / Debian
sudo apt install nodejs

# Check version
node --version
```

## The program

Create a file named `hello.js`:

```javascript
console.log("Hello, World!");
```

## Explanation

`console` is a global object available in browsers and Node.js. Its `log` method prints a value to the console and appends a newline. The dot (`.`) accesses a method on an object. Parentheses call the method. Semicolons are optional in JavaScript but conventional.

## Running it

**Node.js (terminal):**

```bash
node hello.js
```

**Browser console:**

Open DevTools (`F12`), go to the Console tab, and type:

```javascript
console.log("Hello, World!");
```

Both produce:

```
Hello, World!
```

## Bonus: inside an HTML page

```html
<!DOCTYPE html>
<html>
<body>
  <script>
    console.log("Hello, World!");
    document.body.textContent = "Hello, World!";
  </script>
</body>
</html>
```

Save it as `hello.html` and open it in a browser. The page shows the text and the console logs it.

## Notes

JavaScript's official name is **ECMAScript**. Every year the language gets new features through the ECMAScript specification. Modern JavaScript (ES2015 and later) looks quite different from the 1995 original, but `console.log("Hello, World!")` has worked since Node.js 0.1.0.
