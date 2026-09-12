# Javascript Functions
JavaScript functions are reusable blocks of code designed to perform specific tasks, which execute when called or invoked. In JavaScript, functions are first-class objects, meaning they can be passed as arguments, returned from other functions, and assigned to variables.
## Different Ways of Declaring a Function in JavaScript

There are multiple ways to create functions in JavaScript.

---

## 1. Function Declaration

Also called **Function Statement**.

### Syntax

```js
function greet() {
  console.log("Hello");
}
```

### Example

```js
function add(a, b) {
  return a + b;
}

console.log(add(10, 20));
// 30
```

### Features

- Fully hoisted
- Can call before declaration

```js
greet();

function greet() {
  console.log("Hello");
}
```

---

## 2. Function Expression

Function stored inside a variable.

### Syntax

```js
const greet = function () {
  console.log("Hello");
};
```

### Example

```js
const add = function (a, b) {
  return a + b;
};

console.log(add(10, 20));
// 30
```

### Features

- Not fully hoisted
- Cannot call before declaration

```js
greet();

const greet = function () {
  console.log("Hello");
};
```

### Output

```txt
ReferenceError
```

---

## 3. Named Function Expression

A function expression with a name.

### Syntax

```js
const greet = function sayHello() {
  console.log("Hello");
};
```

### Example

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

This will fail:

```js
sayHello();
```

### Output

```txt
ReferenceError
```

Because the name exists only inside the function.

---

## 4. Arrow Function

Short syntax introduced in ES6.

### Syntax

```js
const greet = () => {
  console.log("Hello");
};
```

### Example

```js
const add = (a, b) => {
  return a + b;
};

console.log(add(10, 20));
// 30
```

---

## Shorter Arrow Function

If only one line:

```js
const add = (a, b) => a + b;

console.log(add(10, 20));
// 30
```

Implicit return happens automatically.

---

## Single Parameter

Parentheses optional.

```js
const square = num => num * num;

console.log(square(5));
// 25
```

---

### Features

- Short syntax
- No own `this`
- Not fully hoisted

---

## 5. Anonymous Function

Function without a name.

### Example

```js
function () {
  console.log("Hello");
}
```

Usually used inside:

```js
setTimeout(function () {
  console.log("Hello");
}, 1000);
```

---

## 6. IIFE (Immediately Invoked Function Expression)

Runs immediately after creation.

### Syntax

```js
(function () {
  console.log("Runs immediately");
})();
```

### Example

```js
(function () {
  const secret = "Hidden";

  console.log(secret);
})();
```

### Output

```txt
Hidden
```

Used to create private scope.

---

## 7. Constructor Function

Used to create objects.

### Example

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const user = new Person(
  "Krish",
  22
);

console.log(user);
```

### Output

```txt
{
  name: "Krish",
  age: 22
}
```

---

## 8. Method Function

Function inside an object.

### Example

```js
const user = {
  name: "Krish",

  greet() {
    console.log("Hello");
  },
};

user.greet();
```

### Output

```txt
Hello
```

---

## 9. Callback Function

Function passed as argument.

### Example

```js
function greet(name, callback) {
  console.log("Hi " + name);

  callback();
}

function sayBye() {
  console.log("Bye");
}

greet("Krish", sayBye);
```

### Output

```txt
Hi Krish
Bye
```

---

## 10. Generator Function

Can pause execution using `yield`.

### Syntax

```js
function* generate() {
  yield 1;
  yield 2;
}
```

### Example

```js
function* numbers() {
  yield 1;
  yield 2;
  yield 3;
}

const result = numbers();

console.log(result.next());
```

### Output

```txt
{ value: 1, done: false }
```

---

## 11. Async Function

Used for asynchronous code.

### Example

```js
async function getData() {
  return "Data";
}

getData().then(console.log);
```

### Output

```txt
Data
```

---

# Comparison Table

| Type | Hoisted? | Name Required? |
|------|-----------|----------------|
| Function Declaration | Yes | Yes |
| Function Expression | No | No |
| Named Function Expression | No | Yes |
| Arrow Function | No | No |
| Anonymous Function | No | No |
| IIFE | No | Optional |
| Method Function | No | Yes |
| Callback Function | Depends | Optional |
| Generator Function | Yes | Yes |
| Async Function | Yes | Yes |

---

# Most Commonly Used

In real-world development, these are most common:

### Function Declaration

```js
function greet() {}
```

### Function Expression

```js
const greet = function () {};
```

### Arrow Function

```js
const greet = () => {};
```

---

# Final Rule

Use:

- **Function Declaration** → reusable normal functions
- **Function Expression** → assign function to variable
- **Arrow Function** → short syntax and callbacks
- **IIFE** → run immediately
- **Async Function** → async operations
- **Generator Function** → pause/resume execution

## What Happens When a Function Does Not Have a `return` Statement?

If a function does **not** have a `return` statement, JavaScript automatically returns:

```js
undefined
```

---

### Example 1: No Return Statement

```js
function greet() {
  console.log("Hello");
}

const result = greet();

console.log(result);
```

### Output

```txt
Hello
undefined
```

### Why?

The function prints:

```txt
Hello
```

But since there is **no `return` statement**, JavaScript automatically does:

```js
return undefined;
```

Internally JavaScript sees:

```js
function greet() {
  console.log("Hello");

  return undefined;
}
```

---

### Example 2: Function with Return

```js
function add(a, b) {
  return a + b;
}

const result = add(10, 20);

console.log(result);
```

### Output

```txt
30
```

Because:

```js
return a + b;
```

sends the value back.

---

### Example 3: `console.log()` vs `return`

Many beginners confuse these.

### Wrong Understanding

```js
function add(a, b) {
  console.log(a + b);
}

const result = add(10, 20);

console.log(result);
```

### Output

```txt
30
undefined
```

### Why?

`console.log()` only **prints**.

It does **not return** anything.

So JavaScript still returns:

```js
undefined
```

---

### Example 4: Empty Function

```js
function test() {}

console.log(test());
```

### Output

```txt
undefined
```

Because no return exists.

---

### Example 5: Early Return

You can stop execution using `return`.

```js
function checkAge(age) {
  if (age < 18) {
    return "Not allowed";
  }

  return "Allowed";
}

console.log(checkAge(16));
```

### Output

```txt
Not allowed
```

Once `return` executes, the function stops.

---

### Important Rule

After `return`, code does not run.

```js
function test() {
  return "Hello";

  console.log("Hi");
}

console.log(test());
```

### Output

```txt
Hello
```

This line never runs:

```js
console.log("Hi");
```

Because function execution already ended.

---

# Visual Understanding

## Without Return

```js
function test() {
  console.log("Hello");
}
```

JavaScript treats it like:

```js
function test() {
  console.log("Hello");

  return undefined;
}
```

---

## With Return

```js
function test() {
  return "Hello";
}
```

Returns:

```txt
Hello
```

---

# Quick Summary

| Situation | Return Value |
|-----------|---------------|
| No `return` | `undefined` |
| `return value` | That value |
| `return;` | `undefined` |
| `console.log()` only | `undefined` |

---

# Final Rule

If a function does **not** explicitly return something:

```js
return undefined;
```

is automatically added by JavaScript.
