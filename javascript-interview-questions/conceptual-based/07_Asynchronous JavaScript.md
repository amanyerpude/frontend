
```markdown
# ⏳ Asynchronous JavaScript

1. 🌟What is the difference between synchronous and asynchronous code in JavaScript?  
2. 🌟What are Promises in JavaScript?  
3. 🌟How do JavaScript promises work, and what is the `then()` method?  
4. 🌟What is `async/await`, and how does it simplify asynchronous code?  
5. What is the difference between `setTimeout()` and `setInterval()`?  
6. 🌟What is the event loop in JavaScript?  
7. What is the difference between microtasks and macrotasks in the event loop?  
8. What is a call stack in JavaScript?  
9. How do you handle multiple promises simultaneously?  
10. 🌟What is the difference between `Promise.all`, `allSettled`, `any`, and `race`?  
11. How do you manage errors in JavaScript (sync and async)?  
12. 🌟What is event delegation in JavaScript?  
13. 🌟How does the JavaScript garbage collector work?  
14. What is a memory leak in JavaScript and how do you debug it?
15. 🌟What is the third method other than `.then()` and `.catch()`? (explicitly mentioning `.finally()`)
```

--------------------------------------------------------------------------

# **1️⃣ What is the difference between synchronous and asynchronous code in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Begin by defining **JavaScript as single-threaded**.
    
- Explain that **synchronous code executes line by line**, whereas **asynchronous code does not block execution**.
    
- Use a **real-world analogy (e.g., restaurant order example)** to make it memorable.
    

---

## 💡 **Answer**

JavaScript is **single-threaded**, meaning it executes **one task at a time** using the **call stack**.

- **Synchronous Code** → Tasks are executed **line by line**, blocking the thread until completion.
    
- **Asynchronous Code** → Tasks are **delegated (e.g., to Web APIs)** and executed later, allowing other code to run in the meantime.
    

---

## 🧩 **Example**

```js
// Synchronous
console.log("1");
console.log("2");

// Asynchronous
console.log("1");
setTimeout(() => console.log("2"), 1000);
console.log("3");

// Output:
// 1
// 3
// 2
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is asynchronous programming important in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Emphasise **non-blocking behaviour** and **better user experience**.
    

#### 💡 **Answer**

Asynchronous programming allows JavaScript to:  
✅ Handle **I/O tasks (API calls, timers)** without blocking.  
✅ Keep **UI responsive** in web apps.  
✅ Improve **performance and scalability**.

---

### **2️⃣ What are examples of asynchronous operations in JavaScript?**

#### ✅ **How to Answer in an Interview**

- List **API calls, file reading, timers, event listeners** as examples.
    

#### 💡 **Answer**

Common asynchronous operations include:

- `setTimeout`, `setInterval`
    
- Fetch API calls (`fetch`, `XMLHttpRequest`)
    
- Event listeners (`onclick`, `onload`)
    
- Node.js I/O operations (file system, DB queries)
    

---

## 🎯 **Interview Tips**

✅ Always mention **JavaScript is single-threaded with an event loop**.  
✅ Use **a relatable analogy** (e.g., restaurant orders being served).  
✅ Show an example where asynchronous code **changes execution order**.

---
# **2️⃣ What are Promises in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying a **Promise represents the eventual completion (or failure) of an asynchronous operation**.
    
- Mention the **three states: pending, fulfilled, rejected**.
    
- Explain **why promises were introduced (to avoid callback hell)**.
    

---

## 💡 **Answer**

A **Promise** in JavaScript is an **object that represents the eventual result of an asynchronous operation**.

It can be in one of **three states**:

1. **Pending** – Initial state, neither fulfilled nor rejected.
    
2. **Fulfilled** – Operation completed successfully (`resolve`).
    
3. **Rejected** – Operation failed (`reject`).
    

---

## 🧩 **Example**

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 1000);
});

promise.then(result => console.log(result)); // Success! (after 1s)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why were Promises introduced in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Explain that **callbacks caused nesting issues ("callback hell")**.
    
- Promises make **asynchronous code more readable and manageable**.
    

#### 💡 **Answer**

Before Promises, callbacks were used for async tasks, leading to:  
❌ Deeply nested code (callback hell)  
❌ Difficult error handling

Promises solve this by providing:  
✅ **Chaining with `.then()`**  
✅ **Centralised error handling with `.catch()`**

---

### **2️⃣ What are the states of a Promise?**

#### ✅ **How to Answer in an Interview**

- Clearly list the **three states** and **when they occur**.
    

#### 💡 **Answer**

A Promise has **three states**:  
1️⃣ **Pending** → Initial state.  
2️⃣ **Fulfilled** → `resolve()` is called.  
3️⃣ **Rejected** → `reject()` is called.

---

## 🎯 **Interview Tips**

✅ Always mention **Promise states** and why they are better than callbacks.  
✅ Be ready for **follow-ups on `.then()`, `.catch()`, `.finally()`**.  
✅ Short code example helps show practical usage.

---
# **3️⃣ How do JavaScript promises work, and what is the `then()` method?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **a Promise executes asynchronously and returns a placeholder object for the future value**.
    
- Explain **the `then()` method is used to handle the resolved value**.
    
- Show **how chaining works with `then()`**.
    

---

## 💡 **Answer**

A **Promise** executes an asynchronous task and **eventually resolves or rejects**.

- The **`then()` method** is called **when the promise is fulfilled**, and it receives the resolved value.
    
- **Chaining `then()` calls** allows sequential execution of asynchronous operations.
    

---

## 🧩 **Example**

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve(10), 1000);
});

promise
  .then(num => num * 2)       // 20
  .then(result => console.log(result)); // 20
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What happens if you return a value inside `then()`?**

#### ✅ **How to Answer in an Interview**

- Mention that the **returned value becomes the input for the next `then()` in the chain**.
    

#### 💡 **Answer**

If you return a value from `then()`, it is **wrapped in a resolved promise** and passed to the next `then()`.

```js
Promise.resolve(5)
  .then(x => x * 2)    // returns 10
  .then(y => console.log(y)); // 10
```

---

### **2️⃣ What happens if you return a Promise inside `then()`?**

#### ✅ **How to Answer in an Interview**

- Explain that **the next `then()` waits until the returned promise resolves**.
    

#### 💡 **Answer**

If a `Promise` is returned inside `then()`, the chain **waits for it to resolve** before continuing.

```js
Promise.resolve(2)
  .then(x => new Promise(res => setTimeout(() => res(x * 3), 1000)))
  .then(result => console.log(result)); // 6 (after 1s)
```

---

## 🎯 **Interview Tips**

✅ Always highlight **chaining** as a key benefit.  
✅ Mention how returning **values vs promises** changes execution.  
✅ Be ready for follow-ups on **`.catch()` and `.finally()`**.

# **4️⃣ What is `async/await`, and how does it simplify asynchronous code?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **`async/await` is syntactic sugar over Promises**.
    
- Mention that **`async` functions always return a Promise**, and `await` pauses execution until the Promise resolves.
    
- Explain how it **makes async code look synchronous and cleaner**.
    

---

## 💡 **Answer**

`async/await` is a **modern way to write asynchronous code** in JavaScript, built on top of Promises.

- **`async`** → Marks a function as asynchronous (it always returns a Promise).
    
- **`await`** → Pauses execution until the Promise resolves, making code **look synchronous**.
    

---

## 🧩 **Example**

```js
// Using Promises
fetchData()
  .then(data => processData(data))
  .catch(err => console.error(err));

// Using async/await
async function getData() {
  try {
    const data = await fetchData();
    processData(data);
  } catch (err) {
    console.error(err);
  }
}
getData();
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is `async/await` better than `.then()`?**

#### ✅ **How to Answer in an Interview**

- Explain that it **makes code more readable** and **reduces callback nesting**.
    
- Also mention **error handling with `try...catch` is cleaner**.
    

#### 💡 **Answer**

✅ Cleaner, synchronous-like syntax.  
✅ Easier error handling with `try...catch`.  
✅ No deeply nested `.then()` chains.

---

### **2️⃣ Can we use `await` outside an `async` function?**

#### ✅ **How to Answer in an Interview**

- Explain that **you cannot use `await` outside `async`** except in **top-level `await` (ES2022)**.
    

#### 💡 **Answer**

- Before ES2022 → ❌ Cannot use `await` outside `async`.
    
- After ES2022 → ✅ `await` allowed at top-level in modules.
    

```js
// ✅ Top-level await (ES2022+)
const data = await fetch("api/data");
```

---

## 🎯 **Interview Tips**

✅ Always mention **`async/await` = syntactic sugar over Promises**.  
✅ Use **before/after example** to show how it simplifies code.  
✅ Be ready for follow-ups like **error handling & parallel execution with `Promise.all`**.

# **5️⃣ What is the difference between `setTimeout()` and `setInterval()`?**

---

## ✅ **How to Answer in an Interview**

- Start by saying both are **timers provided by the browser (Web APIs)**.
    
- Mention that **`setTimeout` runs once**, while **`setInterval` runs repeatedly**.
    
- Use a **table for clarity**.
    

---

## 💡 **Answer**

|Function|Purpose|Execution|
|---|---|---|
|**setTimeout()**|Executes a function **once** after a delay|Runs **one time**|
|**setInterval()**|Executes a function **repeatedly** at fixed intervals|Runs **until cleared**|

---

## 🧩 **Example**

```js
// setTimeout - runs once after 2 seconds
setTimeout(() => console.log("Hello after 2s"), 2000);

// setInterval - runs every 1 second
const interval = setInterval(() => console.log("Repeating..."), 1000);

// Stop after 5 seconds
setTimeout(() => clearInterval(interval), 5000);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How do you stop a `setTimeout()` or `setInterval()`?**

#### ✅ **How to Answer in an Interview**

- Explain that both return an **ID**, which can be passed to `clearTimeout()` or `clearInterval()`.
    

#### 💡 **Answer**

```js
const timeoutId = setTimeout(() => console.log("Hi"), 2000);
clearTimeout(timeoutId); // Cancels timeout

const intervalId = setInterval(() => console.log("Loop"), 1000);
clearInterval(intervalId); // Stops interval
```

---

### **2️⃣ What happens if the callback execution time is longer than the interval?**

#### ✅ **How to Answer in an Interview**

- Mention that **JavaScript won't start the next callback until the current one finishes**, because it’s single-threaded.
    

#### 💡 **Answer**

If the callback takes longer than the interval, the next execution **waits until the call stack is free**.  
This means intervals **can drift** if execution is slow.

---

## 🎯 **Interview Tips**

✅ Always differentiate **one-time vs repeated execution**.  
✅ Mention that **timers are part of Web APIs, not JS core**.  
✅ Be ready for follow-ups on **clearInterval/clearTimeout** and **execution drift**.

# **6️⃣ What is the event loop in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **JavaScript is single-threaded**, and the event loop **manages execution of sync & async tasks**.
    
- Mention **how the call stack, Web APIs, callback queue, and microtask queue interact**.
    
- Keep it short but conceptual – **diagram or analogy helps**.
    

---

## 💡 **Answer**

The **event loop** is the mechanism that allows JavaScript to **handle asynchronous operations despite being single-threaded**.

- It **checks the call stack** – if empty, it takes tasks from the **microtask queue** (Promises) first, then **callback queue** (setTimeout, events).
    
- This enables **non-blocking, asynchronous behaviour**.
    

---

## 🧩 **Example**

```js
console.log("Start");

setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");

// Output:
// Start
// End
// Promise   (microtask first)
// Timeout   (macrotask next)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between microtasks and macrotasks in the event loop?**

#### ✅ **How to Answer in an Interview**

- Explain that **microtasks (Promises, MutationObserver)** run **before** macrotasks (setTimeout, setInterval).
    

#### 💡 **Answer**

- **Microtasks** → Promise callbacks, queueMicrotask() – **executed first**.
    
- **Macrotasks** → setTimeout, setInterval, I/O events – executed **after all microtasks**.
    

```js
setTimeout(() => console.log("Macrotask"));
Promise.resolve().then(() => console.log("Microtask"));
```

Output:

```
Microtask
Macrotask
```

---

### **2️⃣ Why is the event loop important in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Because **it enables asynchronous, non-blocking behaviour** in a single-threaded language.
    

#### 💡 **Answer**

Without the event loop, JavaScript **could not handle async tasks like API calls, timers, or user events** while still processing other code.

---

## 🎯 **Interview Tips**

✅ Always mention **call stack, microtask queue, macrotask queue**.  
✅ Use a **small example with Promises & setTimeout**.  
✅ Be ready for **deep follow-ups on microtasks/macrotasks**.

---
# **7️⃣ What is the difference between microtasks and macrotasks in the event loop?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **both are task queues handled by the event loop**, but **microtasks have higher priority**.
    
- Give examples of **which functions go into each queue**.
    
- Show a short code snippet to demonstrate execution order.
    

---

## 💡 **Answer**

In JavaScript, **tasks are queued as microtasks or macrotasks**, and **microtasks always run first after the current execution context ends**.

|Queue Type|Examples|Priority|
|---|---|---|
|**Microtasks**|Promise callbacks, `queueMicrotask`, `MutationObserver`|Higher|
|**Macrotasks**|`setTimeout`, `setInterval`, I/O callbacks, DOM events|Lower|

---

## 🧩 **Example**

```js
console.log("Start");

setTimeout(() => console.log("Macrotask"), 0);

Promise.resolve().then(() => console.log("Microtask"));

console.log("End");

// Output:
// Start
// End
// Microtask
// Macrotask
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why do microtasks run before macrotasks?**

#### ✅ **How to Answer in an Interview**

- Explain that **Promises and microtasks are designed to be executed as soon as possible** for more predictable async behaviour.
    

#### 💡 **Answer**

Microtasks are given **higher priority** so that Promises and other critical async tasks **execute immediately after the current stack**, before macrotasks.

---

### **2️⃣ Can microtasks create an infinite loop?**

#### ✅ **How to Answer in an Interview**

- Yes, because **new microtasks can queue more microtasks**, blocking macrotasks indefinitely.
    

#### 💡 **Answer**

```js
function loop() {
  Promise.resolve().then(loop);
}
loop(); // Infinite microtask loop → macrotasks never run
```

This is why **excessive microtask chaining should be avoided**.

---

## 🎯 **Interview Tips**

✅ Always **list examples** for each queue.  
✅ Use a **short code snippet** to show the execution order.  
✅ Mention that **microtasks can block macrotasks if queued infinitely**.

# **8️⃣ What is a call stack in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **the call stack is a data structure that keeps track of function calls in JavaScript**.
    
- Mention that **JavaScript is single-threaded and uses the call stack to execute code line by line**.
    
- Use a **small example to show how functions are pushed and popped**.
    

---

## 💡 **Answer**

The **call stack** is a **LIFO (Last-In-First-Out) data structure** that JavaScript uses to **manage function execution**.

- When a function is called → **pushed to the stack**.
    
- When it returns → **popped from the stack**.
    

It helps JavaScript know **where it is in the program execution**.

---

## 🧩 **Example**

```js
function first() {
  second();
}
function second() {
  console.log("Hello");
}

first();
```

**Execution Flow (Stack):**  
1️⃣ `first()` → pushed  
2️⃣ `second()` → pushed  
3️⃣ `console.log()` → pushed & executed  
4️⃣ Functions popped as they return

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is a stack overflow?**

#### ✅ **How to Answer in an Interview**

- Explain that it happens when **the call stack exceeds its limit due to infinite recursion**.
    

#### 💡 **Answer**

A **stack overflow** occurs when **functions call each other infinitely without termination**, causing the stack to grow indefinitely.

```js
function recurse() {
  recurse(); // ❌ Infinite recursion
}
recurse(); // Stack overflow
```

---

### **2️⃣ How is the call stack related to asynchronous code?**

#### ✅ **How to Answer in an Interview**

- Mention that **asynchronous callbacks are not pushed to the stack immediately**, but **queued in Web APIs and later added back via the event loop**.
    

#### 💡 **Answer**

The call stack only executes **synchronous tasks**.  
Async tasks (`setTimeout`, Promises) **go to Web APIs**, and their callbacks are added **back to the stack via the event loop** when ready.

---

## 🎯 **Interview Tips**

✅ Always mention **LIFO behaviour**.  
✅ Show **function push/pop flow with a short example**.  
✅ Be ready for follow-ups on **stack overflow & relation to event loop**.

# **9️⃣ How do you handle multiple promises simultaneously?**

---

## ✅ **How to Answer in an Interview**

- Start by mentioning **JavaScript provides Promise utility methods (`Promise.all`, `allSettled`, `race`, `any`)**.
    
- Explain that these methods **allow parallel execution of promises** instead of chaining sequentially.
    
- Give a **basic example with `Promise.all()`**.
    

---

## 💡 **Answer**

Multiple promises can be handled simultaneously using **Promise combinators**:

1️⃣ **`Promise.all`** → Waits for all promises to **resolve** (fails fast if any reject).  
2️⃣ **`Promise.allSettled`** → Waits for all promises, regardless of success/failure.  
3️⃣ **`Promise.race`** → Returns the result of the **first promise to settle**.  
4️⃣ **`Promise.any`** → Returns the **first fulfilled promise**, ignores rejections.

---

## 🧩 **Example**

```js
const p1 = Promise.resolve(10);
const p2 = Promise.resolve(20);
const p3 = Promise.resolve(30);

Promise.all([p1, p2, p3]).then(values => console.log(values));
// Output: [10, 20, 30]
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use `Promise.all` vs `Promise.allSettled`?**

#### ✅ **How to Answer in an Interview**

- **Promise.all** fails fast if **any promise rejects**.
    
- **Promise.allSettled** always returns **all results** (fulfilled/rejected).
    

#### 💡 **Answer**

```js
Promise.all([p1, p2, Promise.reject("Error")])
  .catch(err => console.log(err)); // "Error"

Promise.allSettled([p1, p2, Promise.reject("Error")])
  .then(results => console.log(results));
// Returns an array with status for each promise
```

---

### **2️⃣ Can you run promises in parallel using `async/await`?**

#### ✅ **How to Answer in an Interview**

- Yes, by calling all promises first and then awaiting them together.
    

#### 💡 **Answer**

```js
async function getData() {
  const p1 = fetch("url1");
  const p2 = fetch("url2");
  const [res1, res2] = await Promise.all([p1, p2]);
}
```

This ensures both fetches happen **in parallel**, not sequentially.

---

## 🎯 **Interview Tips**

✅ Always mention **Promise combinators**.  
✅ Give **use-case examples** for `all`, `allSettled`, `race`, `any`.  
✅ Be ready for follow-ups on **error handling & parallel vs sequential execution**.

# **🔟 What is the difference between `Promise.all`, `allSettled`, `any`, and `race`?**

---

## ✅ **How to Answer in an Interview**

- Start by saying these are **Promise combinator methods** to handle multiple promises in parallel.
    
- Provide a **clear comparison table** for behaviour on resolve/reject.
    
- Give **one-liner use cases**.
    

---

## 💡 **Answer**

|Method|Resolves When|Rejects When|Use Case|
|---|---|---|---|
|**Promise.all**|All promises **fulfill**|Any promise **rejects**|Run multiple tasks in parallel and fail fast|
|**Promise.allSettled**|All promises **settle** (fulfilled/rejected)|❌ Never rejects|Get results of all promises regardless of success/failure|
|**Promise.race**|**First promise settles** (resolve or reject)|Rejects if first promise rejects|Use when you only care about the first result|
|**Promise.any**|**First promise fulfills**|Rejects only if **all reject**|Return first successful result, ignore failures|

---

## 🧩 **Example**

```js
const p1 = Promise.resolve(10);
const p2 = Promise.reject("Error");
const p3 = Promise.resolve(30);

Promise.all([p1, p3]).then(console.log);         // [10, 30]
Promise.allSettled([p1, p2]).then(console.log);  // [{status:'fulfilled',value:10}, {status:'rejected',reason:'Error'}]
Promise.race([p1, p3]).then(console.log);        // 10
Promise.any([p2, p3]).then(console.log);         // 30
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Which of these methods "fail fast"?**

#### ✅ **How to Answer in an Interview**

- Mention that **Promise.all** and **Promise.race** reject **as soon as one promise rejects (if it's first to settle)**.
    

#### 💡 **Answer**

- **Promise.all** → Fails immediately if **any promise rejects**.
    
- **Promise.race** → Fails if the **first settled promise rejects**.
    
- **Promise.allSettled** → Never rejects.
    
- **Promise.any** → Rejects **only if all promises fail**.
    

---

### **2️⃣ When should you use `Promise.any`?**

#### ✅ **How to Answer in an Interview**

- Explain that **Promise.any is ideal when you just need the first successful result and can ignore failures**.
    

#### 💡 **Answer**

```js
Promise.any([
  fetch("server1"), 
  fetch("server2"), 
  fetch("server3")
])
.then(response => console.log("First success:", response))
.catch(err => console.log("All failed"));
```

---

## 🎯 **Interview Tips**

✅ Use a **table to compare methods** (interviewers love this format).  
✅ Be ready to give **real-world use cases** for each method.  
✅ Mention **ES versions** – `Promise.any` is **ES2021**.

# **1️⃣1️⃣ How do you manage errors in JavaScript (sync and async)?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **error handling in JS is done using try-catch for synchronous code and `.catch()` or try-catch with async/await for asynchronous code**.
    
- Mention **custom error handling using `throw new Error()`**.
    
- Show **examples for both sync and async cases**.
    

---

## 💡 **Answer**

JavaScript provides different ways to handle errors:

### 🔹 **Synchronous Errors**

- Use `try...catch` to catch errors in normal code.
    

```js
try {
  JSON.parse("{invalidJson}");
} catch (err) {
  console.error("Error:", err.message);
}
```

### 🔹 **Asynchronous Errors**

1. **Promises** – Use `.catch()`
    
2. **Async/Await** – Wrap in `try...catch`
    

```js
// Using .catch()
fetch("wrong-url")
  .then(res => res.json())
  .catch(err => console.error("Fetch Error:", err));

// Using async/await
async function getData() {
  try {
    const res = await fetch("wrong-url");
    const data = await res.json();
  } catch (err) {
    console.error("Async Error:", err.message);
  }
}
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between `throw` and `return` in error handling?**

#### ✅ **How to Answer in an Interview**

- Explain that **`throw` stops execution and passes control to the nearest catch block**, while `return` just sends back a value.
    

#### 💡 **Answer**

```js
function test(val) {
  if (!val) throw new Error("Invalid value"); // stops execution
  return val; // just returns the value
}
```

---

### **2️⃣ How can you create custom error types in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Explain that you can **extend the Error class** to create custom errors.
    

#### 💡 **Answer**

```js
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

throw new ValidationError("Invalid input");
```

---

## 🎯 **Interview Tips**

✅ Always **show both sync & async handling**.  
✅ Mention **custom error classes** – interviewers like seeing deeper knowledge.  
✅ Be ready for follow-ups on **Promise rejection handling best practices**.

# **1️⃣2️⃣ What is event delegation in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **event delegation is a technique where you attach a single event listener to a parent element to handle events of its child elements using event bubbling**.
    
- Mention **it improves performance and avoids adding multiple listeners**.
    
- Show a **real-world example (list items click handler)**.
    

---

## 💡 **Answer**

**Event delegation** is a technique where **a single event listener is attached to a parent element**, and events from child elements are handled using **event bubbling (`event.target`)**.

✅ It improves performance when dealing with **many dynamically added child elements**.

---

## 🧩 **Example**

```html
<ul id="menu">
  <li>Home</li>
  <li>About</li>
  <li>Contact</li>
</ul>

<script>
document.getElementById("menu").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Clicked:", e.target.textContent);
  }
});
</script>
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is event delegation better than adding listeners to each element?**

#### ✅ **How to Answer in an Interview**

- Because it **reduces memory usage and works for dynamically added elements**.
    

#### 💡 **Answer**

- Fewer event listeners → Better **performance & memory efficiency**.
    
- Works for **elements added later to the DOM** (no need to reattach listeners).
    

---

### **2️⃣ What is event bubbling and capturing?**

#### ✅ **How to Answer in an Interview**

- Explain that **events propagate in two phases** – capturing (top → target) and bubbling (target → top).
    

#### 💡 **Answer**

- **Capturing phase** → Event travels **from root → target**.
    
- **Bubbling phase** → Event travels **from target → root**.
    

```js
element.addEventListener("click", handler, true); // Capturing
element.addEventListener("click", handler, false); // Bubbling
```

---

## 🎯 **Interview Tips**

✅ Always mention **event bubbling** as the core concept.  
✅ Show **a list example (UL > LI)** – interviewers love this.  
✅ Be ready for follow-ups on **capturing vs bubbling phases**.

# **1️⃣3️⃣ How does the JavaScript garbage collector work?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **JavaScript has automatic memory management using a garbage collector (GC)**.
    
- Explain that **GC frees memory occupied by objects that are no longer reachable (no references)**.
    
- Mention that **most browsers use mark-and-sweep algorithm**.
    

---

## 💡 **Answer**

JavaScript has **automatic garbage collection**, meaning developers don’t manually free memory.

- The **GC finds objects that are no longer reachable** (no references pointing to them).
    
- It then **frees their memory** using the **mark-and-sweep algorithm**.
    

---

## 🧩 **Example**

```js
let obj = { name: "Alice" };
obj = null; // No reference → eligible for GC
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the mark-and-sweep algorithm?**

#### ✅ **How to Answer in an Interview**

- Explain that GC **marks all reachable objects** and **removes unmarked (unreachable) ones**.
    

#### 💡 **Answer**

1. Start from **root objects (window, global)**.
    
2. **Mark all objects reachable via references**.
    
3. **Unmarked objects are removed from memory**.
    

---

### **2️⃣ Can JavaScript garbage collection be forced manually?**

#### ✅ **How to Answer in an Interview**

- No, **GC cannot be forced manually in browsers**, but **Node.js has experimental flags (`--expose-gc`)**.
    

#### 💡 **Answer**

In browsers → ❌ No way to force GC.  
In Node.js → ✅ Possible with `global.gc()` (requires `--expose-gc`).

---

## 🎯 **Interview Tips**

✅ Always mention **mark-and-sweep algorithm**.  
✅ Say **GC runs automatically, not manually controlled**.  
✅ Be ready for follow-ups on **memory leaks** and how to prevent them.

---

Alright ✅ Moving to **Q14: What is a memory leak in JavaScript and how do you debug it?**

---

# **1️⃣4️⃣ What is a memory leak in JavaScript and how do you debug it?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **a memory leak happens when memory that is no longer needed is not released because references to objects are still retained**.
    
- Mention common causes (unused event listeners, global variables, timers not cleared).
    
- Explain debugging using **browser DevTools (Memory tab, heap snapshots)**.
    

---

## 💡 **Answer**

A **memory leak** occurs when **memory that is no longer needed is not released**, usually because **there are still references to unused objects**.

---

### 🔹 **Common Causes**

1. Unremoved event listeners
    
2. Global variables growing indefinitely
    
3. Forgotten `setInterval` or `setTimeout`
    
4. Detached DOM elements
    

---

## 🧩 **Example**

```js
let arr = [];
setInterval(() => arr.push(new Array(1000000)), 1000); 
// Memory grows indefinitely unless interval is cleared
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How do you debug memory leaks?**

#### ✅ **How to Answer in an Interview**

- Mention **Chrome DevTools → Performance/Memory tab → Heap Snapshots**.
    
- Use **allocation timelines** to find objects that never get released.
    

#### 💡 **Answer**

✅ Use **Chrome DevTools → Memory tab → Heap Snapshots**  
✅ Look for **objects that keep growing in size**  
✅ Fix by **removing references, clearing timers, or detaching unused DOM nodes**

---

### **2️⃣ How can memory leaks be prevented?**

#### ✅ **How to Answer in an Interview**

- Best practices: **remove event listeners, clear timers, avoid global variables**.
    

#### 💡 **Answer**

✔ Always **remove event listeners** with `removeEventListener()`  
✔ Use `clearInterval()` and `clearTimeout()`  
✔ Avoid unnecessary global variables  
✔ Nullify references (`obj = null`) when no longer needed

---

## 🎯 **Interview Tips**

✅ Always mention **common causes + debugging tools**.  
✅ Give a **practical example of a leak (setInterval)**.  
✅ Be ready for follow-ups on **garbage collector behaviour**.

--------------------------------------------------------------------------
