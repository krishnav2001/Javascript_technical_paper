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
