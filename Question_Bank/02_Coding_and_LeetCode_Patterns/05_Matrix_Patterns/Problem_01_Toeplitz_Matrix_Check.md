Great! Let’s dive into a classic matrix pattern recognition problem — often asked to test your **looping control and diagonal thinking**:

---

## 🔹 **Problem: Toeplitz Matrix Check**

### 🧠 **Interview-style Question Statement:**

> A matrix is called a **Toeplitz matrix** if every diagonal from **top-left to bottom-right** has the **same element**.
> 
> Write a function `isToeplitzMatrix(matrix)` that returns `true` if the matrix is Toeplitz; otherwise, return `false`.

---

### 🔸 Example:

```js
Input:
[
  [1, 2, 3, 4],
  [5, 1, 2, 3],
  [9, 5, 1, 2]
]

Output: true ✅
```

Because:

- All diagonals:
    
    - `[1]`, `[2,1]`, `[3,2,1]`, `[4,3,2]` etc.
        
    - Have identical values along the same diagonal
        

---

### ❌ Counter Example:

```js
[
  [1, 2],
  [2, 2]
]
```

Here, diagonal `[1,2]` ≠ `[2]`, so it's **not** a Toeplitz matrix → returns `false`.

---

## 🧱 **Step-by-Step Beginner-Friendly Explanation**

### 🎯 Your Goal:

For every element (except the last row and last column), check:

- `matrix[i][j] === matrix[i+1][j+1]`
    

---

### ✅ **Implementation in JavaScript**

```js
function isToeplitzMatrix(matrix) {
  const rows = matrix.length;
  const cols = matrix[0].length;

  for (let i = 0; i < rows - 1; i++) {
    for (let j = 0; j < cols - 1; j++) {
      if (matrix[i][j] !== matrix[i + 1][j + 1]) {
        return false;
      }
    }
  }

  return true;
}
```

---

### 🔍 Explanation:

- You stop at `rows - 1` and `cols - 1` because you compare each cell with the one diagonally down-right
    
- If any mismatch is found → return `false`
    

---

### 🧠 What You Say in an Interview:

> “I compared each element with the one diagonally below and to the right.  
> If they all match, the matrix is Toeplitz.  
> This runs in O(m × n) time and uses no extra space.”

---

### ⏱️ Time & Space Complexity

|Metric|Value|
|---|---|
|Time|O(m × n)|
|Space|O(1)|

---

Would you like to continue with more matrix-based problems like:

- Diagonal traversal
    
- Spiral matrix
    
- Matrix rotation
    
- Zigzag or wave print?
    

Or close this topic here?