# TypeScript

TypeScript was created by Microsoft engineer Anders Hejlsberg (who also designed C#) and released in 2012. It is a strict syntactical superset of JavaScript — every valid JavaScript program is also a valid TypeScript program. TypeScript adds optional static type annotations that are checked at compile time and then erased, producing plain JavaScript. It has become the standard choice for large JavaScript codebases at companies like Google, Airbnb, and Slack.

## Prerequisites

TypeScript requires Node.js. If you completed Chapter 3, you already have it. Install the TypeScript compiler globally:

```bash
npm install -g typescript

# Verify
tsc --version
```

For running TypeScript directly without a compile step, install `ts-node`:

```bash
npm install -g ts-node
```

## The program

Create a file named `hello.ts`:

```typescript
const message: string = "Hello, World!";
console.log(message);
```

## Explanation

**`const message: string`** — Declares a constant named `message` with an explicit type annotation of `string`. The `: string` part is TypeScript — it tells the compiler this variable must always hold a string value. If you tried to write `message = 42` later, the compiler would reject it.

**`= "Hello, World!"`** — Assigns the string value. TypeScript can also infer the type automatically:

```typescript
const message = "Hello, World!"; // TypeScript knows this is a string
```

**`console.log(message)`** — Identical to JavaScript. After type checking, TypeScript compiles this to the same JavaScript you saw in Chapter 3.

## Running it

**Compile then run:**

```bash
tsc hello.ts
node hello.js
```

`tsc` produces a `hello.js` file with the type annotations stripped out.

**Run directly with ts-node:**

```bash
ts-node hello.ts
```

Output:

```
Hello, World!
```

## A more TypeScript-flavored version

```typescript
function greet(name: string): string {
    return `Hello, ${name}!`;
}

console.log(greet("World"));
```

This version shows a typed function — `name` must be a string, and the function is declared to return a string. The backtick string is a template literal (available in modern JavaScript too).

## Notes

TypeScript's type system is one of the most expressive available. It supports union types, intersection types, mapped types, conditional types, and generics. But you can adopt it gradually — start with plain JavaScript and add types as needed. The `any` type is an escape hatch that opts out of type checking entirely.
