# JavaScript Revision Notes

Quick, practical guide to core JavaScript concepts, syntax, and patterns.

---

## 1. Spread Operator (`...`)

Unpacks elements of an iterable (arrays, objects, strings) into individual elements or properties.

```javascript
// Arrays
const numbers = [1, 2, 3];
const expanded = [...numbers, 4, 5]; // [1, 2, 3, 4, 5]
const copyArr = [...numbers];

// Objects
const user = { name: "Alex", role: "Dev" };
const updatedUser = { ...user, role: "Lead", location: "NY" }; 
// { name: "Alex", role: "Lead", location: "NY" }

// Function arguments
const sum = (a, b, c) => a + b + c;
sum(...numbers); // 6
```

---

## 2. Template Literals

Strings created using backticks (`` ` ``) allowing string interpolation, multiline formatting, and expression evaluation.

```javascript
const user = "Sam";
const score = 85;

// Interpolation & expressions
const message = `Hello ${user}, your grade is ${score >= 80 ? "Pass" : "Fail"}.`;

// Multiline string
const html = `
  <div>
    <h1>${user}</h1>
  </div>
`;
```

---

## 3. Default Parameters

Assigns fallback values to function parameters if they are `undefined` or omitted.

```javascript
function greet(name = "Guest", prefix = "Welcome") {
  return `${prefix}, ${name}!`;
}

greet();                // "Welcome, Guest!"
greet("Sarah");         // "Welcome, Sarah!"
greet("Leo", "Hi");     // "Hi, Leo!"
greet(undefined, "Hi"); // "Hi, Guest!" (falls back)
greet(null, "Hi");      // "Hi, null!" (null is NOT undefined)
```

---

## 4. Destructuring

Extracts values from arrays or properties from objects into distinct variables.

```javascript
// Array Destructuring
const coords = [10, 20, 30];
const [x, y] = coords;          // x = 10, y = 20
const [, , z] = coords;         // z = 30 (skipping)
const [first, ...rest] = coords; // first = 10, rest = [20, 30]

// Object Destructuring
const config = { host: "localhost", port: 8080, debug: true };
const { host, port } = config;

// Renaming & default values
const { debug: isDebugMode, timeout = 5000 } = config; 
// isDebugMode = true, timeout = 5000
```

---

## 5. Closures

A function bundled together with references to its surrounding state (lexical environment). Inner functions retain access to the outer scope even after the outer function has finished executing.

```javascript
function createCounter(initialValue = 0) {
  let count = initialValue;

  return {
    increment: () => ++count,
    decrement: () => --count,
    getValue: () => count
  };
}

const counter = createCounter(10);
console.log(counter.increment()); // 11
console.log(counter.increment()); // 12
console.log(counter.getValue());   // 12
```

---

## 6. Arrow Functions vs Regular Functions

| Feature | Regular Function | Arrow Function |
| :--- | :--- | :--- |
| `this` binding | Dynamic (depends on how function is called) | Lexical (inherits `this` from parent scope) |
| `arguments` object | Available | Not available (use rest parameters instead) |
| Constructor (`new`) | Can be used as constructor | Cannot be used with `new` |
| Implicit return | Requires explicit `return` keyword | Supported for single line expressions |

```javascript
const obj = {
  name: "Metrics",
  // Regular function: 'this' points to obj
  regular() {
    setTimeout(function() {
      console.log(this.name); // undefined (this is window/global)
    }, 100);
  },
  // Arrow function: inherits 'this' from surrounding lexical context
  arrow() {
    setTimeout(() => {
      console.log(this.name); // "Metrics"
    }, 100);
  }
};
```

---

## 7. `===` (Strict) vs `==` (Loose) Equality

- `==` performs type coercion before comparison.
- `===` compares both value and type without conversion.

```javascript
5 == "5";        // true  (string converts to number)
5 === "5";       // false (different types: number vs string)

0 == false;      // true
0 === false;     // false

null == undefined;  // true
null === undefined; // false
```

---

## 8. Why `value === undefined` is Better Than `!value`

`!value` checks for *falsiness*, which includes `0`, `""`, `false`, `null`, `NaN`, and `undefined`. Checking `value === undefined` specifically checks for unassigned values without breaking on legitimate falsy data.

```javascript
const itemCount = 0;

// BAD / RISKY: 0 is falsy, triggers default unexpected behavior
if (!itemCount) {
  console.log("No items!"); // Executes even though itemCount is valid 0!
}

// GOOD: Explicit check for undefined
if (itemCount === undefined) {
  console.log("Value was never provided!"); // Does not execute
}
```

---

## 9. Array Utility Methods Chaining

Combining high-order array methods (`filter`, `map`, `reduce`, etc.) sequentially to transform data cleanly.

```javascript
const products = [
  { name: "Laptop", category: "tech", price: 1000, inStock: true },
  { name: "Phone", category: "tech", price: 500, inStock: false },
  { name: "Shirt", category: "apparel", price: 40, inStock: true },
  { name: "Monitor", category: "tech", price: 300, inStock: true }
];

// Goal: Get total price of in-stock tech items with a 10% discount applied
const totalTechCost = products
  .filter(p => p.category === "tech" && p.inStock)
  .map(p => p.price * 0.9)
  .reduce((sum, price) => sum + price, 0);

console.log(totalTechCost); // 1000 * 0.9 + 300 * 0.9 = 1170
```

---

## 10. `null` vs `undefined`

- `undefined`: Variable has been declared but has not yet been assigned a value (JS default).
- `null`: Explicit assignment representing intentional absence of any object value.

```javascript
let x; 
console.log(x);        // undefined (uninitialized)
console.log(typeof x); // "undefined"

let y = null; 
console.log(y);        // null (explicit empty state)
console.log(typeof y); // "object" (historical JS bug, but standard)
```

---

## 11. CommonJS Modules (`require` & `module.exports`)

Node.js module system for exporting code from one file and importing it into another.

```javascript
// --- mathUtils.js ---
const add = (a, b) => a + b;
const multiply = (a, b) => a * b;

module.exports = {
  add,
  multiply
};

// --- app.js ---
const { add, multiply } = require("./mathUtils");

console.log(add(2, 3));      // 5
console.log(multiply(4, 5)); // 20
```

---

## 12. Console Methods

Different logging utilities for debugging and structured output.

```javascript
// Output messages
console.log("Standard log statement");
console.info("Informational message");
console.warn("Warning alert");
console.error("Critical failure log");

// Tabular data visualizer
const users = [{ id: 1, name: "Alice" }, { id: 2, name: "Bob" }];
console.table(users);

// Timing operations
console.time("DB Query");
// simulate async work...
console.timeEnd("DB Query"); // Prints elapsed time in ms

// Grouping logs
console.group("User Details");
console.log("Name: John");
console.log("Role: Admin");
console.groupEnd();
```

---

## 13. Clean Code Best Practices

### Indentation & Formatting
- Standard 2-space indentation. Keep formatting consistent across files.

### Variable Naming
- Use camelCase for variables/functions: `totalCount`, `getUserData()`.
- Use UPPER_SNAKE_CASE for constants: `MAX_RETRIES`, `API_URL`.
- Use descriptive nouns for variables and verb phrases for functions.

```javascript
// BAD
const d = new Date();
const x = 50;
function data(u) { return u.status === 1; }

// GOOD
const currentDate = new Date();
const maxItemsPerPage = 50;
function isUserActive(user) { return user.status === 1; }
```

### Loop Variable Naming
- Avoid single letter variables like `i`, `j`, `k` unless dealing with simple matrix/index counters. Prefer domain nouns for items.

```javascript
// BAD
for (let i = 0; i < a.length; i++) {
  console.log(a[i]);
}

// GOOD
for (const item of items) {
  console.log(item);
}
```

---

## 14. First-Class & Higher-Order Functions (Callbacks)

Passing functions as arguments to other functions and executing them on demand.

```javascript
// Function taking another function as argument
function processUserInput(data, callback) {
  const formattedData = data.trim().toUpperCase();
  callback(formattedData);
}

// Callback implementation
const displayNotice = (message) => {
  console.log(`[ALERT]: ${message}`);
};

processUserInput("  hello world  ", displayNotice); 
// Output: [ALERT]: HELLO WORLD
```

---

## 15. Named vs Anonymous Functions

```javascript
// Named Function Statement (Hoisted, visible stack traces)
function calculateTotal(price, tax) {
  return price + tax;
}

// Anonymous Function (Assigned to variable / Expression)
const calculateTotalAnon = function(price, tax) {
  return price + tax;
};

// Anonymous Inline Callback (e.g. array iteration)
const nums = [1, 2, 3];
nums.map(function(num) {
  return num * 2;
});

// Equivalent with Anonymous Arrow Function
nums.map(num => num * 2);
```

---

## 16. Variable Number of Arguments

Handling arbitrary numbers of function arguments.

### Modern Approach: Rest Parameters (`...`)
```javascript
function calculateSum(initial, ...numbers) {
  return numbers.reduce((acc, curr) => acc + curr, initial);
}

console.log(calculateSum(10, 1, 2, 3, 4)); // 20
```

### Legacy Approach: `arguments` object (Regular functions only)
```javascript
function legacySum() {
  const argsArray = Array.from(arguments);
  return argsArray.reduce((acc, curr) => acc + curr, 0);
}

console.log(legacySum(5, 10, 15)); // 30
```

---

## 17. Debugging Strategies

1. **Strategic Logging:** Use `console.table()` for array objects, `console.dir()` to inspect object structures, and `console.trace()` to print execution call stacks.
2. **`debugger` Statement:** Insert `debugger;` into code to trigger an automatic breakpoint when DevTools/debugger is active.
3. **Browser DevTools Breakpoints:**
   - **Line Breakpoints:** Click line numbers in sources tab to halt execution.
   - **Conditional Breakpoints:** Pause execution only when expression evaluates to `true` (e.g. `item.id === 404`).
   - **Event Listener / XHR Breakpoints:** Pause execution automatically on API requests or DOM mutations.
4. **Isolate Scope:** Test tricky logic in standalone functions or isolated test cases away from UI state.
