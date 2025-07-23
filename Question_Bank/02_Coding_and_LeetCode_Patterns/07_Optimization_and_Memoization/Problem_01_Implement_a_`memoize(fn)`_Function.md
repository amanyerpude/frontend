Great! Let's tackle one of the most practical and foundational problems in frontend performance:

---

## 🔹 **Problem: Implement a `memoize(fn)` Function**

### 🧠 **Interview-style Question Statement:**

> Write a function `memoize(fn)` that takes another function `fn` and returns a **cached (memoized)** version of that function.  
> When called with the same arguments again, it should return the **cached result** instead of re-executing `fn`.

---

### 🔸 Example:

```js
function slowSquare(n) {
  console.log("Computing...");
  return n * n;
}

const memoSquare = memoize(slowSquare);

memoSquare(5); // "Computing..." → 25
memoSquare(5); // no log → 25 (from cache)
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Wrap a function so that:
    
    - You **cache the result** for every unique input
        
    - If the same input comes again, return the cached value instead of recomputing
        

---

## ✅ **Basic Memoization with Single Argument**

```js
function memoize(fn) {
  const cache = {};

  return function (arg) {
    if (arg in cache) {
      return cache[arg];
    } else {
      const result = fn(arg);
      cache[arg] = result;
      return result;
    }
  };
}
```

---

### 🧪 Usage:

```js
const square = memoize(n => {
  console.log("Calculating...");
  return n * n;
});

console.log(square(4)); // logs, returns 16
console.log(square(4)); // returns 16, no log
```

---

## ✅ **Advanced: Handle Multiple Arguments**

```js
function memoize(fn) {
  const cache = new Map();

  return function (...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      return cache.get(key);
    }

    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}
```

---

### 🔍 Why `JSON.stringify(args)`?

- Because arrays and objects aren’t usable as keys in plain objects
    
- `Map` allows more flexible keys and better performance
    

---

## 🧠 What You Say in an Interview:

> “I used a closure to maintain a private cache.  
> I used `JSON.stringify(args)` to serialize the arguments as keys in the cache.  
> If the function is called again with the same inputs, I return the cached result.”

---

### ⏱️ Time & Space Complexity

|Operation|Time|
|---|---|
|Cache hit|O(1) (Map lookup)|
|Cache miss|O(1) to compute, plus cache write|

---

Would you like to explore:

- **LRU cache / timed cache extension** of this?
    
- Or move on to another **frontend performance pattern**?