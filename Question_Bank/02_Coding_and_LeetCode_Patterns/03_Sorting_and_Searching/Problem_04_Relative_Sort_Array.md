Awesome! Let's finish the set with a slightly advanced and **real-world-relevant sorting problem**.

---

## 🔹 **Problem 4: Relative Sort Array**

(LeetCode #1122)

### 🧠 **Interview-style Question Statement:**

> You are given two arrays: `arr1` and `arr2`.
> 
> - `arr2` contains distinct elements and is a **subset of arr1**.
>     
> 
> Sort `arr1` so that:
> 
> 1. The relative order of items in `arr1` is the **same as in `arr2`** for elements that exist in `arr2`.
>     
> 2. The remaining elements not in `arr2` are placed at the end in **ascending order**.
>     

---

### 🔸 Example:

```js
Input:
arr1 = [2,3,1,3,2,4,6,7,9,2,19]  
arr2 = [2,1,4,3,9,6]

Output:
[2,2,2,1,4,3,3,9,6,7,19]
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Custom sort `arr1` so that:
    
    - Elements from `arr2` appear in the same order and frequency as in `arr1`
        
    - Remaining elements appear sorted
        

---

### ✅ **Approach: Use a Frequency Map + Custom Sort**

```js
function relativeSortArray(arr1, arr2) {
  const count = new Map();

  // Count frequencies of arr1 elements
  for (let num of arr1) {
    count.set(num, (count.get(num) || 0) + 1);
  }

  const result = [];

  // Add elements from arr2 in the correct order
  for (let num of arr2) {
    let freq = count.get(num);
    for (let i = 0; i < freq; i++) {
      result.push(num);
    }
    count.delete(num); // remove it once processed
  }

  // Handle remaining elements
  const remaining = [];

  for (let [num, freq] of count) {
    for (let i = 0; i < freq; i++) {
      remaining.push(num);
    }
  }

  remaining.sort((a, b) => a - b);

  return result.concat(remaining);
}
```

---

### 🔍 **Explanation:**

1. Count all elements in `arr1` using a map
    
2. Process `arr2` to push those elements in order (with frequency)
    
3. Collect and sort remaining items not in `arr2`
    
4. Merge both parts
    

---

### 🧠 What You Say in an Interview:

> “I used a frequency map to track occurrences of all numbers.  
> I processed elements of `arr2` first to preserve their order, then sorted and appended the leftovers.”

---

### ⏱️ Time & Space Complexity

|Metric|Value|
|---|---|
|Time|O(n log n) — due to sorting remainder|
|Space|O(n) — for map and result|

---

That wraps up your **Sorting & Searching** set ✅