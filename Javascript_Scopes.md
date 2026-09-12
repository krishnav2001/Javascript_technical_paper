# Scopes in JavaScript

**Scope** determines where a variable can be accessed in a program.

JavaScript has mainly **4 types of scopes**:

1. Global Scope  
2. Function Scope  
3. Block Scope  
4. Lexical Scope

---

# 1. Global Scope

A variable declared outside any function or block is in the **global scope**.

It can be accessed from anywhere in the program.

```js
let name = "Krish";

function greet() {
  console.log(name);
}

greet(); // Krish
console.log(name); // Krish
```

---

# 2. Function Scope

Variables declared inside a function can only be accessed inside that function.

`var` is function-scoped.

```js
function test() {
  var age = 22;
  console.log(age);
}

test(); // 22
console.log(age); // Error
```

---

# 3. Block Scope

Variables declared with `let` and `const` inside `{}` are block-scoped.

They can only be accessed inside that block.

```js
{
  let city = "Bangalore";
  const country = "India";

  console.log(city); // Bangalore
}

console.log(city); // Error
```

---

# 4. Lexical Scope

A child function can access variables from its parent function.

This is called **lexical scope**.

```js
function outer() {
  let message = "Hello";

  function inner() {
    console.log(message);
  }

  inner();
}

outer(); // Hello
```

---

# Difference Between `var`, `let`, and `const`

| Keyword | Scope |
|----------|-------|
| `var` | Function Scope |
| `let` | Block Scope |
| `const` | Block Scope |

Example:

```js
function example() {
  if (true) {
    var a = 10;
    let b = 20;
    const c = 30;
  }

  console.log(a); // 10
  console.log(b); // Error
  console.log(c); // Error
}

example();
```

---

There are mainly **4 scopes**:

1. **Global Scope** – Accessible everywhere  
2. **Function Scope** – Accessible only inside a function  
3. **Block Scope** – Accessible only inside `{}`  
4. **Lexical Scope** – Child functions can access parent variables


# Why We Should Avoid Using `var` in JavaScript

We avoid `var` because:

1. It is **function scoped**, not block scoped  
2. It allows **re-declaration**  
3. Hoisting can cause bugs (`undefined`)  
4. It may create unexpected global variables  

So, modern JavaScript uses **`let`** and **`const`** instead.

---

# 1. `var` is Function Scoped (Not Block Scoped)

`var` ignores block `{}` scope.

```js
if (true) {
  var age = 22;
}

console.log(age); // 22
```

Problem:  
The variable is accessible outside the block, which can lead to bugs.

With `let`:

```js
if (true) {
  let age = 22;
}

console.log(age); // Error
```

---

# 2. Re-declaration is Allowed

`var` allows redeclaring the same variable.

```js
var name = "Krish";
var name = "John";

console.log(name); // John
```

Problem:  
You may accidentally overwrite variables.

With `let`:

```js
let name = "Krish";
let name = "John"; // Error
```

---

# 3. Hoisting Can Cause Confusion

`var` gets hoisted and initialized as `undefined`.

```js
console.log(a); // undefined

var a = 10;
```

This can create unexpected behavior.

With `let`:

```js
console.log(a); // Error

let a = 10;
```

`let` and `const` use **Temporal Dead Zone (TDZ)**, making code safer.

---

# 4. Can Accidentally Become Global

Using `var` carelessly may pollute the global scope.

```js
var user = "Krish";
```

This may create issues in large applications.

---

# So Best is 

* Use **`const`** by default  
* Use **`let`** when value changes  
* Avoid **`var`**

Example:

```js
const name = "Krish";
let age = 22;

age = 23;
```

# Why Using Global Variables is Bad in JavaScript

A **global variable** is a variable declared outside functions or blocks, making it accessible from anywhere in the program.

```js
let name = "Musharaf"; // Global variable
```

Global variables are bad because:

1. They can be modified from anywhere  
2. Cause naming conflicts  
3. Make debugging difficult  
4. Reduce code reusability  
5. Stay in memory longer  

So, prefer **local variables** and **function scope**.

Using too many global variables is considered bad practice.

---

# 1. Can Be Modified from Anywhere

Any part of the program can change the value.

```js
let count = 10;

function update() {
  count = 100;
}

update();

console.log(count); // 100
```

Problem:  
It becomes hard to track where the value changed.

---

# 2. Causes Naming Conflicts

Another file or function may use the same variable name.

```js
let user = "Krish";

// Somewhere else
let user = "John"; // Error
```

Problem:  
Variables may clash in large projects.

---

# 3. Hard to Debug

If many functions modify the same variable, finding bugs becomes difficult.

```js
let score = 0;

function add() {
  score++;
}

function reset() {
  score = 0;
}
```

Problem:  
Any function can unexpectedly change the value.

---

# 4. Makes Code Less Reusable

Functions depending on global variables are harder to reuse.

Bad Example:

```js
let tax = 10;

function calculate(price) {
  return price + tax;
}
```

Better Example:

```js
function calculate(price, tax) {
  return price + tax;
}
```

Now the function is reusable.

---

# 5. Memory Issues

Global variables stay in memory for the entire program execution.

Problem:  
Unnecessary memory usage.

---

# Best Practice

* Avoid global variables whenever possible

* Use **local variables**, **function parameters**, `let`, and `const`.

Example:

```js
function greet() {
  const name = "Krish";
  console.log(name);
}

greet();
```
