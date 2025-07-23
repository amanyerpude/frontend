Perfect! Let's move on to:

---

## 🔹 **Problem 3: Minimum Absolute Difference**

### 🧠 **Interview-style Question Statement:**

> Given an array of integers, return **all pairs of elements** with the **minimum absolute difference** between them.
> 
> The result should be returned as an array of pairs sorted in increasing order.
> 
> If multiple pairs have the same minimum difference, return all of them.

---

### 🔸 Example:

```js
Input: [4, 2, 1, 3]  
Output: [[1, 2], [2, 3], [3, 4]]

Input: [1, 3, 6, 10, 15]  
Output: [[1, 3]]
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Find the **minimum absolute difference** between any two elements
    
- Return all **sorted pairs** with that difference
    

---

### ✅ **Efficient Approach: Sort & Scan Once**

```js
function minimumAbsDifference(arr) {
  arr.sort((a, b) => a - b); // Step 1: sort ascending

  let minDiff = Infinity;
  let result = [];

  for (let i = 0; i < arr.length - 1; i++) {
    const diff = arr[i + 1] - arr[i];

    if (diff < minDiff) {
      minDiff = diff;
      result = [[arr[i], arr[i + 1]]]; // reset
    } else if (diff === minDiff) {
      result.push([arr[i], arr[i + 1]]);
    }
  }

  return result;
}
```

---

### 🔍 **Explanation:**

- Sorting ensures **adjacent elements** give the smallest possible difference
    
- Keep track of the smallest difference seen so far (`minDiff`)
    
- If you find a smaller difference → reset result
    
- If it matches the minimum → add the pair
    

---

### 🧠 What You Say in an Interview:

> “I sorted the array so I could check adjacent pairs.  
> That guarantees I'm only checking the closest possible values.  
> Then I collected all pairs with the smallest difference in a single pass.”

---

### ⏱️ Time & Space Complexity

|Metric|Value|
|---|---|
|Time|O(n log n)|
|Space|O(n) (for result array)|

---

Ready for the final one in this set — **Problem 4: Relative Sort Array**?