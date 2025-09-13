## Coding & LeetCode Patterns - Categorized

### 🔹 Array Manipulation

- Remove Duplicates From An Array
    
    - Code using Set and Two Pointer approach
        
- Remove Element (LeetCode)
    
    - Original problem: `Remove Element`
        
- 2nd Max Number from an Array
    
- Deep Merge of Two Objects
    
    - Original problem: `Deep Merge`
        
- Array Flattening (recursive and .flat)
    
    - Original problem: `item.flat(Infinity)` and recursive helper function
        
- Divide Array in Chunks (two methods)
    
    - Original problem: `chunks(item, chunk)`
        
- Rotate Array by K
    

### 🔸 String Manipulation

- Print All Substrings Including null (Set-based)
    
    - Original problem: `allSubstrings("gfg")`
        
- Reverse Every Word in a String
    
    - Original problem: `Reverse every word of a string`
        
- Check for Anagram (sort and compare method)
    
    - Original problem: `isAnagram("rat", "car")`
        
- Palindrome Check (ignore punctuation, case-insensitive)
    
    - Original problem: `isPalindrome("A man, a plan, a canal, Panama!")`
        

### 🔶 Recursion & Backtracking

- Parenthesis Pairing (generate valid n-pairs)
    
    - Original problem: `getpair(3)`
        
- Next Permutation (LeetCode)
    
    - Original problem: `nextPermutation(nums)`
        

### 🟢 Sorting & Searching

- Bubble Sort (with early exit)
    
    - Original problem: `bubbleSort(arr)`
        
- Search Insert Position (binary search)
    
    - Original problem: `searchInsert(nums, target)`
        
- Minimum Absolute Difference
    
- Relative Sort Array (Map + custom sort)
    
    - Original problem: `relativeSortArray(arr1, arr2)`
        

### 🟡 Math and Logical Patterns

- Maximum Number of Balloons (frequency map)
    
    - Original problem: `maxNumberOfBalloons(text)`
        
- Prime Arrangements (modular factorial)
    
    - Original problem: `numPrimeArrangements(n)`
        

### 🟣 Optimization & Memoization

- Memoization Function (custom useMemo logic in JS)
    
    - Original implementation: `memoize(fn)`
        

### 🟠 React Coding Challenges

- React JS Counter (auto increment with direction flip)
    
    - Original title: `React Js Counter`
        
- Counter that counts till 10, pauses, then resumes next range
    
    - Original: `Counter till 10 then next 10 etc. (TEKsystems 2nd round)`
        

### 🧮 Matrix Patterns

- Toeplitz Matrix Check
    
    - Original problem: `isToeplitzMatrix(matrix)`
      
      
# ❓ **Interview Question**

**Write a JavaScript program to print only the vowels from a string.**  
**Example:**  
Input → `"hellow world"`  
Output → `e, o, o`

---

### ✅ **Step-by-Step Approach**

#### **1️⃣ Understand the Problem**

- We need to extract only vowels (`a, e, i, o, u`) from a given string.
    
- Output should be a comma-separated list.
    

#### **2️⃣ Approach Explanation (to say to the interviewer)**

👉 _“I’ll iterate through each character of the string, check if it’s a vowel, and collect it in an array. Finally, I’ll join the vowels with commas and print the result. I’ll use a `Set` for faster lookup (O(1)).”_

---

### ✅ **Code Solution (Readable)**

```javascript
function printVowels(str) {
  const vowels = new Set(['a', 'e', 'i', 'o', 'u']);
  const result = [];

  for (let char of str.toLowerCase()) {
    if (vowels.has(char)) {
      result.push(char);
    }
  }

  console.log(result.join(', '));
}

// Example
printVowels("hellow world"); // Output: e, o, o
```

---

### ✅ **One-Liner Solution (Using Regex)**

```javascript
console.log("hellow world".match(/[aeiou]/gi).join(", ")); // e, o, o
```

👉 _“This uses `match()` with a regex to extract vowels directly and `join()` to format the result.”_

---

### ✅ **Complexity**

- **Time Complexity** → O(n) (We iterate over each character once)
    
- **Space Complexity** → O(k) (Where k is the number of vowels found)
    

---

### ✅ **How to Communicate in the Interview**

🔹 _“I first implemented a simple loop-based approach for readability.  
If we need a shorter solution, we can use regex with `match()` to directly extract vowels.  
Both solutions are O(n) time. The regex version is concise but less explicit in logic.”_

---

🔥 If the interviewer asks for **further optimisation**, you can say:  
👉 _“Since we already need to check every character, we can’t go below O(n).  
But we can avoid storing the vowels and print them directly inside the loop if memory is a concern.”_

---

# ❓ **Interview Question**

You are given the following JavaScript code:

```javascript
for (var/let i = 0; i < 5; i++) {
  setTimeout(() => console.log("i", i), 0);
}
```

#### **Questions to Answer:**

1️⃣ What will be the **output** of the above code?  
2️⃣ **Why does this output occur?** (Explain event loop, closures, and scope)  
3️⃣ How would the output differ if we use `var` vs `let`?

---

## ✅ **Step 1: Understanding the Problem**

This question tests **closures**, **scope (`var` vs `let`)**, and **how the event loop works with asynchronous tasks (`setTimeout`)**.

---

## ✅ **Answer 1: What will be the output?**

### 🔹 **Case 1 – Using `var`**

```
i 5
i 5
i 5
i 5
i 5
```

### 🔹 **Case 2 – Using `let`**

```
i 0
i 1
i 2
i 3
i 4
```

---

## ✅ **Answer 2: Why does this happen?**

### 🔹 **Using `var`**

- `var` is **function-scoped**, so the **same `i` variable is shared** across all iterations.
    
- By the time `setTimeout` callbacks execute, the loop has already completed, and `i` has become `5`.
    
- Hence, all logs print `5`.
    

### 🔹 **Using `let`**

- `let` is **block-scoped**, so **each iteration has its own copy of `i`**.
    
- The closure inside `setTimeout` “remembers” the correct value of `i` for that iteration.
    
- Hence, logs print `0, 1, 2, 3, 4`.
    

---

## ✅ **Event Loop Explanation**

- `setTimeout` is an **asynchronous task**.
    
- The callback is pushed to the **callback queue** after `0ms`.
    
- But the **event loop** executes it **only after the synchronous code (the loop) finishes execution**.
    
- That’s why in the `var` case, all callbacks run **after the loop**, so they see `i = 5`.
    

---

## ✅ **Answer 3: How would you fix it for `var`?**

### 🔹 **Method 1 – Use `let` (Simplest Fix)**

```javascript
for (let i = 0; i < 5; i++) {
  setTimeout(() => console.log("i", i), 0);
}
```

### 🔹 **Method 2 – Use IIFE (Closure with `var`)**

```javascript
for (var i = 0; i < 5; i++) {
  ((x) => setTimeout(() => console.log("i", x), 0))(i);
}
```

👉 This creates a **new copy of `i`** (`x`) for each iteration.

---

## ✅ **How to Explain in the Interview**

💬 **Sample Answer (Think-Aloud)**

> “When using `var`, it is function-scoped, so all iterations share the same `i`. By the time the `setTimeout` callbacks execute, the loop is over, and `i` is `5`.
> 
> Using `let`, which is block-scoped, creates a new binding of `i` for each iteration, so the callbacks remember the correct value.
> 
> The reason this happens is because `setTimeout` is asynchronous – the callbacks execute after the synchronous code finishes due to the event loop.
> 
> To fix it while using `var`, I can wrap the callback in an IIFE and pass `i` as a parameter, so each callback gets its own copy of `i`.”

---

## ✅ **Follow-Up Questions Interviewer Might Ask**

🔹 How does **closure** make the correct value of `i` available?  
🔹 What is the difference between **macro-task (`setTimeout`)** and **micro-task (`Promise`)** in the event loop?  
🔹 Can we achieve the same output using `bind` or `Function.prototype.call`?

---
# ❓ **Interview Question – Sorting a Mixed Array**

📌 **Task:**  
Sort the following array that contains both **strings** and **numbers**:

```javascript
const arr = ['a', 'c', 'y', 'u', 2];
```

---

### ✅ **Points to Cover**

1️⃣ Write JavaScript code to sort this array correctly.
2️⃣ Explain how JavaScript handles sorting when data types are mixed.
3️⃣ Show how to sort **alphabetically first and then numerically (or vice versa)**.

---

## ✅ **Answer 1 – Default Sorting in JavaScript**

```javascript
const arr = ['a', 'c', 'y', 'u', 2];
console.log(arr.sort()); 
// Output: [2, "a", "c", "u", "y"]
```

### 🔹 **Why?**

- `sort()` **converts all elements to strings** and sorts them **lexicographically (dictionary order)**.
    
- So `2` becomes `"2"`, and sorting happens alphabetically → `"2" < "a"`.
    

---

## ✅ **Answer 2 – Sorting Numbers and Strings Separately**

### **Alphabetically First → Then Numerically**

```javascript
const arr = ['a', 'c', 'y', 'u', 2];

const sorted = arr.sort((a, b) => {
  const isANum = typeof a === "number";
  const isBNum = typeof b === "number";

  if (isANum && !isBNum) return 1;  // Numbers go last
  if (!isANum && isBNum) return -1; // Strings go first

  return a > b ? 1 : -1; // Normal sorting within same type
});

console.log(sorted); 
// Output: ["a", "c", "u", "y", 2]
```

---

### **Numerically First → Then Alphabetically**

```javascript
const arr = ['a', 'c', 'y', 'u', 2];

const sorted = arr.sort((a, b) => {
  const isANum = typeof a === "number";
  const isBNum = typeof b === "number";

  if (isANum && !isBNum) return -1; // Numbers go first
  if (!isANum && isBNum) return 1;  // Strings go last

  return a > b ? 1 : -1; // Normal sorting within same type
});

console.log(sorted); 
// Output: [2, "a", "c", "u", "y"]
```

---

## ✅ **How JavaScript Handles Sorting When Types Are Mixed**

- The default `sort()` converts **everything to strings** and sorts **lexicographically**.
    
- `"2"` comes before `"a"` because `"2"` has a lower Unicode value.
    
- To get meaningful sorting, we need to **explicitly handle types** in the comparator.
    

---

## ✅ **How to Explain to Interviewer**

💬 **Sample Answer:**

> “By default, JavaScript’s `sort()` converts all elements to strings and sorts lexicographically. That’s why `2` is treated as `"2"`, coming before `"a"`.
> 
> To properly sort mixed arrays, I use a custom comparator inside `sort()`. I first check the type of each element. Depending on whether I want strings or numbers first, I return `-1` or `1`. Finally, I sort elements of the same type normally using `a > b ? 1 : -1`.
> 
> This approach gives me full control over sorting order.”

---

### 🔹 **Follow-Up Questions They Might Ask**

✅ What if the array has **multiple numbers**?  
✅ How would you **sort numbers in ascending order but strings in reverse alphabetical order**?  
✅ Can you write a **generic function** that sorts any mixed array?

---

### ❓ **Interview Question – Working with Array Methods**

📌 **Task:**  
Given the array:

```javascript
const A = ['s', 't', 'r', 'l', 'n', 'g', 's'];
```

---

### ✅ **Sub-Tasks to Solve**

1️⃣ Find **all positions (indexes)** of character `'s'`.  
2️⃣ Change the character `'l'` to **uppercase** (or lowercase if applicable).

---

## ✅ **Answer 1 – Find All Positions of `'s'`**

### 🔹 **Code Using `map()` + `filter()`**

```javascript
const A = ['s', 't', 'r', 'l', 'n', 'g', 's'];

const indexes = A
  .map((ch, i) => (ch === 's' ? i : -1))
  .filter(i => i !== -1);

console.log(indexes); // Output: [0, 6]
```

### 🔹 **Alternative Using `reduce()`**

```javascript
const indexes = A.reduce((acc, ch, i) => {
  if (ch === 's') acc.push(i);
  return acc;
}, []);

console.log(indexes); // Output: [0, 6]
```

---

## ✅ **Answer 2 – Change `'l'` to Uppercase**

### 🔹 **Code Using `map()`**

```javascript
const updatedArray = A.map(ch => (ch === 'l' ? ch.toUpperCase() : ch));

console.log(updatedArray); 
// Output: ['s', 't', 'r', 'L', 'n', 'g', 's']
```

---

## ✅ **Explanation (to Say to Interviewer)**

💬 **Sample Answer:**

> “For finding all indexes of `'s'`, I used `map()` to create an array of indexes or `-1`, then filtered out `-1`. Alternatively, I could use `reduce()` to build an array directly.
> 
> For changing `'l'` to uppercase, I used `map()` to iterate over elements and replace `'l'` with `ch.toUpperCase()`.
> 
> Both solutions are clean, functional, and avoid manual loops.”

---

## ✅ **Time Complexity**

- **Finding indexes** → O(n) (Iterate once through array)
    
- **Changing character** → O(n) (Iterate once through array)
    

---

## 🔹 **Follow-Up Questions Interviewer May Ask**

✅ How would you **find positions of multiple characters at once?**  
✅ Can you **mutate the original array instead of creating a new one?**  
✅ What if the array has **strings longer than 1 character**?

---
# ❓ **Interview Question – Counting Repeated Characters**

📌 **Task:**  
Given the array:

```javascript
const A = ['a', 'm', 'e', 't', 'y', 'a', 'm'];
```

🔹 **Requirement:**  
Write code to **count the number of repeated characters** **without using any inbuilt functions like `reduce`, `filter`, or `map`**.

✅ **Goal:** Test ability to **implement logic manually using loops, objects, or maps**.

---

## ✅ **Answer – Using a Simple `for` Loop and Object**

```javascript
const A = ['a', 'm', 'e', 't', 'y', 'a', 'm'];

const freq = {};
for (let i = 0; i < A.length; i++) {
  const ch = A[i];
  if (freq[ch]) {
    freq[ch]++; // Increment if exists
  } else {
    freq[ch] = 1; // Initialise count
  }
}

console.log(freq); 
// Output: { a: 2, m: 2, e: 1, t: 1, y: 1 }

// Find only repeated characters
for (let key in freq) {
  if (freq[key] > 1) {
    console.log(`${key} is repeated ${freq[key]} times`);
  }
}
```

---

## ✅ **Output**

```
a is repeated 2 times
m is repeated 2 times
```

---

## ✅ **How to Explain to Interviewer**

💬 **Sample Answer:**

> “Since I can’t use `reduce`, `filter`, or `map`, I implemented manual counting using a plain object.  
> I iterated through the array using a `for` loop, checked if the character already exists in the object, and incremented its count. Finally, I printed only the keys where the count is greater than 1.”

---

## ✅ **Time & Space Complexity**

- **Time Complexity** → O(n) (We traverse the array once)
    
- **Space Complexity** → O(k) (Where k is the number of unique characters)
    

---

## 🔹 **Possible Follow-Up Questions**

✅ How would you **return only the first repeated character?**  
✅ How would you **solve this if the input was a string instead of an array?**  
✅ Can you do this using a **Map instead of an Object?**

---
# ❓ **Interview Question – Sum of Elements in an Array**

📌 **Task:**  
Write code to **calculate the sum of all elements** in an array.

Example:

```javascript
const arr = [1, 2, 3, 4, 5];
```

---

## ✅ **Answer 1 – Using `reduce()` (Concise Way)**

```javascript
const arr = [1, 2, 3, 4, 5];

const sum = arr.reduce((acc, curr) => acc + curr, 0);

console.log(sum); // 15
```

🔎 **Explanation:**

- `reduce()` iterates over each element, accumulating the sum.
    
- `acc` = accumulator (total sum so far), `curr` = current element.
    
- Initial value = `0`.
    

---

## ✅ **Answer 2 – Using `for` Loop (Manual Implementation)**

```javascript
const arr = [1, 2, 3, 4, 5];
let sum = 0;

for (let i = 0; i < arr.length; i++) {
  sum += arr[i];
}

console.log(sum); // 15
```

---

## ✅ **Answer 3 – Using `for...of` Loop**

```javascript
const arr = [1, 2, 3, 4, 5];
let sum = 0;

for (let num of arr) {
  sum += num;
}

console.log(sum); // 15
```

---

## ✅ **How to Explain to Interviewer**

💬 **Sample Answer:**

> “The easiest way is to use `reduce()`, which iterates over the array and keeps adding each element to an accumulator.  
> Alternatively, I can use a simple `for` loop to manually sum up elements.  
> Both approaches have **O(n)** time complexity and **O(1)** space complexity.”

---

### 🔹 **Follow-Up Questions They May Ask**

✅ How would you **find the average instead of sum?**  
✅ How would you **sum only even numbers?**  
✅ Can you **write this without using any inbuilt functions?**

---
# ❓ **Interview Question – Filtering Numbers and Using `reduce()` in JavaScript**

📌 **Task:**  
Given an array containing both strings and numbers, perform the following:

- ✅ Extract only the numeric elements into a new array using `filter()`.
    
- ✅ Using the original array, create a single string of numbers separated by hyphens (`-`) **using the `reduce()` method** (without `join()`), ignoring non-numeric elements.
    

## ✅ **Example Input**

javascript

`const arr = ['one', 'two', 'three', 'four', 1, 2, 3, 4];`

## ✅ **1️⃣ Filter Numbers Using `filter()`**

javascript

`const onlyNumberArray = arr.filter(item => typeof item === 'number'); console.log(onlyNumberArray); // Output: [1, 2, 3, 4]`

🔎 **Explanation:**

- The `filter()` method creates a new array with all elements that satisfy the condition.
    
- Here, the condition `typeof item === 'number'` ensures only numbers are kept.
    
- Non-number elements ('one', 'two', 'three', 'four') are ignored.
    

## ✅ **2️⃣ Concatenate Numbers as Hyphen-Separated String Using `reduce()`**

javascript

`const output = arr.reduce((acc, curr) => {   if (typeof curr === 'number') {    return acc === '' ? curr.toString() : acc + '-' + curr;  }  return acc; }, ''); console.log(output); // Output: "1-2-3-4"`

🔎 **Explanation:**

- We initialize the accumulator (`acc`) as an empty string `''`.
    
- For every element (`curr`) in the array:
    
    - If it’s a number, append it to the accumulator string.
        
    - If the accumulator is empty, just add the number as a string (`curr.toString()`).
        
    - Otherwise, append a hyphen followed by the number.
        
- Non-number elements are ignored and do not modify the accumulator.
    
- This approach avoids starting or ending the output with a hyphen.
    

## ✅ **3️⃣ Edge Cases to Consider**

- **Empty array:** Returns an empty string `''`.
    
- **Array with no numbers:** Outputs an empty string `''`.
    
- **Array with one number:** Outputs that number as a string, without hyphens.
    
- Mixed data types other than string/number will be ignored as well.
    

## ✅ **4️⃣ Time and Space Complexity**

- **Time Complexity:** O(n), where n is the length of the input array. Both `filter()` and `reduce()` iterate through the array once.
    
- **Space Complexity:** O(n) for the filtered array of numbers (in the `filter()` step). The `reduce()` step accumulates a string and doesn’t create additional arrays.
    

## ✅ **How to Explain in Interview**

💬 **Sample Answer:**

> “The problem requires extraction of numbers from a mixed array and then transforming them into a formatted string. I use `filter()` here for clarity and readability to get only the numbers, which is convenient for direct access.  
> For concatenation, the requirement to use `reduce()` forces me to build the string manually. I start with an empty string and append numbers separated by hyphens as I iterate through the array. I handle the first element separately to avoid leading hyphens.  
> This approach handles mixed data types gracefully by skipping non-numbers. It’s efficient with a linear time complexity, iterating over the array only once in each step.”

## 🔹 **Follow-Up Questions**

✅ Can you perform the filtering and concatenation in a single `reduce()` call without using `filter()`?  
✅ How would you modify the solution to handle floating point numbers or numeric strings?  
✅ What if the separator needed to be configurable instead of fixed as `-`?  
✅ How would you handle large arrays where memory is a constraint?

--------------------------------------------------------------------------

# ❓ **Interview Question – Hoisting in JavaScript**

📌 **Task:**  
Explain **hoisting** for `var`, `let`, `const`, and function declarations with examples.

---

## ✅ **What is Hoisting?**

Hoisting is JavaScript's default behavior of **moving declarations to the top of their scope (global or function scope)** during the compilation phase.

⚠️ **Only declarations are hoisted, not initializations.**

---

## ✅ **1️⃣ Hoisting with `var`**

```javascript
console.log(a); // undefined
var a = 10;
```

🔎 **Explanation:**

- `var` declarations are **hoisted and initialized with `undefined`**.
    
- At runtime, the value is assigned after the declaration line.
    

---

## ✅ **2️⃣ Hoisting with `let` and `const`**

```javascript
console.log(b); // ReferenceError
let b = 20;

console.log(c); // ReferenceError
const c = 30;
```

🔎 **Explanation:**

- `let` and `const` are also **hoisted**, but they are in the **Temporal Dead Zone (TDZ)** until their declaration line is reached.
    
- Accessing them **before declaration** throws **ReferenceError**.
    

---

## ✅ **3️⃣ Hoisting with Function Declarations**

```javascript
greet(); // "Hello"

function greet() {
  console.log("Hello");
}
```

🔎 **Explanation:**

- Function **declarations** are fully hoisted.
    
- Both the function **name and body** are available before the line where it is written.
    

---

## ✅ **4️⃣ Hoisting with Function Expressions**

```javascript
sayHi(); // TypeError: sayHi is not a function

var sayHi = function () {
  console.log("Hi");
};
```

🔎 **Explanation:**

- `sayHi` is declared as `var`, so it is hoisted **but initialized as `undefined`**.
    
- Calling `sayHi()` before initialization gives **TypeError**.
    

---

## ✅ **How to Explain to Interviewer**

💬 **Sample Answer:**

> “JavaScript hoists all declarations during the compilation phase.  
> `var` is hoisted and initialized with `undefined`.  
> `let` and `const` are hoisted but remain in the **temporal dead zone**, so accessing them before declaration throws a ReferenceError.  
> Function declarations are fully hoisted, but function expressions behave like variables – they are hoisted but not initialized until runtime.”

---

## 🔹 **Follow-Up Questions**

✅ Why does `let`/`const` have a **temporal dead zone**?  
✅ What happens if you define a function using `var` vs `let`?  
✅ How does hoisting affect arrow functions?

---

# ❓ **Interview Question – `this` Binding in JavaScript**

📌 **Task:**  
Show how `this` behaves in different contexts:

- ✅ Global context
    
- ✅ Object methods
    
- ✅ Arrow functions
    
- ✅ Event handlers
    

---

## ✅ **1️⃣ `this` in Global Context**

```javascript
console.log(this); // Browser: Window | Node.js: {}
```

🔎 **Explanation:**

- In browsers, the global object is `window`, so `this === window`.
    
- In strict mode (`'use strict'`), `this` is `undefined` in the global scope.
    

---

## ✅ **2️⃣ `this` in Object Methods**

```javascript
const obj = {
  name: "John",
  greet: function () {
    console.log(this.name);
  },
};

obj.greet(); // John
```

🔎 **Explanation:**

- When a function is called as a method (`obj.greet()`),  
    `this` refers to the **object before the dot (`obj`)**.
    

---

## ✅ **3️⃣ `this` in Arrow Functions**

```javascript
const obj = {
  name: "John",
  greet: () => {
    console.log(this.name);
  },
};

obj.greet(); // undefined
```

🔎 **Explanation:**

- Arrow functions **do not have their own `this`**.
    
- They inherit `this` from their **lexical scope** (the enclosing scope).
    
- Here, `this` is the global object, so `this.name` is `undefined`.
    

---

### ✅ **Arrow Function Inside a Method**

```javascript
const obj = {
  name: "John",
  greet: function () {
    const arrow = () => console.log(this.name);
    arrow();
  },
};

obj.greet(); // John
```

🔎 **Explanation:**

- The arrow function inherits `this` from the surrounding **regular function**, so it works as expected.
    

---

## ✅ **4️⃣ `this` in Event Handlers**

```html
<button id="btn">Click Me</button>
<script>
  document.getElementById("btn").addEventListener("click", function () {
    console.log(this); // <button> element
  });

  document.getElementById("btn").addEventListener("click", () => {
    console.log(this); // window (lexical scope)
  });
</script>
```

🔎 **Explanation:**

- In a **regular function**, `this` refers to the element that triggered the event.
    
- In an **arrow function**, `this` refers to the outer lexical scope (likely `window`).
    

---

## ✅ **How to Explain in Interview**

💬 **Sample Answer:**

> “The value of `this` depends on **how a function is called**, not where it’s defined.  
> In the global scope, `this` is the global object (or undefined in strict mode).  
> In object methods, `this` refers to the object before the dot.  
> Arrow functions don’t have their own `this` and instead inherit from their lexical scope.  
> In event handlers, `this` points to the element for regular functions but stays lexical for arrow functions.”

---

## 🔹 **Follow-Up Questions**

✅ What happens if you use `this` inside `setTimeout`?  
✅ How does `bind()`, `call()`, and `apply()` change `this`?  
✅ Why is `this` undefined inside class methods when used as callbacks?

---


# ❓ **Interview Question – Type Conversion in JavaScript**

📌 **Task:**  
Show examples of converting values between different types:

- String → Number
    
- Number → String
    
- Boolean ↔ Number/String
    

✅ **Goal:** Test understanding of **explicit and implicit type conversions** in JavaScript.

---

## ✅ **Answer – Examples with Explanation**

### 🔹 **1️⃣ String → Number**

```javascript
console.log(Number("123"));   // 123 (explicit conversion)
console.log(+"123");          // 123 (unary plus operator)
console.log(parseInt("123")); // 123 (integer parsing)
console.log(parseFloat("12.34")); // 12.34 (float parsing)
console.log(Number("abc"));   // NaN (invalid conversion)
```

---

### 🔹 **2️⃣ Number → String**

```javascript
console.log(String(123));     // "123" (explicit conversion)
console.log((123).toString()); // "123" (method)
console.log(123 + "");        // "123" (implicit conversion due to concatenation)
```

---

### 🔹 **3️⃣ Boolean → Number/String**

```javascript
console.log(Number(true));  // 1
console.log(Number(false)); // 0

console.log(String(true));  // "true"
console.log(String(false)); // "false"
```

---

### 🔹 **4️⃣ Number/String → Boolean**

```javascript
console.log(Boolean(0));      // false (0 is falsy)
console.log(Boolean(1));      // true (non-zero is truthy)
console.log(Boolean(""));     // false (empty string is falsy)
console.log(Boolean("hello")); // true (non-empty string is truthy)
```

---

## ✅ **Explanation of Output**

💬 **Sample Answer (to Say to Interviewer):**

> “JavaScript has both explicit and implicit type conversions.
> 
> - `Number(value)` converts strings to numbers, returning `NaN` for invalid strings.
>     
> - `String(value)` or `value.toString()` converts numbers or booleans to strings.
>     
> - Boolean conversion follows **truthy/falsy rules** → `0`, `""`, `null`, `undefined`, `NaN` are falsy, everything else is truthy.
>     
> 
> I also showed implicit conversions, such as using the unary `+` operator for number conversion and concatenating with `""` to convert to a string.”

---

## ✅ **Complexity**

- These are **built-in operations**, so they are **O(1)**.
    

---

## 🔹 **Follow-Up Questions Interviewer Might Ask**

✅ What is the difference between `parseInt("12abc")` and `Number("12abc")`?  
✅ How does `==` vs `===` behave during type coercion?  
✅ What are truthy and falsy values in JavaScript?

---