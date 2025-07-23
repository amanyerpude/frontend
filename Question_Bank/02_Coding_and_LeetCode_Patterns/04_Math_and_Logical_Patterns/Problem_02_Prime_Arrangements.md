Awesome! Let’s tackle a number theory + modular arithmetic problem:

---

## 🔹 **Problem 2: Prime Arrangements**

### 🧠 **Interview-style Question Statement:**

> Given an integer `n`, return the number of valid **prime arrangements** of numbers from `1` to `n`.
> 
> A valid arrangement is one where **prime numbers occupy only prime indices** (1-based index).
> 
> Since the answer can be large, return the result **modulo 10⁹ + 7**.

---

### 🔸 Example:

```js
Input: 5  
Output: 12

Explanation: There are 3 prime numbers ≤ 5 → [2, 3, 5]  
So place them in any of the 3 prime indices → 3!  
Place non-primes (1, 4) in remaining indices → 2!  
Answer = 3! * 2! = 6 × 2 = 12
```

---

## 🧱 **Step-by-Step Beginner Explanation**

### 🎯 Your Goal:

1. Count how many numbers from `1` to `n` are prime.
    
2. Place those prime numbers in **prime positions** (2, 3, 5...).
    
3. The number of arrangements is:  
    `primeCount! × (n - primeCount)!`
    
4. Return the result modulo `10⁹ + 7`.
    

---

### ✅ **Helper: Count Primes using Sieve**

```js
function countPrimes(n) {
  let count = 0;
  for (let i = 2; i <= n; i++) {
    if (isPrime(i)) count++;
  }
  return count;
}

function isPrime(num) {
  if (num < 2) return false;
  for (let i = 2; i * i <= num; i++) {
    if (num % i === 0) return false;
  }
  return true;
}
```

---

### ✅ **Final Function with Modular Factorial**

```js
const MOD = 1e9 + 7;

function numPrimeArrangements(n) {
  const primeCount = countPrimes(n);
  return (factorial(primeCount) * factorial(n - primeCount)) % MOD;
}

function factorial(k) {
  let res = 1;
  for (let i = 2; i <= k; i++) {
    res = (res * i) % MOD;
  }
  return res;
}
```

---

### 🧠 What You Say in an Interview:

> “I counted how many numbers from 1 to `n` are prime, then placed them only at prime indices.  
> Since each group is independently permutable, I used `primeCount! × (n - primeCount)!`.  
> I handled large results using modulo arithmetic.”

---

### ⏱️ Time & Space Complexity

|Step|Time|
|---|---|
|Prime count|O(n√n)|
|Factorial|O(n)|
|Space|O(1)|

---

That wraps up your **Math & Logical Patterns** set ✅

Would you like a full list of other similar problems in this category?