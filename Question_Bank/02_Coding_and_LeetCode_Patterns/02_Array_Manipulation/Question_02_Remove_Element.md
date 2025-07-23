
---

## 🔹 **Question 2: Remove Element**

### 🧠 **Interview-style Question Statement:**

> Given an array of integers `nums` and an integer `val`, **remove all instances of `val` in-place** and return the new length of the array.
> 
> Do **not** allocate extra space. Modify the input array directly.
> 
> The order of elements can be changed.
> 
> Example:  
> Input: `nums = [3, 2, 2, 3], val = 3`  
> Output: `2`, and the first two elements of `nums` can be `[2, 2]`.

---

### ✅ **Your Goal:**

- Remove all values equal to `val`.
    
- Modify the original array (in-place).
    
- Return the **new length** of the updated array.
    
- You don’t need to worry about what's in the rest of the array after that length.
    

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🧠 Think Like This:

- “I’ll loop through the array.”
    
- “If the current number is **not** equal to `val`, I’ll keep it.”
    
- “I’ll use a pointer `i` to track where to write the next ‘kept’ element.”
    

---

### ✅ **Code (Two Pointer Pattern)**

```js
function removeElement(nums, val) {
  let i = 0;

  for (let j = 0; j < nums.length; j++) {
    if (nums[j] !== val) {
      nums[i] = nums[j];
      i++;
    }
  }

  return i;
}
```

---

### 🔍 **Explanation:**

- `j` loops through the full array.
    
- `i` keeps track of the **position to write** non-`val` elements.
    
- We overwrite elements we want to remove by **writing over them with the next valid number**.
    
- In the end, `i` tells us how many elements we’ve kept.
    

---

### 🧪 **Example Walkthrough**

```js
nums = [3, 2, 2, 3], val = 3
```

- j = 0 → nums[0] == 3 → skip
    
- j = 1 → nums[1] == 2 → nums[0] = 2, i++
    
- j = 2 → nums[2] == 2 → nums[1] = 2, i++
    
- j = 3 → nums[3] == 3 → skip
    

✅ Final array: `[2, 2, _, _]`, return `i = 2`

---

### 🧠 What You Say in an Interview:

> “I’ll use a two-pointer approach. One pointer reads each item, and another tracks where to write the next valid item. This allows us to modify the array in-place with O(1) space.”

---

### ⚠️ **Edge Cases to Mention**

- Empty array
    
- Array with no `val` present
    
- Array with all elements as `val`
    

---

### 🔚 **Time & Space Complexity**

- **Time:** O(n) — loop through array once
    
- **Space:** O(1) — no extra space used
    

---
