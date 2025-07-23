Perfect — let’s tackle **Question 7: Rotate Array by K** — a classic problem that tests **array manipulation, edge case handling, and understanding of in-place changes**.

---

## 🔹 **Question 7: Rotate Array by K Positions**

### 🧠 **Interview-style Question Statement:**

> Given an array, rotate the elements to the right by `k` steps.  
> Rotation means each element moves `k` positions to the right, and the last elements wrap around to the front.
> 
> You must return the rotated array.
> 
> Example:  
> Input: `arr = [1, 2, 3, 4, 5, 6, 7]`, `k = 3`  
> Output: `[5, 6, 7, 1, 2, 3, 4]`

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Move each element `k` steps to the right
    
- Wrap around the end
    
- Can be solved by slicing, or in-place with reversals
    

---

## ✅ **Approach 1: Using `.slice()` (Clean & Interview-Friendly)**

```js
function rotateArray(arr, k) {
  const n = arr.length;
  k = k % n; // handles k > n

  return arr.slice(-k).concat(arr.slice(0, n - k));
}
```

---

### 🔍 **Explanation:**

- `arr.slice(-k)` gives the **last k elements**
    
- `arr.slice(0, n - k)` gives the **first part**
    
- You **join** them using `.concat()`
    

---

### 🧪 Example:

```js
arr = [1, 2, 3, 4, 5, 6, 7], k = 3

arr.slice(-3) → [5, 6, 7]  
arr.slice(0, 4) → [1, 2, 3, 4]  
concat → [5, 6, 7, 1, 2, 3, 4]
```

✅ Done.

---

## ✅ **Approach 2: In-place (LeetCode Style — Reverse Trick)**

```js
function rotate(arr, k) {
  k %= arr.length;

  reverse(arr, 0, arr.length - 1);
  reverse(arr, 0, k - 1);
  reverse(arr, k, arr.length - 1);
}

function reverse(arr, start, end) {
  while (start < end) {
    [arr[start], arr[end]] = [arr[end], arr[start]];
    start++;
    end--;
  }
}
```

---

### 🔍 **Explanation:**

1. Reverse the whole array
    
2. Reverse the first `k` elements
    
3. Reverse the remaining `n-k` elements
    

This rotates the array **in-place with O(1) extra space**.

---

### 🧠 What You Say in an Interview:

> “If space isn't constrained, I’ll use slicing for clarity.  
> If asked to rotate in-place with O(1) space, I’ll use the reverse method.  
> It’s a classic trick to rotate arrays efficiently.”

---

### ✅ Edge Cases to Mention:

- `k = 0` → no rotation
    
- `k > array.length` → use `k % array.length`
    
- Empty array → return empty array
    

---

### ⏱️ Time & Space Complexity

|Method|Time|Space|
|---|---|---|
|`slice`|O(n)|O(n)|
|`reverse`|O(n)|O(1)|

---

That wraps up all your **array manipulation** problems! 🎉  
Would you like a compact **PDF cheat sheet** of all 7? Or shall we start a new set — like **React internals** or **DOM questions**?