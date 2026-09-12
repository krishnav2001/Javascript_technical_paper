# Pass by Value vs Pass by Reference in JavaScript

When values are passed to variables or functions, JavaScript handles them in two ways:

1. **Pass by Value**
2. **Pass by Reference** (more accurately: reference value sharing)

Understanding this helps explain why some values change and others don't.

---

# 1. Pass by Value

In **pass by value**, a **copy of the value** is passed.

Changing one variable does **not affect** the other.

Usually happens with **primitive data types**:

- `number`
- `string`
- `boolean`
- `null`
- `undefined`
- `symbol`
- `bigint`

---

## Example with Number

```js
let a = 10;
let b = a;

b = 20;

console.log(a);
// 10

console.log(b);
// 20
```

### Why?

`b` gets a **copy** of `a`.

```txt
a → 10
b → 10 (copy)
```

After:

```js
b = 20;
```

Only `b` changes.

---

## Example with String

```js
let firstName = "Krish";
let secondName = firstName;

secondName = "John";

console.log(firstName);
// Krish

console.log(secondName);
// John
```

Because strings are primitive values.

---

## Example in Function

```js
function updateAge(age) {
  age = 30;
}

let userAge = 22;

updateAge(userAge);

console.log(userAge);
// 22
```

### Why?

A copy is passed.

```txt
userAge → 22
age → copy of 22
```

Changing `age` does not affect `userAge`.

---

# 2. Pass by Reference

For **objects and arrays**, JavaScript passes a **reference to memory**.

Both variables point to the **same object**.

Usually happens with:

- Objects
- Arrays
- Functions

---

## Example with Object

```js
const user1 = {
  name: "Krish",
};

const user2 = user1;

user2.name = "John";

console.log(user1.name);
// John

console.log(user2.name);
// John
```

### Why?

Both point to the same memory location.

```txt
user1 ──► { name: "Krish" }
user2 ──► same object
```

After:

```js
user2.name = "John";
```

The original object changes.

---

## Example with Array

```js
const arr1 = [1, 2, 3];

const arr2 = arr1;

arr2.push(4);

console.log(arr1);
// [1, 2, 3, 4]

console.log(arr2);
// [1, 2, 3, 4]
```

Both variables reference the same array.

---

## Example in Function

```js
function updateUser(user) {
  user.name = "John";
}

const person = {
  name: "Krish",
};

updateUser(person);

console.log(person.name);
// John
```

### Why?

The function receives the object reference.

So changes affect the original object.

---

# 3. Important Confusion

JavaScript is technically:

```txt
Pass by Value
```

Even for objects.

But for objects, the **value itself is a reference**.

This is called:

```txt
Reference Value Sharing
```

Example:

```js
const obj1 = {
  name: "John",
};

const obj2 = obj1;
```

JavaScript copies the **reference value**, not the whole object.

---

# 4. Reassigning vs Modifying

These behave differently.

## Modifying Object

Changes original object.

```js
function update(user) {
  user.name = "David";
}

const person = {
  name: "John",
};

update(person);

console.log(person.name);
// David
```

---

## Reassigning Object

Does not change original object.

```js
function update(user) {
  user = {
    name: "David",
  };
}

const person = {
  name: "John",
};

update(person);

console.log(person.name);
// John
```

### Why?

You changed the local reference only.

---

# 5. Avoid Shared Mutation (Copy Objects)

Use spread operator.

```js
const user1 = {
  name: "Krish",
};

const user2 = {
  ...user1,
};

user2.name = "John";

console.log(user1.name);
// Krish

console.log(user2.name);
// John
```

Now they are separate objects.

---

# Memory Visualization

## Primitive (Pass by Value)

```txt
a → 10
b → copy of 10
```

Independent values.

---

## Object (Reference Sharing)

```txt
obj1 ──► memory object
obj2 ──► same memory object
```

Shared object.

---

# Quick Summary

| Type | Behavior |
|------|-----------|
| Number | Pass by value |
| String | Pass by value |
| Boolean | Pass by value |
| Object | Reference sharing |
| Array | Reference sharing |
| Function | Reference sharing |

---

# Easy Rule to Remember

## Primitive Types

```txt
Copy value
```

No effect on original.

---

## Objects / Arrays

```txt
Copy reference
```

Changes may affect original.

---

# Final Rule

### Primitive Types

```js
let a = 10;
let b = a;
```

A **copy** is created.

---

### Objects / Arrays

```js
const a = {};
const b = a;
```

Both point to the **same object in memory**.
