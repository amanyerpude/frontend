Let’s dive into **Question 4: Deep Merge of Two Objects** — a frequent real-world and interview problem, especially in frontend roles where state merging is common (like in Redux or React context).

---

## 🔹 **Question 4: Deep Merge of Two Objects**

### 🧠 **Interview-style Question Statement:**

> Write a function that deeply merges two JavaScript objects.  
> If both objects share a key, and the values of that key are also objects, merge them recursively.  
> Otherwise, the value from the second object should overwrite the first.

---

### 🔸 Example:

```js
Input:
obj1 = { a: 1, b: { x: 10, y: 20 } }
obj2 = { b: { y: 99, z: 30 }, c: 3 }

Output:
{ a: 1, b: { x: 10, y: 99, z: 30 }, c: 3 }
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Loop through each key in `obj2`
    
- If the key exists in `obj1` and **both values are objects**, merge them **recursively**
    
- Else, **overwrite** the value in `obj1` with the value from `obj2`
    

---

### ✅ **Code (Recursive Solution)**

```js
function deepMerge(obj1, obj2) {
  const result = { ...obj1 }; // make a shallow copy

  for (let key in obj2) {
    if (
      obj2.hasOwnProperty(key) &&
      typeof obj2[key] === 'object' &&
      obj2[key] !== null &&
      !Array.isArray(obj2[key])
    ) {
      // if both sides are objects, merge them recursively
      result[key] = deepMerge(result[key] || {}, obj2[key]);
    } else {
      // otherwise, overwrite
      result[key] = obj2[key];
    }
  }

  return result;
}
```

---

### 🔍 **Explanation:**

- `typeof obj2[key] === 'object'` checks if the value is an object (but not array or null).
    
- `result[key] || {}` ensures we don’t try to merge with `undefined`.
    
- This solution **does not handle arrays** — they’ll be overwritten (which is often acceptable unless arrays are part of the merge logic).
    

---

### 🧪 Walkthrough Example:

```js
obj1 = { a: 1, b: { x: 10, y: 20 } }
obj2 = { b: { y: 99, z: 30 }, c: 3 }

deepMerge(obj1, obj2)
```

Step-by-step:

- `a` only exists in `obj1` → keep as is
    
- `b` exists in both → go deeper:
    
    - `x` exists only in obj1 → keep
        
    - `y` exists in both → overwrite with `99`
        
    - `z` exists only in obj2 → add
        
- `c` exists only in obj2 → add
    

Final result:

```js
{ a: 1, b: { x: 10, y: 99, z: 30 }, c: 3 }
```

---

## ⚠️ What to Watch For in Interviews

- ✅ Check `typeof` to avoid merging `null`
    
- ✅ Avoid treating arrays as objects (unless asked)
    
- ✅ Handle nested object keys
    
- ✅ Avoid mutation by copying the object
    

---

### 🧠 What You Say in an Interview:

> “I use recursion to go deeper whenever both values are objects.  
> If either value isn’t an object (like number or string), I overwrite the value in the first object with the second.  
> This handles deeply nested merges without side effects.”

---

### ⏱️ Time & Space Complexity

- **Time:** O(n) in terms of keys, but could grow with nested depth
    
- **Space:** O(n) for the resulting object (since we’re not mutating original)
    

---

Ready to tackle **Question 5: Array Flattening (recursive and .flat)** next?