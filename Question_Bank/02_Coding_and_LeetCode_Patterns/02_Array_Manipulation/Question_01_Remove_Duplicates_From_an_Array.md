
---

## 🔹 **Question 1: Remove Duplicates From an Array**

### 🧠 **Interview-style Question Statement:**

> Given an array of integers, return a new array with all duplicates removed.  
> For example, if the input is `[1, 2, 2, 3, 4, 4, 4, 5]`, the output should be `[1, 2, 3, 4, 5]`.

---

## 🧱 **Step-by-Step Explanation (Beginner-friendly)**

### 🎯 Your Goal:

You need to remove repeated values and keep just one of each.

---

### ✅ **Approach 1: Using `Set` (Simplest and best for interviews)**

```js
function removeDuplicates(arr) {
  return [...new Set(arr)];
}
```

### 🔍 **Explanation:**

- A **Set** is a special object in JavaScript that only stores **unique values**.
    
- `new Set(arr)` removes duplicates.
    
- `...` is the **spread operator** that pulls all values out of the Set and puts them into a new array.
    

```js
const arr = [1, 2, 2, 3, 4, 4, 5];
const unique = [...new Set(arr)];
console.log(unique); // [1, 2, 3, 4, 5]
```

---

### 📦 **Approach 2: Manual method using a loop (for interviews that don’t allow built-ins)**

```js
function removeDuplicates(arr) {
  const seen = {};
  const result = [];

  for (let num of arr) {
    if (!seen[num]) {
      result.push(num);
      seen[num] = true;
    }
  }

  return result;
}
```

### 🔍 **Explanation:**

- We use an object `seen` to **remember what we’ve already added**.
    
- If the number hasn't been seen, we push it to `result` and mark it as seen.
    
- This mimics how a Set works, but using plain JS.
    

---

## 🧠 **What You Say in an Interview:**

> “I’ll use a `Set` because it gives me uniqueness out of the box in JavaScript.  
> If the company disallows built-in shortcuts, I’ll use an object to track seen elements and build a new array.”

---

### 💡 Bonus (If They Ask for In-Place Deduplication in a Sorted Array):

You’ll use a **two-pointer** approach — we’ll cover this in an advanced round.

---

## ✅ **Your Turn to Practice**

Try this input:

```js
removeDuplicates([10, 10, 20, 30, 20, 40, 40, 50])
```

---
