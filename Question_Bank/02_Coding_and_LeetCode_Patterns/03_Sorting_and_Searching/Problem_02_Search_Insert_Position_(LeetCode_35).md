Great! Let’s move on to a very common **binary search variant** — often asked at FAANG and startups alike:

---

## 🔹 **Problem 2: Search Insert Position (LeetCode #35)**

### 🧠 **Interview-style Question Statement:**

> Given a **sorted array** of distinct integers and a target value, return the **index** if the target is found.
> 
> If not, return the **index where it would be inserted** in order.
> 
> You must use **binary search** (O(log n)).

---

### 🔸 Example:

```js
Input: nums = [1, 3, 5, 6], target = 5  
Output: 2

Input: nums = [1, 3, 5, 6], target = 2  
Output: 1

Input: nums = [1, 3, 5, 6], target = 7  
Output: 4
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Use binary search to find the **target**
    
- If not found, return the **index where it should go**
    

---

### ✅ **Binary Search Code (JS)**

```js
function searchInsert(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (nums[mid] === target) {
      return mid;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }

  // left is the correct insert position
  return left;
}
```

---

### 🔍 **Explanation:**

- If the element is found, return `mid`.
    
- If not, `left` is the index where the target **should be inserted** — it's the first index where `nums[i] > target`.
    

---

### 🧠 What You Say in an Interview:

> “I used a binary search approach. If the target isn't found, the left pointer ends up at the smallest index where the target could be inserted to maintain sorted order.”

---

### ⏱️ Time & Space Complexity

|Metric|Value|
|---|---|
|Time|O(log n)|
|Space|O(1)|

---

Would you like to continue with **Problem 3: Minimum Absolute Difference**?