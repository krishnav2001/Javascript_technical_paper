# Truthy and Falsy Values in JavaScript

In JavaScript, every value is treated as either:

- **Truthy** → behaves like `true`
- **Falsy** → behaves like `false`

This happens in conditions like:

```js
if (value) {
  console.log("True");
} else {
  console.log("False");
}
```

---

# 1. Falsy Values

JavaScript has only a few **falsy values**.

These values become `false` in boolean context.

## List of Falsy Values

| Value | Meaning |
|--------|----------|
| `false` | Boolean false |
| `0` | Number zero |
| `-0` | Negative zero |
| `0n` | BigInt zero |
| `""` | Empty string |
| `null` | No value |
| `undefined` | Value not assigned |
| `NaN` | Invalid number |

---

## Examples

### `false`

```js
if (false) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

### `0`

```js
if (0) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

### Empty String `""`

```js
if ("") {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

### `null`

```js
if (null) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

### `undefined`

```js
let name;

if (name) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

### `NaN`

```js
if (NaN) {
  console.log("Truthy");
} else {
  console.log("Falsy");
}

// Falsy
```

---

# 2. Truthy Values

Everything that is **not falsy** is **truthy**.

## Common Truthy Values

| Value |
|--------|
| `true` |
| `"hello"` |
| `" "` (space) |
| `"0"` |
| `"false"` |
| `1` |
| `-1` |
| `[]` |
| `{}` |
| `function(){}` |

---

## Examples

### Non-empty String

```js
if ("hello") {
  console.log("Truthy");
}

// Truthy
```

---

### Space `" "`

```js
if (" ") {
  console.log("Truthy");
}

// Truthy
```

Even space is truthy because the string is **not empty**.

---

### Empty Array `[]`

```js
if ([]) {
  console.log("Truthy");
}

// Truthy
```

This surprises many beginners.

Arrays are objects, and objects are truthy.

---

### Empty Object `{}`

```js
if ({}) {
  console.log("Truthy");
}

// Truthy
```

---

### String `"false"`

```js
if ("false") {
  console.log("Truthy");
}

// Truthy
```

Because it is just a non-empty string.

---

### String `"0"`

```js
if ("0") {
  console.log("Truthy");
}

// Truthy
```

String `"0"` is different from number `0`.

---

# 3. Boolean Conversion

JavaScript converts values into boolean automatically.

You can manually convert using `Boolean()`.

```js
console.log(Boolean(0));
// false

console.log(Boolean("hello"));
// true

console.log(Boolean([]));
// true
```

---

# 4. Double NOT (`!!`)

Shortcut to convert into boolean.

```js
console.log(!!0);
// false

console.log(!!"hello");
// true

console.log(!![]);
// true
```

---

# 5. Common Interview Questions

## Is `[]` truthy or falsy?

```js
Boolean([]);
// true
```

**Truthy**

---

## Is `{}` truthy or falsy?

```js
Boolean({});
// true
```

**Truthy**

---

## Is `"0"` truthy or falsy?

```js
Boolean("0");
// true
```

**Truthy**

---

## Is `0` truthy or falsy?

```js
Boolean(0);
// false
```

**Falsy**

---

## Is `"false"` truthy or falsy?

```js
Boolean("false");
// true
```

**Truthy**

Because it is a string.

---

# Example in Real World

### Checking login user

```js
const username = "Krish";

if (username) {
  console.log("User logged in");
} else {
  console.log("No user");
}
```

---

### Checking empty input

```js
const name = "";

if (!name) {
  console.log("Please enter name");
}
```

---

# Easy Trick to Remember

## Falsy Values

Think:

```txt
Empty, Zero, Missing, Invalid
```

Examples:

```txt
0
""
null
undefined
NaN
false
```

---

## Truthy Values

Think:

```txt
Everything else
```

---

# Quick Summary

| Value | Truthy/Falsy |
|--------|---------------|
| `false` | Falsy |
| `0` | Falsy |
| `""` | Falsy |
| `null` | Falsy |
| `undefined` | Falsy |
| `NaN` | Falsy |
| `"hello"` | Truthy |
| `[]` | Truthy |
| `{}` | Truthy |
| `"0"` | Truthy |

## Final Rule

Only **8 values are falsy** in JavaScript.

Everything else is **truthy**.
