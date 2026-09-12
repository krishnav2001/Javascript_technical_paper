# Different Data Types in JavaScript

JavaScript has **8 data types**. They are divided into:

1. **Primitive Data Types**-store single, immutable values directly by value.
2. **Non-Primitive (Reference) Data Types**-store mutable collections of data as references to memory locations.

---

# 1. Primitive Data Types

## 1. String
Used to store text.

```js
let name = "krish";
console.log(typeof name); // string
```

---

## 2. Number
Used to store integers and decimal numbers.

```js
let age = 25;
let price = 99.99;

console.log(typeof age); // number
```

---

## 3. BigInt
Used to store very large numbers.

```js
let bigNumber = 12345678901234567890n;
console.log(typeof bigNumber); // bigint
```

---

## 4. Boolean
Represents `true` or `false`.

```js
let isLoggedIn = true;
console.log(typeof isLoggedIn); // boolean
```

---

## 5. Undefined
A variable declared but not assigned a value.

```js
let city;
console.log(city); // undefined
console.log(typeof city); // undefined
```

---

## 6. Null
Represents an intentional empty value.

```js
let user = null;
console.log(user); // null
console.log(typeof user); // object (JavaScript bug)
```

---

## 7. Symbol
Used to create unique identifiers.

```js
let id = Symbol("id");
console.log(typeof id); // symbol
```

---

# 2. Non-Primitive (Reference) Data Type

## 8. Object
Used to store collections of data.

```js
let person = {
  name: "krish",
  age: 22
};

console.log(typeof person); // object
```

### Array
Arrays are also objects.

```js
let numbers = [1, 2, 3];
console.log(typeof numbers); // object
```

### Function
Functions are also objects.

```js
function greet() {
  console.log("Hello");
}

console.log(typeof greet); // function
```

---

# Quick Summary Table

| Data Type | Example |
|------------|----------|
| String | `"Hello"` |
| Number | `10`, `5.5` |
| BigInt | `123n` |
| Boolean | `true`, `false` |
| Undefined | `let x;` |
| Null | `null` |
| Symbol | `Symbol()` |
| Object | `{}`, `[]`, `function(){}` |
