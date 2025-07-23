Great! Let’s start with a beginner-friendly yet foundational sorting algorithm:

---

## 🔹 **Problem 1: Bubble Sort (with Early Exit Optimization)**

### 🧠 **Interview-style Question Statement:**

> Implement the **Bubble Sort algorithm** to sort an array of numbers in ascending order.
> 
> Add an optimization: If during a full pass no swaps are made, exit early — the array is already sorted.

---

### 🔸 Example:

```js
Input: [5, 1, 4, 2, 8]  
Output: [1, 2, 4, 5, 8]
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Compare adjacent elements and **swap** if they’re out of order.
    
- Repeat this until no more swaps are needed.
    

---

### ✅ **Optimized Bubble Sort Code**

```js
function bubbleSort(arr) {
  let n = arr.length;

  for (let i = 0; i < n - 1; i++) {
    let swapped = false;

    for (let j = 0; j < n - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        // Swap
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        swapped = true;
      }
    }

    // No swaps = array already sorted
    if (!swapped) break;
  }

  return arr;
}
```

---

### 🔍 **Explanation:**

- Outer loop controls the number of passes
    
- Inner loop compares adjacent elements
    
- The `swapped` flag helps us exit early if a pass does **no work**
    

---

### 🧪 Example Trace:

Input: `[3, 2, 1]`

- Pass 1: `[2, 1, 3]`
    
- Pass 2: `[1, 2, 3]`
    
- Pass 3: `swapped = false` → exit early ✅
    

---

### 🧠 What You Say in an Interview:

> “I implemented the standard Bubble Sort, but added a `swapped` flag to exit early if a pass does nothing — which improves best-case to O(n).”

---

### ⏱️ Time & Space Complexity

|Case|Time|Space|
|---|---|---|
|Best|O(n)|O(1)|
|Average|O(n²)|O(1)|
|Worst|O(n²)|O(1)|

---

Would you like to move on to **Problem 2: Search Insert Position (Binary Search)**?