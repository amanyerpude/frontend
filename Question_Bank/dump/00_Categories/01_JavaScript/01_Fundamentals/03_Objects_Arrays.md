# Objects & Arrays

## 🎯 Object Basics

**[Source: dump/JavaScript.md, Section: Arrays & Objects]**

1. What is the difference between an object and an array in JavaScript?

2. What are different ways to create objects in JavaScript?

---

## 🔧 Object Methods

**[Source: dump/JavaScript.md, Section: Arrays & Objects]**

1. What are object methods like `Object.keys()`, `Object.values()`, and `Object.entries()`?

2. What is the difference between `Object.freeze()` and `Object.seal()`?

3. Able to modify and transform objects

---

## 📋 Array Methods

**[Source: dump/JavaScript.md, Section: Arrays & Objects]**

1. What is the difference between `map()` and `forEach()`?

2. What is the difference between `map()` and `filter()`?

3. What is the difference between `find()` and `findIndex()`?

4. What is the difference between `slice()` and `splice()`?

5. Difference between array constructor and `Array.of()`

---

## 📦 Copying & Cloning

**[Source: dump_four.md, Section: Top 10 Most Common Questions]**

1. Deep Copy vs Shallow Copy (How to achieve this)

```jsx
const a = { ab: { cd: { ef: true } } };
const b = a;
const c = { ...a };
console.log(a === b);
console.log(a === c);
a.ab.cd.ef = false;
console.log(b.ab.cd.ef);
console.log(c.ab.cd.ef);
```

---

**[Source: dump/00_JavaScript_Interview.md, Section: Object and Memory]**

1. Shallow copy Deep Copy

---

**[Source: dump/JavaScript.md, Section: Arrays & Objects]**

1. What is the difference between shallow copy and deep copy?

2. How do you clone an object or array in JavaScript?

