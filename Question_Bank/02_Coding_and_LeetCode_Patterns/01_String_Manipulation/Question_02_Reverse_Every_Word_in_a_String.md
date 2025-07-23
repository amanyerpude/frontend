Great! Let's move on to **Question 2: Reverse Every Word in a String** — a frequent string manipulation task that checks your understanding of string splitting, joining, and in-place thinking.

---

## 🔹 **Question 2: Reverse Every Word in a String**

### 🧠 **Interview-style Question Statement:**

> Given a string, reverse each word individually **while keeping the word order the same**.
> 
> Example:  
> Input: `"hello world"`  
> Output: `"olleh dlrow"`

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

- Break the sentence into words
    
- Reverse each word
    
- Join the reversed words back into a sentence
    

---

### ✅ **Approach: Use `.split()`, `.map()`, and `.reverse()`**

```js
function reverseEachWord(str) {
  return str
    .split(' ')                        // Split sentence into words
    .map(word => word.split('').reverse().join('')) // Reverse each word
    .join(' ');                        // Join words back with space
}
```

---

### 🔍 **Explanation:**

1. `.split(' ')` → breaks the sentence into individual words
    
2. `.map()` → applies a function to each word
    
3. Inside `.map()`:
    
    - `word.split('')` → turns word into array of characters
        
    - `.reverse()` → reverses the character array
        
    - `.join('')` → converts array back into string
        
4. `.join(' ')` → reassembles the sentence with spaces
    

---

### 🧪 Example:

```js
reverseEachWord("hello world")
// → ["olleh", "dlrow"] → "olleh dlrow"
```

---

### 🧠 What You Say in an Interview:

> “I split the sentence into words, reversed each word individually, and then joined the reversed words back into a string. This approach is readable and efficient using built-in methods.”

---

### 🧪 Edge Cases:

- Multiple spaces → can be preserved using regex-based split if required
    
- Empty string → return empty string
    
- Tabs/newlines → may need normalization if specified
    

---

### ⏱️ Time & Space Complexity:

- **Time:** O(n)
    
- **Space:** O(n)
    

---

Shall we continue with **Question 3: Check for Anagram**?