# Error Handling in JavaScript (`try...catch`)

Error handling is used to **prevent application crashes** when something goes wrong.

JavaScript provides:

```js
try...catch
```

to handle errors safely.


when code may fail:

- API responses
- JSON parsing
- User input validation
- File operations
- Custom validation

This prevents your application from crashing.

---

# Why Use Error Handling?

Without error handling, an error can stop program execution.

### Example Without `try...catch`

```js
console.log("Start");

JSON.parse("{invalid json}");

console.log("End");
```

### Output

```txt
Start
SyntaxError
```

`"End"` never runs because the app crashes.

---

# Basic Syntax

```js
try {
  // risky code
} catch (error) {
  // handle error
}
```

---

# Example 1: Basic `try...catch`

```js
try {
  console.log(a);
} catch (error) {
  console.log("Something went wrong");
}
```

### Output

```txt
Something went wrong
```

Instead of crashing, the error is handled.

---

# How It Works

### `try`

Contains code that may fail.

```js
try {
  riskyCode();
}
```

---

### `catch`

Runs if an error occurs.

```js
catch (error) {
  console.log(error);
}
```

---

# Example 2: Access Error Object

```js
try {
  console.log(a);
} catch (error) {
  console.log(error);
}
```

### Output

```txt
ReferenceError: a is not defined
```

The `error` object contains details.

---

## Common Error Properties

### `error.message`

Gets error message.

```js
try {
  JSON.parse("{bad json}");
} catch (error) {
  console.log(error.message);
}
```

### Output

```txt
Unexpected token b in JSON
```

---

### `error.name`

Gets error type.

```js
try {
  console.log(a);
} catch (error) {
  console.log(error.name);
}
```

### Output

```txt
ReferenceError
```

---

# Example 3: Invalid JSON

```js
const json = "{name: 'Krish'}";

try {
  const data = JSON.parse(json);

  console.log(data);
} catch (error) {
  console.log("Invalid JSON");
}
```

### Output

```txt
Invalid JSON
```

---

# Example 4: Custom Error Message

```js
try {
  const age = -10;

  if (age < 0) {
    throw new Error(
      "Age cannot be negative"
    );
  }
} catch (error) {
  console.log(error.message);
}
```

### Output

```txt
Age cannot be negative
```

---

# `throw`

Used to create custom errors.

### Syntax

```js
throw new Error("Message");
```

### Example

```js
function divide(a, b) {
  if (b === 0) {
    throw new Error(
      "Cannot divide by zero"
    );
  }

  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.log(error.message);
}
```

### Output

```txt
Cannot divide by zero
```

---

# `finally`

Runs **always**, whether error happens or not.

### Syntax

```js
try {
} catch (error) {
} finally {
}
```

---

# Example

```js
try {
  console.log("Inside try");
} catch (error) {
  console.log("Error");
} finally {
  console.log("Always runs");
}
```

### Output

```txt
Inside try
Always runs
```

---

## Example With Error

```js
try {
  console.log(a);
} catch (error) {
  console.log("Error happened");
} finally {
  console.log("Done");
}
```

### Output

```txt
Error happened
Done
```

---

# Common Error Types

## `ReferenceError`

Variable not defined.

```js
console.log(x);
```

---

## `SyntaxError`

Invalid syntax.

```js
JSON.parse("{bad json}");
```

---

## `TypeError`

Wrong operation on data type.

```js
null.name;
```

---

## `RangeError`

Value out of allowed range.

```js
new Array(-1);
```

---

# Nested `try...catch`

```js
try {
  try {
    console.log(a);
  } catch (error) {
    console.log("Inner catch");
  }
} catch (error) {
  console.log("Outer catch");
}
```

### Output

```txt
Inner catch
```

---

# Real World Example

### API Data Parsing

```js
const response = `{
  "name": "Krish"
}`;

try {
  const data = JSON.parse(
    response
  );

  console.log(data.name);
} catch (error) {
  console.log(
    "Failed to parse data"
  );
}
```

---

# Important Notes

## `try...catch` only catches runtime errors

Wrong:

```js
try {
  function () {}
}
```

This causes syntax error before execution.

---

## Avoid Empty Catch

Bad:

```js
try {
  riskyCode();
} catch (error) {}
```

You lose debugging information.

Better:

```js
catch (error) {
  console.log(error.message);
}
```

---

# Quick Summary

| Keyword | Purpose |
|----------|----------|
| `try` | Code that may fail |
| `catch` | Handle error |
| `throw` | Create custom error |
| `finally` | Always runs |

---
# Flow

```txt
try
   ↓
Error?
 ├── No → continue
 └── Yes → catch
           ↓
        finally
```
