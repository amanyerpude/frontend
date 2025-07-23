Great! Now let’s tackle **Question 5: Array Flattening** — a very common problem in frontend interviews, especially to test **recursion**, **array methods**, and your understanding of **nested structures**.

---

## 🔹 **Question 5: Flatten a Nested Array**

### 🧠 **Interview-style Question Statement:**

> Given a nested array of any depth (e.g., `[1, [2, [3, [4]]]]`), write a function to **flatten it into a single-level array**.
> 
> You must implement:
> 
> - One solution using recursion
>     
> - One using the built-in `.flat()` method
>     

---

## 🧱 **Step-by-Step Beginner Explanation**

---

### ✅ **Approach 1: Using `.flat(Infinity)`**

This is the **easiest way**, and good to mention early in the interview.

```js
const flatten = (arr) => arr.flat(Infinity);
```

- `arr.flat()` flattens **1 level** by default.
    
- Passing `Infinity` flattens **all levels**, no matter how deeply nested.
    

---

### ✅ **Approach 2: Using Recursion (Interview-favourite)**

```js
function flatten(arr) {
  let result = [];

  for (let item of arr) {
    if (Array.isArray(item)) {
      result = result.concat(flatten(item)); // recursive call
    } else {
      result.push(item);
    }
  }

  return result;
}
```

---

### 🔍 **Explanation:**

- You loop through each item.
    
- If it’s an array, you recursively call `flatten` on it.
    
- If it’s not an array (e.g., number, string), you just push it into the result.
    
- `concat()` is used to **combine the results** from recursive calls.
    

---

### 🧪 Example Walkthrough:

Input:

```js
[1, [2, [3, [4]]]]
```

Step-by-step:

- 1 → push
    
- [2, [3, [4]]] → flatten again
    
    - 2 → push
        
    - [3, [4]] → flatten again
        
        - 3 → push
            
        - [4] → flatten again
            
            - 4 → push
                

✅ Final result: `[1, 2, 3, 4]`

---

### ❓ What If It's Already Flat?

```js
[1, 2, 3] → should return the same
```

What If It Contains Empty Arrays?

```js
[1, [], [2, [3]]] → still works → `[1, 2, 3]`
```

---

### 🧠 What You Say in an Interview:

> “I can use `.flat(Infinity)` for quick flattening if built-in methods are allowed.  
> But to show understanding, I also implemented a recursive version where I check each item and flatten only if it’s an array. This works for deeply nested arrays and keeps the logic clean.”

---

### 🧪 Bonus: Using `reduce` (If you want to flex)

```js
function flatten(arr) {
  return arr.reduce((acc, val) => 
    acc.concat(Array.isArray(val) ? flatten(val) : val), []);
}
```

Same logic as recursion, but in a more functional programming style using `reduce`.

---

### ⏱️ Time & Space Complexity

- **Time:** O(n) — each element is visited once
    
- **Space:** O(n) — storing all values in final flat array
    

---

Ready to continue with **Question 6: Divide Array into Chunks**?