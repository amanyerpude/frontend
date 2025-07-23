Great! Let's now tackle **Problem 2: Next Permutation** — a classic problem that tests **recursion thinking, array manipulation, and lexicographic order logic**. It's a common LeetCode hard-level favorite.

---

## 🔹 **Problem 2: Next Permutation**

### 🧠 **Interview-style Question Statement:**

> Given an array of numbers representing a permutation, rearrange the array into the **next lexicographically greater permutation** of numbers.
> 
> If such arrangement is not possible (i.e., it's the last permutation), rearrange it as the **lowest possible order** (i.e., sorted in ascending order).
> 
> You must modify the array **in-place** (no extra array).

---

### 🔸 Example:

```js
Input: [1, 2, 3]  
Output: [1, 3, 2]

Input: [3, 2, 1]  
Output: [1, 2, 3] // because it was the last permutation

Input: [1, 1, 5]  
Output: [1, 5, 1]
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

Find the next greater arrangement of the array that would come in "dictionary order."

---

### ✅ **Core Logic**

1. **Find the longest non-increasing suffix** (from the end).
    
2. **Find the pivot** — the element just before the suffix.
    
3. **Find the rightmost successor** to the pivot in the suffix (a number just larger).
    
4. **Swap pivot and successor**
    
5. **Reverse the suffix**
    

---

### ✅ **Code Implementation**

```js
function nextPermutation(nums) {
  let i = nums.length - 2;

  // Step 1: Find the first decreasing element from the right
  while (i >= 0 && nums[i] >= nums[i + 1]) {
    i--;
  }

  if (i >= 0) {
    // Step 2: Find just the next larger element to the right of nums[i]
    let j = nums.length - 1;
    while (nums[j] <= nums[i]) {
      j--;
    }

    // Step 3: Swap pivot with next larger
    [nums[i], nums[j]] = [nums[j], nums[i]];
  }

  // Step 4: Reverse suffix
  reverse(nums, i + 1, nums.length - 1);
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

### 🔍 **Explanation for `[1,2,3]`**:

1. Start from end: `3 > 2` → suffix is `3`
    
2. Pivot is `2`
    
3. Find next larger → `3`
    
4. Swap `2` and `3` → `[1,3,2]`
    
5. Reverse suffix (just `2`) → final result: `[1,3,2]`
    

---

### 🧠 What You Say in an Interview:

> “I identified the pivot — the first element that breaks the descending trend from the end.  
> Then I swapped it with the next higher number in the suffix and reversed the suffix to get the next permutation.”

---

### ✅ Edge Cases

- `[3,2,1]` → no higher permutation → return `[1,2,3]`
    
- Duplicates: handled naturally by comparison
    

---

### ⏱️ Time & Space Complexity

- **Time:** O(n)
    
- **Space:** O(1) — in-place
    

---
