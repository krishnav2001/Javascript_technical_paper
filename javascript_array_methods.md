# Popular JavaScript Array Utility Methods

> **Important:**  
Arrays in JavaScript are **mutable**, meaning they can be changed after creation.

```js
const arr = [1, 2, 3];

arr.push(4);

console.log(arr);
// [1, 2, 3, 4]
```

Some methods modify the original array (**mutable**) while others return a new array/value (**immutable**).

---

# Basics

# 1. `push()`

Adds item(s) to the end of array.

### Mutable or Immutable?
**Mutable**

```js
const arr = [1, 2];

arr.push(3);

console.log(arr);
// [1, 2, 3]
```

---

# 2. `pop()`

Removes last item.

### Mutable or Immutable?
**Mutable**

```js
const arr = [1, 2, 3];

arr.pop();

console.log(arr);
// [1, 2]
```

---

# 3. `concat()`

Combines arrays.

### Mutable or Immutable?
**Immutable**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];

const result = arr1.concat(arr2);

console.log(result);
// [1, 2, 3, 4]

console.log(arr1);
// unchanged
```

---

# 4. `slice()`

Returns part of array.

### Mutable or Immutable?
**Immutable**

```js
const arr = [10, 20, 30, 40];

const result = arr.slice(1, 3);

console.log(result);
// [20, 30]

console.log(arr);
// unchanged
```

---

# 5. `splice()`

Add/remove elements.

### Mutable or Immutable?
**Mutable**

### Remove Items

```js
const arr = [1, 2, 3, 4];

arr.splice(1, 2);

console.log(arr);
// [1, 4]
```

### Add Items

```js
const arr = [1, 2, 3];

arr.splice(1, 0, 100);

console.log(arr);
// [1, 100, 2, 3]
```

---

# 6. `join()`

Converts array to string.

### Mutable or Immutable?
**Immutable**

```js
const fruits = [
  "apple",
  "banana",
  "mango",
];

console.log(fruits.join(", "));
// apple, banana, mango
```

---

# 7. `flat()`

Flattens nested arrays.

### Mutable or Immutable?
**Immutable**

```js
const arr = [1, [2, 3], [4, [5]]];

console.log(arr.flat());
// [1, 2, 3, 4, [5]]
```

---

# Finding

# 8. `find()`

Returns first matching element.

### Mutable or Immutable?
**Immutable**

```js
const numbers = [10, 20, 30];

const result = numbers.find(
  (num) => num > 15
);

console.log(result);
// 20
```

---

# 9. `indexOf()`

Returns index of element.

### Mutable or Immutable?
**Immutable**

```js
const fruits = [
  "apple",
  "banana",
];

console.log(
  fruits.indexOf("banana")
);
// 1
```

---

# 10. `includes()`

Checks if value exists.

### Mutable or Immutable?
**Immutable**

```js
const arr = [1, 2, 3];

console.log(arr.includes(2));
// true

console.log(arr.includes(10));
// false
```

---

# 11. `findIndex()`

Returns index of matching element.

### Mutable or Immutable?
**Immutable**

```js
const numbers = [10, 20, 30];

const result = numbers.findIndex(
  (num) => num > 15
);

console.log(result);
// 1
```

---

# Higher Order Functions

# 12. `forEach()`

Runs function for every item.

### Mutable or Immutable?
**Immutable** (method itself)

```js
const fruits = [
  "apple",
  "banana",
];

fruits.forEach((fruit) => {
  console.log(fruit);
});
```

### Output

```txt
apple
banana
```

Returns:

```js
undefined
```

---

# 13. `filter()`

Returns matching items.

### Mutable or Immutable?
**Immutable**

```js
const numbers = [10, 20, 30];

const result = numbers.filter(
  (num) => num > 15
);

console.log(result);
// [20, 30]
```

---

# 14. `map()`

Transforms data.

### Mutable or Immutable?
**Immutable**

```js
const numbers = [1, 2, 3];

const doubled = numbers.map(
  (num) => num * 2
);

console.log(doubled);
// [2, 4, 6]
```

---

# 15. `reduce()`

Converts array into one value.

### Mutable or Immutable?
**Immutable**

```js
const numbers = [10, 20, 30];

const total = numbers.reduce(
  (acc, curr) => acc + curr,
  0
);

console.log(total);
// 60
```

---

# 16. `sort()`

Sorts array.

### Mutable or Immutable?
**Mutable**

### String Sort

```js
const fruits = [
  "banana",
  "apple",
];

fruits.sort();

console.log(fruits);
// ["apple", "banana"]
```

### Number Sort

```js
const numbers = [40, 5, 100];

numbers.sort((a, b) => a - b);

console.log(numbers);
// [5, 40, 100]
```

---

# Advanced

# 17. Method Chaining

Combining multiple methods together.

### Example

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter((num) => num > 2)
  .map((num) => num * 2);

console.log(result);
// [6, 8, 10]
```

### Step-by-step

First:

```js
.filter((num) => num > 2)
```

Result:

```js
[3, 4, 5]
```

Then:

```js
.map((num) => num * 2)
```

Final:

```js
[6, 8, 10]
```

---

## Real Example

```js
const users = [
  {
    name: "John",
    active: true,
  },
  {
    name: "David",
    active: false,
  },
  {
    name: "Mike",
    active: true,
  },
];

const activeNames = users
  .filter((user) => user.active)
  .map((user) => user.name);

console.log(activeNames);

// ["John", "Mike"]
```

---

# Mutable vs Immutable Summary

## Mutable Methods

These change original array.

```js
push()
pop()
splice()
sort()
```

---

## Immutable Methods

These return new array/value.

```js
concat()
slice()
join()
flat()
find()
indexOf()
includes()
findIndex()
forEach()
filter()
map()
reduce()
```

---

# Quick Summary Table

| Method | Purpose | Mutable/Immutable |
|--------|----------|-------------------|
| `push()` | Add end | Mutable |
| `pop()` | Remove end | Mutable |
| `concat()` | Merge arrays | Immutable |
| `slice()` | Copy part | Immutable |
| `splice()` | Add/remove | Mutable |
| `join()` | Array → String | Immutable |
| `flat()` | Flatten | Immutable |
| `find()` | Find element | Immutable |
| `indexOf()` | Find index | Immutable |
| `includes()` | Check value | Immutable |
| `findIndex()` | Find matching index | Immutable |
| `forEach()` | Loop | Immutable |
| `filter()` | Filter items | Immutable |
| `map()` | Transform | Immutable |
| `reduce()` | One value | Immutable |
| `sort()` | Sort | Mutable |
