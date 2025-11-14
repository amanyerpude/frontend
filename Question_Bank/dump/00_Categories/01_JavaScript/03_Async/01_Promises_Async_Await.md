# Promises & Async/Await

## 💼 Promise & Async/Await Output

**[Source: dump_four.md, Lines 85-96]**

1. Promise & Async/Await Output

```jsx
async function chart(v){
  console.log("start", v);
  await console.log("middle", v);
  console.log("end", v);
}
chart("first");
chart("second");
```

---

## 📚 Theory Questions

### Basics

**[Source: dump/00_JavaScript_Interview.md, Section: Asynchronous JavaScript]**

1. Promises, Async Await

---

**[Source: dump/JavaScript.md, Section: Asynchronous JavaScript]**

1. What is the difference between synchronous and asynchronous code in JavaScript?

2. What are Promises in JavaScript?

3. How do JavaScript promises work, and what is the `then()` method?

4. What is `async/await`, and how does it simplify asynchronous code?

5. What is the difference between `setTimeout()` and `setInterval()`?

---

### Promise Methods

**[Source: dump/JavaScript.md, Section: Asynchronous JavaScript]**

1. How do you handle multiple promises simultaneously?

2. What is the difference between `Promise.all`, `allSettled`, `any`, and `race`?

3. What is the third method other than `.then()` and `.catch()`? (explicitly mentioning `.finally()`)

4. What is the third method other than `.then()` and `.catch()`?

5. Promises (then-catch, async-await, promise.all)

6. Name some static Promise methods and explain the difference between `Promise.all()` and `Promise.allSettled()`.

7. What is the difference between `Promise.all`, `allSettled`, `any`, and `race`?

---

### Error Handling

**[Source: dump/00_JavaScript_Interview.md, Section: Asynchronous JavaScript]**

1. How to catch errors inside loops - Original question: "How to catch errors inside loops"

2. How error got catched in asyn await function - Original question: "How error got catched in asyn await function"

---

**[Source: dump/JavaScript.md, Section: Asynchronous JavaScript]**

1. How do you manage errors in JavaScript (sync and async)?

---

### Web APIs

**[Source: dump/JavaScript.md, Section: Asynchronous JavaScript]**

1. Fetch API

---

## 🔥 Promise Patterns

**[Source: dump_four.md, Lines 119-145]**

1. Execute promises in sequence.

2. Retry a promise N times on failure.

3. Implement a cancelable promise.

4. MapLimit.

---

## 🔧 Promise Polyfills

**[Source: dump_four.md, Lines 119-145]**

4. Implement `Promise.all`, `Promise.race`, and `Promise.allSettled` polyfills.

---

**[Source: dump_two.md, Lines 173-235]**

8. **Implement a Promise.all polyfill.**
    - How do you handle one rejection?
    - How do you deal with an empty array?

9. **Implement a Promise.race polyfill.**
    - How do you return the first settled promise?
    - How would you handle rejections?

