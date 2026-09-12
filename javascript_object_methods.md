# Popular JavaScript Object Utility Methods

> **Important:**  
Objects in JavaScript are **mutable**, meaning their properties can be changed after creation.

```js
const person = {
  name: "John",
};

person.name = "David";

console.log(person);
// { name: "David" }
```

However, some object utility methods **do not mutate** the original object and instead return a **new value/object**.

---

# 1. `Object.keys()`

Returns an array of object keys.

### Mutable or Immutable?
**Immutable** (does not modify original object)

```js
const user = {
  name: "Krish",
  age: 22,
};

console.log(Object.keys(user));
// ["name", "age"]

console.log(user);
// unchanged
```

---

# 2. `Object.values()`

Returns an array of object values.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
  age: 22,
};

console.log(Object.values(user));
// ["Krish", 22]
```

---

# 3. `Object.entries()`

Converts object into key-value pair array.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
  age: 22,
};

console.log(Object.entries(user));

/*
[
  ["name", "Krish"],
  ["age", 22]
]
*/
```

---

# 4. `Object.fromEntries()`

Converts key-value pair array back into object.

### Mutable or Immutable?
**Immutable**

```js
const entries = [
  ["name", "Krish"],
  ["age", 22],
];

console.log(Object.fromEntries(entries));

/*
{
  name: "Krish",
  age: 22
}
*/
```

---

# 5. `Object.assign()`

Copies properties from source object(s).

### Mutable or Immutable?
**Mutable** (modifies target object)

```js
const obj1 = {
  a: 1,
};

const obj2 = {
  b: 2,
};

Object.assign(obj1, obj2);

console.log(obj1);
// { a: 1, b: 2 }
```

### Immutable Way

```js
const obj1 = {
  a: 1,
};

const obj2 = {
  b: 2,
};

const merged = Object.assign({}, obj1, obj2);

console.log(merged);
// { a: 1, b: 2 }
```

---

# 6. `Object.freeze()`

Prevents object modification.

### Mutable or Immutable?
**Makes object immutable**

```js
const user = {
  name: "Krish",
};

Object.freeze(user);

user.name = "John";

console.log(user);
// { name: "Krish" }
```

---

# 7. `Object.seal()`

Allows modification of existing properties but prevents adding/removing keys.

### Mutable or Immutable?
**Partially Mutable**

```js
const user = {
  name: "Krish",
};

Object.seal(user);

user.name = "John"; // allowed
user.age = 22; // not allowed

console.log(user);
// { name: "John" }
```

---

# 8. `Object.hasOwn()`

Checks whether key exists directly in object.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
};

console.log(Object.hasOwn(user, "name"));
// true

console.log(Object.hasOwn(user, "age"));
// false
```

---

# 9. `hasOwnProperty()`

Checks if property exists.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
};

console.log(user.hasOwnProperty("name"));
// true
```

---

# 10. `Object.create()`

Creates a new object using another object as prototype.

### Mutable or Immutable?
**Immutable** (doesn't modify original object)

```js
const person = {
  greet() {
    console.log("Hello");
  },
};

const user = Object.create(person);

user.name = "Krish";

console.log(user.name);
// Krish

user.greet();
// Hello
```

---

# 11. `Object.is()`

Checks whether two values are exactly same.

### Mutable or Immutable?
**Immutable**

```js
console.log(Object.is(5, 5));
// true

console.log(Object.is(NaN, NaN));
// true
```

---

# 12. `Object.getOwnPropertyNames()`

Returns all property names.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
  age: 22,
};

console.log(Object.getOwnPropertyNames(user));
// ["name", "age"]
```

---

# 13. `Object.getOwnPropertyDescriptors()`

Returns detailed property information.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
};

console.log(
  Object.getOwnPropertyDescriptors(user)
);
```

---

# 14. `Object.defineProperty()`

Defines or modifies property.

### Mutable or Immutable?
**Mutable**

```js
const user = {};

Object.defineProperty(user, "name", {
  value: "Krish",
  writable: false,
});

console.log(user);
// { name: "Krish" }
```

---

# 15. `Object.defineProperties()`

Defines multiple properties.

### Mutable or Immutable?
**Mutable**

```js
const user = {};

Object.defineProperties(user, {
  name: {
    value: "Krish",
  },
  age: {
    value: 22,
  },
});

console.log(user);
```

---

# 16. `Object.getPrototypeOf()`

Returns prototype of object.

### Mutable or Immutable?
**Immutable**

```js
const arr = [];

console.log(Object.getPrototypeOf(arr));
```

---

# 17. `Object.setPrototypeOf()`

Changes prototype.

### Mutable or Immutable?
**Mutable**

```js
const animal = {
  sound: "meow",
};

const cat = {};

Object.setPrototypeOf(cat, animal);

console.log(cat.sound);
// meow
```

---

# 18. `Object.preventExtensions()`

Prevents adding new properties.

### Mutable or Immutable?
**Partially Mutable**

```js
const user = {
  name: "Krish",
};

Object.preventExtensions(user);

user.age = 22;

console.log(user);
// { name: "Krish" }
```

---

# 19. `delete`

Removes property from object.

### Mutable or Immutable?
**Mutable**

```js
const user = {
  name: "Krish",
  age: 22,
};

delete user.age;

console.log(user);
// { name: "Krish" }
```

---

# 20. Spread Operator (`...`)

Used for object copying/merging.

### Mutable or Immutable?
**Immutable**

```js
const user = {
  name: "Krish",
};

const updatedUser = {
  ...user,
  age: 22,
};

console.log(updatedUser);
// { name: "Krish", age: 22 }

console.log(user);
// unchanged
```

---

# Summary

| Method | Purpose | Mutable/Immutable |
|--------|----------|-------------------|
| `Object.keys()` | Get keys | Immutable |
| `Object.values()` | Get values | Immutable |
| `Object.entries()` | Object → Array | Immutable |
| `Object.fromEntries()` | Array → Object | Immutable |
| `Object.assign()` | Merge objects | Mutable |
| `Object.freeze()` | Prevent changes | Immutable |
| `Object.seal()` | Restrict changes | Partially Mutable |
| `Object.hasOwn()` | Check key | Immutable |
| `Object.create()` | Create object | Immutable |
| `delete` | Remove property | Mutable |
| `...` spread | Copy object | Immutable |

## Final Note

Objects are **mutable** in JavaScript, but many utility methods are **immutable** and return a **new value/object** instead of changing the original object.
