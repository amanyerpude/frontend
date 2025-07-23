Great! Let’s begin with a **frequency map-based counting problem** — often asked to test your understanding of string analysis and hashmap usage.

---

## 🔹 **Problem 1: Maximum Number of Balloons**

### 🧠 **Interview-style Question Statement:**

> Given a string `text`, return the **maximum number of times** the word `"balloon"` can be formed using the letters in `text`.
> 
> Each letter in `text` can be used **only once per occurrence** of the word.

---

### 🔸 Example:

```js
Input: "nlaebolko"
Output: 1

Input: "loonbalxballpoon"
Output: 2

Input: "leetcode"
Output: 0
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Count how many complete `"balloon"`s can be formed from the given letters
    
- Use each letter **only once per occurrence**
    
- Note: `"balloon"` requires:
    
    - `b`: 1
        
    - `a`: 1
        
    - `l`: 2
        
    - `o`: 2
        
    - `n`: 1
        

---

### ✅ **Approach: Use a Frequency Map**

```js
function maxNumberOfBalloons(text) {
  const freq = {};

  for (let char of text) {
    freq[char] = (freq[char] || 0) + 1;
  }

  return Math.min(
    freq['b'] || 0,
    freq['a'] || 0,
    Math.floor((freq['l'] || 0) / 2),
    Math.floor((freq['o'] || 0) / 2),
    freq['n'] || 0
  );
}
```

---

### 🔍 **Explanation:**

- Count occurrences of each letter
    
- For letters that appear twice in “balloon” (`l`, `o`), divide their count by 2
    
- Take the minimum among all required letters — that’s how many full words we can build
    

---

### 🧠 What You Say in an Interview:

> “I built a frequency map of the input string. Then I checked how many times I can form ‘balloon’ by comparing required counts. For repeated letters like ‘l’ and ‘o’, I divided their frequency by 2.”

---

### ⏱️ Time & Space Complexity

|Metric|Value|
|---|---|
|Time|O(n)|
|Space|O(1) — only fixed-size map needed for 26 letters|

---

Ready to move on to **Problem 2: Prime Arrangements (`numPrimeArrangements`)**?