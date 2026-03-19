---
title: Top 25 JavaScript Interview Questions and Answers (2026 Guide)
date: 2026-03-19 14:00:00 +0800
categories: [Frontend, JavaScript, Interview]
tags: [javascript, interview, frontend, js-basics, coding]
description: Top 25 JavaScript interview questions and answers for 2026. Covers closures, prototype chain, async/await, event loop, and must-know frontend concepts.
---

# Top 25 JavaScript Interview Questions and Answers (2026 Guide)

This article provides a comprehensive collection of **JavaScript interview questions and answers**, covering core fundamentals, advanced concepts, and real-world coding scenarios to help you prepare for frontend interviews.

---

## Table of Contents

1. var vs let vs const  
2. Closures  
3. Prototype Chain  
4. undefined vs null  
5. == vs ===  
6. Hoisting  
7. Arrow Functions  
8. this  
9. new keyword  
10. Promise  
11. async / await  
12. Event Loop  
13. Event Delegation  
14. Deep vs Shallow Copy  
15. Debounce & Throttle  
16. Currying  
17. Memory Leak  
18. Performance Optimization  
19. call / apply / bind  
20. for...in vs for...of  
21. Destructuring  
22. Array Methods  
23. Flatten Array  
24. Remove Duplicates  
25. Summary

---

## 1. What is the difference between `var`, `let`, and `const`?

### Key differences:

| Feature | var | let | const |
|------|-----|-----|------|
| Scope | Function | Block | Block |
| Hoisting | Yes | Yes (TDZ) | Yes (TDZ) |
| Reassignment | Yes | Yes | No |
| Redeclaration | Yes | No | No |

### Example:

```js
console.log(a); // undefined
var a = 1;


console.log(b); // ReferenceError
let b = 2;
```

---

## 2. What is a closure?

A **closure** is created when an inner function retains access to variables from its outer lexical scope, even after the outer function has already finished executing.

### Why closures matter

Closures are commonly used for:

- data encapsulation
- private state
- function factories
- callbacks and asynchronous logic

### Example

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

In this example, `count` is not destroyed after `createCounter()` runs, because the returned function still references it.

### Follow-up questions

- What are real-world use cases of closures?
- Can closures cause memory leaks?
- How would you implement private variables using closures?

### Common pitfall

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
// 3 3 3
```

Because `var` is function-scoped, all callbacks share the same `i`.

A correct version:

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 0);
}
// 0 1 2
```

---

## 3. What is the prototype chain?

In JavaScript, objects can inherit properties and methods from other objects through the **prototype chain**.

When you access a property on an object, JavaScript looks for it in this order:

1. the object itself
2. the object's prototype
3. the prototype's prototype
4. until `null`

### Example

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayName = function () {
  console.log(this.name);
};

const p = new Person("Harry");
p.sayName(); // Harry
```

### Relationship summary

```js
console.log(p.__proto__ === Person.prototype); // true
console.log(Person.prototype.__proto__ === Object.prototype); // true
console.log(Object.prototype.__proto__); // null
```

---

## 4. What is the difference between `undefined` and `null`?

Although both represent “empty” values, they mean different things.

| Type | Meaning |
|------|---------|
| `undefined` | A variable has been declared but not assigned a value |
| `null` | An intentional empty value |

### Example

```js
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null
```

### Typical interview point

```js
typeof undefined; // "undefined"
typeof null; // "object"
```

`typeof null === "object"` is a historical bug in JavaScript.

---

## 5. What is the difference between `==` and `===`?

- `==` performs type coercion before comparison
- `===` compares both value and type strictly

### Example

```js
console.log(1 == "1"); // true
console.log(1 === "1"); // false
console.log(0 == false); // true
console.log(0 === false); // false
```

### Recommendation

In real projects and interviews, prefer `===` and `!==` unless you clearly understand the coercion rules.

---

## 6. What is hoisting?

**Hoisting** means declarations are processed before code execution.

### With `var`

```js
console.log(a); // undefined
var a = 10;
```

JavaScript treats it roughly like this:

```js
var a;
console.log(a);
a = 10;
```

### With `let` and `const`

```js
console.log(b); // ReferenceError
let b = 20;
```

They are also hoisted, but they remain in the **temporal dead zone (TDZ)** until the declaration line is executed.

---

## 7. What is the difference between ordinary functions and arrow functions?

Arrow functions are shorter, but they also behave differently.

### Main differences

1. Arrow functions do not have their own `this`
2. Arrow functions do not have their own `arguments`
3. Arrow functions cannot be used as constructors
4. Arrow functions do not have `prototype`

### Example: `this`

```js
const obj = {
  name: "Harry",
  normal() {
    console.log(this.name);
  },
  arrow: () => {
    console.log(this.name);
  },
};

obj.normal(); // Harry
obj.arrow(); // usually undefined
```

---

## 8. How does `this` work in JavaScript?

The value of `this` depends on **how a function is called**, not where it is defined.

### Common rules

1. **Default binding**: in non-strict mode, `this` may point to the global object
2. **Implicit binding**: when called as an object method, `this` points to that object
3. **Explicit binding**: `call`, `apply`, `bind` can specify `this`
4. **Constructor binding**: inside `new`, `this` points to the new instance
5. **Arrow function**: `this` is lexically inherited from the outer scope

### Example

```js
function show() {
  console.log(this.name);
}

const obj = { name: "Harry" };
show.call(obj); // Harry
```

---

## 9. What happens when `new` is used?

When you use `new`, JavaScript performs these steps:

1. create a new empty object
2. set the new object's prototype to the constructor's `prototype`
3. bind `this` inside the constructor to that new object
4. return the object unless the constructor explicitly returns another object

### Example

```js
function Person(name) {
  this.name = name;
}

const p = new Person("Harry");
console.log(p.name); // Harry
```

---

## 10. What is a Promise?

A **Promise** represents the result of an asynchronous operation.

### States

- `pending`
- `fulfilled`
- `rejected`

### Example

```js
const p = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("success");
  }, 1000);
});

p.then((res) => {
  console.log(res); // success
});
```

### Key point

A Promise's state can change only once.

---

## 11. What is the difference between `Promise`, `async`, and `await`?

`async` / `await` is syntax sugar built on top of Promises.

### Promise style

```js
fetch("/api/user")
  .then((res) => res.json())
  .then((data) => {
    console.log(data);
  })
  .catch((err) => {
    console.error(err);
  });
```

### async / await style

```js
async function getUser() {
  try {
    const res = await fetch("/api/user");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

### Interview point

- `await` can only be used inside `async` functions, or at top level in environments that support top-level `await`
- `await` pauses the current async function, not the entire JavaScript thread

---

## 12. What is the Event Loop?

JavaScript is single-threaded, but it can still handle asynchronous tasks through the **Event Loop**.

### Simplified execution model

1. synchronous code enters the call stack
2. asynchronous callbacks are placed into queues later
3. once the call stack is empty, the event loop moves queued tasks back for execution

### Task priority

- **Microtasks**: `Promise.then`, `queueMicrotask`, `MutationObserver`
- **Macrotasks**: `setTimeout`, `setInterval`, DOM events, script execution

### Example

```js
console.log("start");

setTimeout(() => {
  console.log("timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("promise");
});

console.log("end");
```

### Output

```txt
start
end
promise
timeout
```

Because microtasks are executed before the next macrotask.

### Follow-up questions

- What is the difference between microtasks and macrotasks?
- Why does Promise run before setTimeout?
- What is queueMicrotask?

---

## 13. What is event delegation?

**Event delegation** means attaching an event listener to a parent element and handling child events through event bubbling.

### Benefits

- fewer event listeners
- better performance
- supports dynamically added child elements

### Example

```js
document.getElementById("list").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log(e.target.innerText);
  }
});
```

---

## 14. What is the difference between deep copy and shallow copy?

### Shallow copy

A shallow copy copies only the first level. Nested objects still share references.

```js
const obj = { a: 1, b: { c: 2 } };
const copy = { ...obj };

copy.b.c = 999;
console.log(obj.b.c); // 999
```

### Deep copy

A deep copy recursively copies nested data.

```js
const obj = { a: 1, b: { c: 2 } };
const deepCopy = structuredClone(obj);

deepCopy.b.c = 999;
console.log(obj.b.c); // 2
```

### Notes

`JSON.parse(JSON.stringify(obj))` can work in simple cases, but it has limitations:

- cannot preserve functions
- drops `undefined`
- cannot handle `Symbol`
- cannot handle circular references
- converts `Date` into strings

---

## 15. What are debounce and throttle?

Both are performance optimization techniques for frequent events such as scrolling, resizing, and input typing.

### Debounce

Debounce delays execution until the event stops firing for a specified time.

```js
function debounce(fn, delay) {
  let timer = null;

  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
}
```

### Throttle

Throttle ensures a function runs at most once within a specified interval.

```js
function throttle(fn, delay) {
  let lastTime = 0;

  return function (...args) {
    const now = Date.now();
    if (now - lastTime >= delay) {
      lastTime = now;
      fn.apply(this, args);
    }
  };
}
```

---

## 16. What is currying?

**Currying** transforms a function with multiple arguments into a sequence of functions that each take one argument.

### Example

```js
function add(a) {
  return function (b) {
    return a + b;
  };
}

console.log(add(1)(2)); // 3
```

### Benefit

Currying improves reusability and enables partial application.

---

## 17. What is a memory leak?

A **memory leak** happens when memory that is no longer needed cannot be released.

### Common causes

- global variables used carelessly
- uncleared timers
- uncleared event listeners
- closures retaining unnecessary references
- detached DOM nodes still being referenced

### Example

```js
const button = document.getElementById("btn");

function handleClick() {
  console.log("clicked");
}

button.addEventListener("click", handleClick);

// later, when no longer needed:
button.removeEventListener("click", handleClick);
```

---

## 18. How can JavaScript performance be optimized?

Common optimization ideas:

1. reduce unnecessary DOM operations
2. use debounce and throttle for high-frequency events
3. avoid repeated reflows and repaints
4. lazy load images and modules
5. use code splitting
6. cache repeated computations
7. avoid creating too many large objects unnecessarily
8. choose appropriate data structures and algorithms

---

## 19. What are `call`, `apply`, and `bind`?

All three are used to explicitly set `this`.

### `call`

Passes arguments one by one.

```js
function greet(city) {
  console.log(this.name, city);
}

const obj = { name: "Harry" };
greet.call(obj, "Beijing");
```

### `apply`

Passes arguments as an array.

```js
greet.apply(obj, ["Beijing"]);
```

### `bind`

Returns a new function with bound `this`.

```js
const boundGreet = greet.bind(obj, "Beijing");
boundGreet();
```

---

## 20. What is the difference between `for...in` and `for...of`?

### `for...in`

Used to iterate over enumerable property keys, usually for objects.

```js
const obj = { a: 1, b: 2 };

for (const key in obj) {
  console.log(key, obj[key]);
}
```

### `for...of`

Used to iterate over iterable values, such as arrays, strings, maps, and sets.

```js
const arr = [10, 20, 30];

for (const value of arr) {
  console.log(value);
}
```

---

## 21. What is destructuring?

Destructuring allows values to be extracted from arrays or objects more conveniently.

### Array destructuring

```js
const arr = [1, 2, 3];
const [a, b] = arr;
console.log(a, b); // 1 2
```

### Object destructuring

```js
const user = { name: "Harry", age: 28 };
const { name, age } = user;
console.log(name, age);
```

---

## 22. What are the common array methods?

### Mutating methods

- `push`
- `pop`
- `shift`
- `unshift`
- `splice`
- `sort`
- `reverse`

### Non-mutating methods

- `map`
- `filter`
- `reduce`
- `slice`
- `concat`
- `find`
- `some`
- `every`
- `includes`

### Example

```js
const arr = [1, 2, 3, 4];
const result = arr
  .filter((n) => n % 2 === 0)
  .map((n) => n * 10);

console.log(result); // [20, 40]
```

---

## 23. How do you flatten an array?

### Using built-in `flat`

```js
const arr = [1, [2, [3, 4]]];
console.log(arr.flat(Infinity)); // [1, 2, 3, 4]
```

### Using recursion

```js
function flatten(arr) {
  return arr.reduce((acc, cur) => {
    return acc.concat(Array.isArray(cur) ? flatten(cur) : cur);
  }, []);
}

console.log(flatten([1, [2, [3, 4]]])); // [1, 2, 3, 4]
```

---

## 24. How do you remove duplicates from an array?

### Using `Set`

```js
const arr = [1, 2, 2, 3, 3, 4];
const unique = [...new Set(arr)];
console.log(unique); // [1, 2, 3, 4]
```

---

## 25. Summary

This article covers common JavaScript interview topics, including:

- scope and closures
- prototype chain and `this`
- `Promise`, `async/await`, and event loop
- deep copy, debounce, throttle, and currying
- practical coding questions about arrays and objects

If you can clearly explain these topics and write the related code confidently, you will be well prepared for most JavaScript and frontend interviews.

## 💬 Have thoughts? Leave a comment below!
