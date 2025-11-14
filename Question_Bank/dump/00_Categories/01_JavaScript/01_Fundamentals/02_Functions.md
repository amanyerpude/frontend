# JavaScript Functions

## 🔒 Closures

**[Source: dump_three.md, Section: JavaScript Deep Dive]**

1. Explain **closures** in JavaScript with a real-world analogy.

---

**[Source: dump/00_JavaScript_Interview.md, Section: Functions & Execution]**

1. Closures: advantage and disadvantage

---

**[Source: dump/JavaScript.md, Section: Functions & Scoping]**

1. What is a closure in JavaScript?

2. Explain the concept of closures in JavaScript with a real-world example.

---

## 📞 Call, Apply, and Bind

**[Source: dump_one.md, Lines 15-22]**

1. What's the difference between **call**, **apply**, and **bind** — with real examples?

---

**[Source: dump_four.md, Section: Top 10 Most Common Questions]**

1. Call, Apply, and Bind — difference between them + write a polyfill.

---

**[Source: dump/00_JavaScript_Interview.md, Section: Fundamentals]**

1. This, call(), apply(), bind()

---

**[Source: dump/JavaScript.md, Section: Functions & Scoping]**

1. What is the difference between `call()`, `apply()`, and `bind()`?

2. What is `bind()`, `call()`, and `apply()` in JavaScript, and when do you use them?

---

**[Source: dump/JavaScript.md, Section: Performance, Utilities, and Best Practices]**

1. What are the differences between `call()`, `apply()`, and `bind()`?

---

## 🎯 Callbacks & Higher-Order Functions

**[Source: dump/JavaScript.md, Section: Functions & Scoping]**

1. What are callbacks in JavaScript?

2. What are higher-order functions in JavaScript?

---

## ⚡ Function Types

**[Source: dump/00_JavaScript_Interview.md, Section: Functions & Execution]**

1. Immediately Invoked Function Expression (IIFE)

2. Currying Function

3. Pure Function

---

**[Source: dump_four.md, Lines 57-111]**

7. Currying Function for Infinite Sum.

```jsx
sum(10)(20)(30)() → 60
sum(10)(20)(30)(40)(50)(60)() → 210
```

---

**[Source: dump/JavaScript.md, Section: Functions & Scoping]**

1. What is the difference between pure and impure functions?

2. What is IIFE (Immediately Invoked Function Expression)?

3. What are the limitations of arrow functions?

4. What is an anonymous function in JavaScript?

---

## ⚛️ React useState Batching & Async Updates

**[Source: dump_four.md, Lines 30-50]**

**Scenario Question**

```jsx
const [count, setCount] = useState(0);

const incrementHandler = () => {
  setCount(count + 5);
  setCount(count + 5);
  setCount(count + 5);
  console.log(count);
};
```

Two questions:

1. ❓ What will console.log(count) print?
2. ❓ What will be the updated count value on the UI?

