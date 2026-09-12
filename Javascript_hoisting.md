# Function Hoisting in JavaScript

## What is Hoisting?

**Hoisting** is JavaScript's behavior of moving **declarations** to the top of their scope during execution.

This means some functions and variables can be used **before they are declared**.

---

# 1. Function Declaration Hoisting

**Function declarations are fully hoisted.**

You can call them **before declaration**.

## Syntax

```js
function greet() {
  console.log("Hello");
}
```

## Example

```js
greet();

function greet() {
  console.log("Hello");
}
```

### Output

```txt
Hello
```

### Why?

JavaScript internally treats it like this:

```js
function greet() {
  console.log("Hello");
}

greet();
```

The whole function gets hoisted.

---

# 2. Function Expression Hoisting

Function expressions are **not fully hoisted**.

Only the variable declaration gets hoisted.

## Syntax

```js
const greet = function () {
  console.log("Hello");
};
```

## Example

```js
greet();

const greet = function () {
  console.log("Hello");
};
```

### Output

```txt
ReferenceError:
Cannot access 'greet' before initialization
```

### Why?

Only this gets hoisted:

```js
const greet;
```

But it stays in the **Temporal Dead Zone (TDZ)** until initialization.

So JavaScript does **not know the function yet**.

---

# 3. Function Expression with `var`

With `var`, declaration is hoisted as `undefined`.

## Example

```js
greet();

var greet = function () {
  console.log("Hello");
};
```

### Output

```txt
TypeError:
greet is not a function
```

### Why?

Internally JavaScript sees:

```js
var greet = undefined;

greet(); // undefined()

greet = function () {
  console.log("Hello");
};
```

You are trying to call `undefined` as a function.

---

# 4. Arrow Function Hoisting

Arrow functions behave like function expressions.

They are **not fully hoisted**.

## Example with `const`

```js
sayHi();

const sayHi = () => {
  console.log("Hi");
};
```

### Output

```txt
ReferenceError
```

Because `const` stays inside **TDZ**.

---

## Example with `var`

```js
sayHi();

var sayHi = () => {
  console.log("Hi");
};
```

### Output

```txt
TypeError
```

Because:

```js
var sayHi = undefined;
```

---

# 5. Named Function Expression

```js
const greet = function sayHello() {
  console.log("Hello");
};

greet();
```

### Output

```txt
Hello
```

But this will fail:

```js
sayHello();
```

### Output

```txt
ReferenceError
```

Because the name only exists **inside the function**.

---

# Hoisting Comparison Table

| Function Type | Hoisted? | Can Call Before Declaration? |
|---------------|-----------|-------------------------------|
| Function Declaration | Yes (fully) | Yes |
| Function Expression (`var`) | Partial | No |
| Function Expression (`let`) | Partial | No |
| Function Expression (`const`) | Partial | No |
| Arrow Function (`var`) | Partial | No |
| Arrow Function (`let/const`) | Partial | No |

---

# Visual Understanding

## Function Declaration

```js
greet();

function greet() {
  console.log("Hello");
}
```

JavaScript sees:

```js
function greet() {
  console.log("Hello");
}

greet();
```

---

## Function Expression (`var`)

```js
greet();

var greet = function () {};
```

JavaScript sees:

```js
var greet = undefined;

greet();
```

Error:

```txt
TypeError
```

---

## Function Expression (`const`)

```js
greet();

const greet = function () {};
```

JavaScript sees:

```js
// TDZ

greet();
```

Error:

```txt
ReferenceError
```

---

# Interview Question

## Which functions are hoisted?

### Answer

All function-related variables are hoisted, but:

- **Function declarations are fully hoisted**
- **Function expressions and arrow functions are only partially hoisted**

---

# Easy Rule to Remember

### Function Declaration

```txt
Can call before declaration
```

---

### Function Expression / Arrow Function

```txt
Cannot call before declaration
```

---

# Final Rule

If you use:

```js
function greet() {}
```

It is **fully hoisted**.

If you use:

```js
const greet = function () {};
```

or

```js
const greet = () => {};
```

It is **not fully hoisted**, and calling before declaration causes an error.
