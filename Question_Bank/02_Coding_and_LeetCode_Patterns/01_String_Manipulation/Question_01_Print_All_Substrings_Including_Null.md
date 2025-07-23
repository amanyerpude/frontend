Perfect, Shrey. Let’s start with **String Manipulation** — one of the most commonly tested topics in frontend interviews.

We’ll go problem by problem just like we did with arrays:  
Clear **question statement**, **beginner-friendly explanation**, and **clean JS code**.

---

## 🔹 **Question 1: Print All Substrings Including Null**

### 🧠 **Interview-style Question Statement:**

> Given a string `s`, print **all possible substrings**, including the empty string (`""`).
> 
> Example:  
> Input: `"gfg"`  
> Output: `["", "g", "gf", "gfg", "f", "fg", "g"]`

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- A **substring** is a continuous slice of a string.
    
- For a string of length `n`, total substrings = `n(n+1)/2 + 1` (if including the empty string).
    

---

### ✅ **Approach: Use Two Loops**

```js
function allSubstrings(str) {
  const result = ['']; // including empty string

  for (let i = 0; i < str.length; i++) {
    for (let j = i + 1; j <= str.length; j++) {
      result.push(str.slice(i, j));
    }
  }

  return result;
}
```

---

### 🔍 **Explanation:**

- Outer loop picks the **start index**
    
- Inner loop picks the **end index** (`j` is exclusive)
    
- `str.slice(i, j)` gives substring from `i` to `j-1`
    
- We include an empty string manually at the start
    

---

### 🧪 Example:

```js
allSubstrings("gfg") 
// ["", "g", "gf", "gfg", "f", "fg", "g"]
```

---

### 🧠 What You Say in an Interview:

> “I used a nested loop — the outer one selects the start of the substring and the inner one extends to each end position. I included the empty string separately. This gives all possible continuous substrings.”

---

### ⏱️ Time & Space Complexity:

- **Time:** O(n²)
    
- **Space:** O(n²) (since total substrings grow quadratically)
    

---

Let’s continue with **Question 2: Reverse Every Word in a String**?