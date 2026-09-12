# Popular JavaScript String Utility Methods

> **Important:** Strings in JavaScript are **immutable**.  
This means string methods **do not modify the original string**.  
They return a **new string** instead.

```js
let str = "Hello";

str.toUpperCase();

console.log(str); // "Hello" (original unchanged)
```

---

# 1. `length`

Returns the number of characters in a string.

### Mutable or Immutable**Immutable** (does not modify original string)

```js
const str = "JavaScript";

console.log(str.length); // 10
```

---

# 2. `toUpperCase()`

Converts string to uppercase.

### Mutable or Immutable**Immutable**

```js
const str = "hello";

const result = str.toUpperCase();

console.log(result); // "HELLO"
console.log(str); // "hello"
```

---

# 3. `toLowerCase()`

Converts string to lowercase.

### Mutable or Immutable**Immutable**

```js
const str = "HELLO";

console.log(str.toLowerCase()); // "hello"
```

---

# 4. `trim()`

Removes spaces from both ends.

### Mutable or Immutable**Immutable**

```js
const str = "   Hello World   ";

console.log(str.trim());
// "Hello World"
```

---

# 5. `trimStart()`

Removes spaces from the beginning.

### Mutable or Immutable**Immutable**

```js
const str = "   Hello";

console.log(str.trimStart());
// "Hello"
```

---

# 6. `trimEnd()`

Removes spaces from the end.

### Mutable or Immutable**Immutable**

```js
const str = "Hello   ";

console.log(str.trimEnd());
// "Hello"
```

---

# 7. `includes()`

Checks if substring exists.

### Mutable or Immutable**Immutable**

```js
const str = "JavaScript";

console.log(str.includes("Script")); // true
console.log(str.includes("Python")); // false
```

---

# 8. `startsWith()`

Checks if string starts with given text.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.startsWith("Java")); // true
```

---

# 9. `endsWith()`

Checks if string ends with given text.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.endsWith("Script")); // true
```

---

# 10. `indexOf()`

Returns first index of substring.

Returns `-1` if not found.

### Mutable or Immutable?
**Immutable**

```js
const str = "banana";

console.log(str.indexOf("a")); // 1
console.log(str.indexOf("z")); // -1
```

---

# 11. `lastIndexOf()`

Returns last occurrence index.

### Mutable or Immutable?
**Immutable**

```js
const str = "banana";

console.log(str.lastIndexOf("a")); // 5
```

---

# 12. `slice()`

Extracts part of string.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.slice(0, 4)); // "Java"
console.log(str.slice(-6)); // "Script"
```

---

# 13. `substring()`

Extracts characters between indexes.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.substring(0, 4));
// "Java"
```

---

# 14. `replace()`

Replaces first matching value.

### Mutable or Immutable?
**Immutable**

```js
const str = "Hello World";

console.log(str.replace("World", "JS"));
// "Hello JS"
```

---

# 15. `replaceAll()`

Replaces all matching values.

### Mutable or Immutable?
**Immutable**

```js
const str = "apple apple apple";

console.log(str.replaceAll("apple", "orange"));
// "orange orange orange"
```

---

# 16. `split()`

Converts string into array.

### Mutable or Immutable?
**Immutable**

```js
const str = "apple,banana,mango";

console.log(str.split(","));
// ["apple", "banana", "mango"]
```

---

# 17. `concat()`

Joins strings together.

### Mutable or Immutable?
**Immutable**

```js
const firstName = "krish";
const lastName = " verma";

console.log(firstName.concat(lastName));
// "Krish verma"
```

---

# 18. `repeat()`

Repeats string multiple times.

### Mutable or Immutable?
**Immutable**

```js
const str = "Hi ";

console.log(str.repeat(3));
// "Hi Hi Hi "
```

---

# 19. `charAt()`

Returns character at index.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.charAt(0));
// "J"
```

---

# 20. `charCodeAt()`

Returns Unicode value of character.

### Mutable or Immutable?
**Immutable**

```js
const str = "A";

console.log(str.charCodeAt(0));
// 65
```

---

# 21. `at()`

Gets character using positive or negative index.

### Mutable or Immutable?
**Immutable**

```js
const str = "JavaScript";

console.log(str.at(0)); // J
console.log(str.at(-1)); // t
```

---

# 22. `match()`

Searches using regex.

### Mutable or Immutable?
**Immutable**

```js
const str = "hello123";

console.log(str.match(/[0-9]/g));
// ["1", "2", "3"]
```

---

# 23. `search()`

Returns index of regex match.

### Mutable or Immutable?
**Immutable**

```js
const str = "hello123";

console.log(str.search(/[0-9]/));
// 5
```

---

# 24. `padStart()`

Pads beginning of string.

### Mutable or Immutable?
**Immutable**

```js
const str = "5";

console.log(str.padStart(3, "0"));
// "005"
```

---

# 25. `padEnd()`

Pads end of string.

### Mutable or Immutable**Immutable**

```js
const str = "5";

console.log(str.padEnd(3, "0"));
// "500"
```

---

# Summary

| Method | Purpose | Mutable/Immutable |
|--------|----------|-------------------|
| `toUpperCase()` | Uppercase | Immutable |
| `toLowerCase()` | Lowercase | Immutable |
| `trim()` | Remove spaces | Immutable |
| `includes()` | Check substring | Immutable |
| `slice()` | Extract string | Immutable |
| `replace()` | Replace text | Immutable |
| `split()` | Convert to array | Immutable |
| `repeat()` | Repeat string | Immutable |

## Final Note

✅ **All String methods are immutable in JavaScript** because **strings themselves are immutable**.
