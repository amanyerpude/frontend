
---

## 🔹 **Question 3: 2nd Max Number in an Array**

### 🧠 **Interview-style Question Statement:**

> Given an array of integers, return the **second largest unique number** in the array.
> 
> If there is no such number (e.g., all elements are the same), return `null` or a message like `"Not enough distinct elements"`.

### 🔸 Example:

```js
Input: [10, 5, 8, 10, 7]  
Output: 8

Input: [5, 5, 5]  
Output: null
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Find the **largest** number.
    
- Then find the **largest number that is smaller than that**.
    

---

### ✅ **Approach: Use two variables: `max` and `secondMax`**

```js
function findSecondMax(arr) {
  let max = -Infinity;
  let second = -Infinity;

  for (let num of arr) {
    if (num > max) {
      second = max;
      max = num;
    } else if (num > second && num < max) {
      second = num;
    }
  }

  return second === -Infinity ? null : second;
}
```

---

### 🔍 **Explanation:**

- You loop through the array once.
    
- `max` holds the largest number.
    
- `second` gets updated only if a number is:
    
    - less than `max`
        
    - and greater than the current `second`
        
- At the end, return `second`.
    

---

### 🧪 Example Walkthrough:

Input: `[10, 5, 8, 10, 7]`

- num = 10 → max = 10, second = -∞
    
- num = 5 → second = 5
    
- num = 8 → second = 8 (since 8 > 5 and < max)
    
- num = 10 → skip (not less than max)
    
- num = 7 → skip
    

➡️ Output = 8 ✅

---

### ❓ What If the Array Has Duplicates?

- Your loop will still work since it checks for uniqueness: `num < max`.
    

### ❓ What If the Array is Very Small?

```js
[5] → return null  
[5, 5] → return null  
[5, 8] → return 5 ✅
```

---

### 🧠 What You Say in an Interview:

> “I used two variables to track the largest and second largest numbers.  
> I ensured `secondMax` only updates for values less than the current max.  
> It runs in linear time and doesn’t need sorting or extra space.”

---

### 🔚 Time & Space Complexity

- **Time:** O(n) — one pass
    
- **Space:** O(1) — no extra storage
    

---

Want to try this yourself with input `[9, 1, 9, 2, 8, 8, 10]` and tell me what the second max is?

