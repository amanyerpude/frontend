Awesome — let’s move to **Question 6: Divide Array into Chunks** — another common problem asked to test your **loop logic, array slicing, and thought process**.

---

## 🔹 **Question 6: Divide Array in Chunks**

### 🧠 **Interview-style Question Statement:**

> Given an array and a chunk size `n`, divide the array into subarrays (chunks) of length `n`.  
> The last chunk may be smaller if there aren’t enough elements.
> 
> Example:  
> Input: `arr = [1, 2, 3, 4, 5, 6, 7], chunk = 3`  
> Output: `[[1, 2, 3], [4, 5, 6], [7]]`

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

Split an array into smaller arrays of a fixed length (`chunkSize`).

---

### ✅ **Approach 1: Using a Loop + `.slice()`**

```js
function chunkArray(arr, size) {
  let result = [];

  for (let i = 0; i < arr.length; i += size) {
    result.push(arr.slice(i, i + size));
  }

  return result;
}
```

---

### 🔍 **Explanation:**

- Start at index `0`, go in steps of `size`
    
- Use `.slice(i, i + size)` to grab `size` elements at a time
    
- Push those into `result`
    
- This approach **doesn’t modify the original array**
    

---

### 🧪 Example:

Input: `[1, 2, 3, 4, 5, 6, 7], size = 3`

- i = 0 → `[1, 2, 3]`
    
- i = 3 → `[4, 5, 6]`
    
- i = 6 → `[7]`
    

✅ Output: `[[1, 2, 3], [4, 5, 6], [7]]`

---

### ✅ **Approach 2: Using `.reduce()` (Functional Style)**

```js
function chunkArray(arr, size) {
  return arr.reduce((acc, val) => {
    const last = acc[acc.length - 1];
    if (!last || last.length === size) {
      acc.push([val]); // start new chunk
    } else {
      last.push(val); // add to current chunk
    }
    return acc;
  }, []);
}
```

---

### 🔍 Explanation:

- `reduce` builds up the final array step by step
    
- If the last chunk is full, start a new one
    
- Otherwise, push the value to the current chunk
    

This style is elegant but harder to debug for beginners — only mention if you’re comfortable.

---

## 🧠 What You Say in an Interview:

> “I chose the `.slice()` loop method for clarity and control.  
> It’s easy to understand and modify, and avoids mutation.  
> If needed, I can use `.reduce()` for a more functional approach.”

---

### ⏱️ Time & Space Complexity

- **Time:** O(n)
    
- **Space:** O(n) (new array of chunks)
    

---

### ❓ What If:

- size is `0`? → return empty array or throw error
    
- size is `> array.length`? → return one chunk
    
- array is empty? → return `[]`
    

---
