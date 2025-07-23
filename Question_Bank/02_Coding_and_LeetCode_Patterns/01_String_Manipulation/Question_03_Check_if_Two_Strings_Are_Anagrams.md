Awesome! Let’s now work through **Question 3: Check for Anagram** — a staple string question that tests your grasp of sorting, character frequency, and equality checks.

---

## 🔹 **Question 3: Check if Two Strings Are Anagrams**

### 🧠 **Interview-style Question Statement:**

> Given two strings, return `true` if they are anagrams of each other, otherwise return `false`.  
> Two strings are anagrams if they contain the same characters in the same frequencies, just in different orders.
> 
> Example:  
> `isAnagram("listen", "silent")` → `true`  
> `isAnagram("rat", "car")` → `false`

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Compare two strings to see if **all characters** match — regardless of order
    

---

### ✅ **Approach: Sort & Compare**

```js
function isAnagram(str1, str2) {
  const normalize = str => str.split('').sort().join('');
  return normalize(str1) === normalize(str2);
}
```

---

### 🔍 **Explanation:**

1. `.split('')` → converts string to array of characters
    
2. `.sort()` → arranges characters alphabetically
    
3. `.join('')` → combines characters back into a string
    
4. Compare the sorted versions — if equal, they’re anagrams
    

---

### 🧪 Examples:

```js
isAnagram("listen", "silent") // true
isAnagram("rat", "car")       // false
```

---

### 🧠 What You Say in an Interview:

> “To check if two strings are anagrams, I sorted both strings and compared them.  
> Sorting ensures all characters are in the same order, so equality means they’re anagrams.”

---

### ⚠️ Edge Cases to Discuss:

- **Case sensitivity**: `"Listen"` vs `"Silent"` → are they anagrams?
    
- **Spaces or punctuation**: `"a gentleman"` vs `"elegant man"` — do we normalize those?
    
- To handle case/whitespace:
    

```js
str.toLowerCase().replace(/\s/g, '')
```

---

### 🔁 Alternate Approach (Frequency Map – if sorting not allowed)

```js
function isAnagram(str1, str2) {
  if (str1.length !== str2.length) return false;

  const count = {};

  for (let char of str1) {
    count[char] = (count[char] || 0) + 1;
  }

  for (let char of str2) {
    if (!count[char]) return false;
    count[char]--;
  }

  return true;
}
```

---

### ⏱️ Time & Space Complexity

|Method|Time|Space|
|---|---|---|
|Sort + Compare|O(n log n)|O(1)|
|Frequency Map|O(n)|O(n)|

---

Ready to wrap up with **Question 4: Palindrome Check (Ignore Punctuation, Case-insensitive)**?