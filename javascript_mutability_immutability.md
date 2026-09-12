# Mutable vs Immutable Methods in JavaScript

## What is Mutable?

A **mutable method changes the original data**.

```js
const arr = [1, 2, 3];

arr.push(4);

console.log(arr);
// [1, 2, 3, 4]
```

Here, `push()` changes the original array.

---

## What is Immutable?

An **immutable method does not change the original data**.

Instead, it returns a **new value**.

```js
const arr = [1, 2, 3];

const newArr = arr.concat(4);

console.log(newArr);
// [1, 2, 3, 4]

console.log(arr);
// [1, 2, 3]
```

Here, `concat()` returns a new array.

---

# 1. Array Mutable Methods

These methods **modify the original array**.

| Method | Purpose |
|--------|----------|
| `push()` | Add item at end |
| `pop()` | Remove last item |
| `shift()` | Remove first item |
| `unshift()` | Add item at start |
| `splice()` | Add/remove items |
| `sort()` | Sort array |
| `reverse()` | Reverse array |
| `fill()` | Fill array with value |
| `copyWithin()` | Copy part of array |
| `push()` | Add element |
| `delete` | Remove element (not recommended) |

### Example: `push()`

```js
const arr = [1, 2];

arr.push(3);

console.log(arr);
// [1, 2, 3]
```

---

### Example: `splice()`

```js
const arr = [1, 2, 3, 4];

arr.splice(1, 2);

console.log(arr);
// [1, 4]
```

---

### Example: `sort()`

```js
const numbers = [40, 10, 100];

numbers.sort((a, b) => a - b);

console.log(numbers);
// [10, 40, 100]
```

---

# 2. Array Immutable Methods

These methods **do not modify the original array**.

| Method | Purpose |
|--------|----------|
| `map()` | Transform items |
| `filter()` | Select items |
| `reduce()` | Single value |
| `slice()` | Copy part |
| `concat()` | Merge arrays |
| `find()` | Find first item |
| `findIndex()` | Find index |
| `includes()` | Check existence |
| `indexOf()` | Find index |
| `every()` | Check all |
| `some()` | Check some |
| `flat()` | Flatten array |
| `flatMap()` | Map + flatten |
| `join()` | Convert to string |
| `toSorted()` | Immutable sort |
| `toReversed()` | Immutable reverse |
| `toSpliced()` | Immutable splice |
| `with()` | Replace value immutably |

### Example: `map()`

```js
const arr = [1, 2, 3];

const doubled = arr.map(
  (num) => num * 2
);

console.log(doubled);
// [2, 4, 6]

console.log(arr);
// [1, 2, 3]
```

---

### Example: `filter()`

```js
const arr = [10, 20, 30];

const result = arr.filter(
  (num) => num > 15
);

console.log(result);
// [20, 30]

console.log(arr);
// unchanged
```

---

### Example: `slice()`

```js
const arr = [1, 2, 3, 4];

const result = arr.slice(1, 3);

console.log(result);
// [2, 3]

console.log(arr);
// [1, 2, 3, 4]
```

---

# 3. String Methods

Strings are **immutable in JavaScript**.

That means **all string methods are immutable**.

```js
let str = "hello";

str.toUpperCase();

console.log(str);
// "hello"
```

## Common Immutable String Methods

| Method |
|---------|
| `toUpperCase()` |
| `toLowerCase()` |
| `trim()` |
| `slice()` |
| `substring()` |
| `replace()` |
| `replaceAll()` |
| `split()` |
| `concat()` |
| `includes()` |
| `startsWith()` |
| `endsWith()` |

---

# 4. Object Methods

Objects themselves are **mutable**, but utility methods may or may not mutate.

## Mutable Object Methods

| Method |
|---------|
| `Object.assign(target, source)` |
| `Object.defineProperty()` |
| `Object.defineProperties()` |
| `Object.setPrototypeOf()` |
| `delete` |

### Example

```js
const obj = {
  name: "John",
};

delete obj.name;

console.log(obj);
// {}
```

---

## Immutable Object Methods

| Method |
|---------|
| `Object.keys()` |
| `Object.values()` |
| `Object.entries()` |
| `Object.fromEntries()` |
| `Object.hasOwn()` |
| `Object.getOwnPropertyNames()` |
| `Object.getPrototypeOf()` |

### Example

```js
const user = {
  name: "John",
  age: 20,
};

console.log(Object.keys(user));
// ["name", "age"]

console.log(user);
// unchanged
```

---

# Easy Way to Remember

## Mutable

Changes original data

```txt
Original → Modified
```

Example:

```js
arr.push()
arr.splice()
arr.sort()
```

---

## Immutable

Returns new data

```txt
Original → New Copy
```

Example:

```js
arr.map()
arr.filter()
arr.slice()
```

---

# Quick Summary

| Type | Mutable | Immutable |
|------|----------|------------|
| Array | `push()`, `splice()`, `sort()` | `map()`, `filter()`, `slice()` |
| String | None | All methods |
| Object | `delete`, `assign()` | `keys()`, `values()` |

## Final Rule

If the **original data changes**, it is **mutable**.

If the **original data stays same**, it is **immutable**.
