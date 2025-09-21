
```markdown
# 🧰 Functions & Scoping

1. 🌟What is a closure in JavaScript?  
2. Explain the concept of closures in JavaScript with a 🌟real-world example.  
3. What are callbacks in JavaScript?  
4. 🌟What are higher-order functions in JavaScript?  
5. What is the difference between pure and impure functions?  
6. What is IIFE (Immediately Invoked Function Expression)?  
7. What are the limitations of arrow functions?  
8. 🌟What is the difference between `call()`, `apply()`, and `bind()`?  
9. What is `bind()`, `call()`, and `apply()` in JavaScript, and when do you use them?
10. 🌟What is an anonymous function in JavaScript?
```

--------------------------------------------------------------------------
# **1️⃣ What is a closure in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Begin by defining a closure in simple terms.
    
- Explain that a closure is **a function that remembers its lexical scope even when executed outside that scope**.
    
- Mention practical use cases (data privacy, currying, memoization).
    

---

## 💡 **Answer**

A **closure** is created when a function **remembers and accesses variables from its lexical scope**, even after the outer function has finished executing.

Closures enable **data privacy, stateful functions, and function factories** in JavaScript.

---

## 🧩 **Example**

```js
function outer() {
  let count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer();
counter(); // 1
counter(); // 2
```

Even though `outer()` has finished executing, the `inner()` function still has access to `count` via closure.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why are closures useful?**

#### ✅ **How to Answer in an Interview**

- Mention key use cases.
    

#### 💡 **Answer**

Closures are useful for:

- **Data encapsulation** (private variables)
    
- **Function factories**
    
- **Event handlers with state**
    
- **Memoization and caching**
    

---

### **2️⃣ Do closures affect memory usage?**

#### ✅ **How to Answer in an Interview**

- Explain garbage collection behaviour.
    

#### 💡 **Answer**

Yes, closures keep references to variables even after the outer function ends, which may increase memory usage if not managed properly.

---

### **3️⃣ Can closures be used in loops?**

#### ✅ **How to Answer in an Interview**

- Explain `let` vs `var` issue.
    

#### 💡 **Answer**

Yes, but with `var` inside a loop, closures may capture the same variable. Using `let` creates a new binding per iteration.

---

### **4️⃣ Are arrow functions different in closures?**

#### ✅ **How to Answer in an Interview**

- Explain lexical `this`.
    

#### 💡 **Answer**

Arrow functions **inherit `this` from their surrounding scope**, but they still form closures like normal functions.

---

## 🎯 **Interview Tips**

✅ Always **define closures in simple words**.  
✅ Provide **one practical example** (counter or private variable).  
✅ Mention **memory considerations for closures**.

# **2️⃣ Explain the concept of closures in JavaScript with a real-world example.**

---

## ✅ **How to Answer in an Interview**

- Start with a **short closure definition**.
    
- Then provide a **real-world analogy or practical example** (e.g., private variables, event handlers, function factories).
    
- Show how closures help maintain **state** across function calls.
    

---

## 💡 **Answer**

A **closure** is a function that **remembers the variables from its lexical scope**, even after the outer function has finished executing.

---

### **Real-World Example – Private Variables**

```js
function createBankAccount(initialBalance) {
  let balance = initialBalance;

  return {
    deposit(amount) {
      balance += amount;
      console.log(`Deposited: $${amount}. Balance: $${balance}`);
    },
    withdraw(amount) {
      if (amount <= balance) {
        balance -= amount;
        console.log(`Withdrew: $${amount}. Balance: $${balance}`);
      } else {
        console.log("Insufficient funds!");
      }
    },
    getBalance() {
      return balance;
    }
  };
}

const account = createBankAccount(100);
account.deposit(50);  // Deposited: $50. Balance: $150
account.withdraw(30); // Withdrew: $30. Balance: $120
console.log(account.getBalance()); // 120
```

Here, the variable **`balance`** is **private** and only accessible via closure functions.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is this example a closure?**

#### ✅ **How to Answer in an Interview**

- Relate back to the concept.
    

#### 💡 **Answer**

Because the inner functions (`deposit`, `withdraw`, `getBalance`) **remember and access `balance`** from the outer function even after `createBankAccount()` has returned.

---

### **2️⃣ How does this pattern achieve data encapsulation?**

#### ✅ **How to Answer in an Interview**

- Explain privacy.
    

#### 💡 **Answer**

Since `balance` is not directly accessible outside, it **cannot be modified directly**, making it effectively **private**.

---

### **3️⃣ Where are closures used in real-world apps?**

#### ✅ **How to Answer in an Interview**

- Mention real use cases.
    

#### 💡 **Answer**

- Event listeners with state
    
- Currying functions
    
- Private variables in modules
    
- Memoization and caching
    

---

### **4️⃣ Can this be done with classes instead?**

#### ✅ **How to Answer in an Interview**

- Compare both approaches.
    

#### 💡 **Answer**

Yes, classes can also encapsulate state using private fields, but closures are a **functional programming alternative**.

---

## 🎯 **Interview Tips**

✅ Always give a **real-world example (like private variables)**.  
✅ Explain **how closures make variables private**.  
✅ Relate back to **state management in frontend apps**.

# **3️⃣ What are callbacks in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by defining a **callback function** as a function passed into another function to be executed later.
    
- Mention that callbacks are common in **asynchronous operations**.
    
- Provide both **synchronous and asynchronous examples**.
    

---

## 💡 **Answer**

A **callback** is a function that is **passed as an argument to another function**, and is executed **after the main function has finished its task**.

Callbacks are widely used for **event handling, asynchronous operations, and higher-order functions**.

---

## 🧩 **Example – Synchronous Callback**

```js
function greet(name, callback) {
  console.log(`Hello, ${name}`);
  callback();
}

greet("Alice", () => console.log("Welcome!"));
// Hello, Alice
// Welcome!
```

---

## 🧩 **Example – Asynchronous Callback**

```js
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What are the problems with callbacks?**

#### ✅ **How to Answer in an Interview**

- Mention callback hell.
    

#### 💡 **Answer**

- Difficult to manage when there are **nested callbacks** (Callback Hell).
    
- Harder to read and debug.
    
- Error handling can get messy.
    

---

### **2️⃣ How did Promises improve callbacks?**

#### ✅ **How to Answer in an Interview**

- Explain benefits of Promises.
    

#### 💡 **Answer**

Promises avoid **deeply nested callbacks** and provide better **error handling** and **chaining** with `.then()` and `.catch()`.

---

### **3️⃣ Are all callbacks asynchronous?**

#### ✅ **How to Answer in an Interview**

- Clarify misconception.
    

#### 💡 **Answer**

No. Callbacks can be **synchronous** (executed immediately) or **asynchronous** (executed later).

---

### **4️⃣ Can arrow functions be used as callbacks?**

#### ✅ **How to Answer in an Interview**

- Show syntax.
    

#### 💡 **Answer**

Yes, arrow functions are commonly used for concise callback definitions:

```js
[1, 2, 3].forEach(num => console.log(num * 2));
```

---

## 🎯 **Interview Tips**

✅ Always give **both sync and async examples**.  
✅ Mention **callback hell problem**.  
✅ Relate to **real-world use cases like event handling or API calls**.

# **4️⃣ What are higher-order functions in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by defining higher-order functions (HOFs) in **simple terms**.
    
- Explain that HOFs **either take a function as an argument, return a function, or both**.
    
- Provide **common examples** (`map`, `filter`, `forEach`).
    

---

## 💡 **Answer**

A **higher-order function (HOF)** is a function that **takes another function as an argument, returns a function, or both**.

HOFs enable **functional programming patterns** like callbacks, currying, and function composition.

---

## 🧩 **Example – Takes a Function as Argument**

```js
function greet(name) {
  return `Hello, ${name}`;
}

function processUser(name, callback) {
  console.log(callback(name));
}

processUser("Alice", greet);
// Hello, Alice
```

---

## 🧩 **Example – Returns a Function**

```js
function multiplier(factor) {
  return function (num) {
    return num * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What are some built-in HOFs in JavaScript?**

#### ✅ **How to Answer in an Interview**

- List commonly used examples.
    

#### 💡 **Answer**

- `map()`, `filter()`, `reduce()`, `forEach()`, `sort()`, `some()`, `every()` – all are HOFs because they take a **callback function**.
    

---

### **2️⃣ How do HOFs enable functional programming?**

#### ✅ **How to Answer in an Interview**

- Explain benefits.
    

#### 💡 **Answer**

They allow functions to be **passed around like values**, making code more **modular, reusable, and declarative**.

---

### **3️⃣ Are arrow functions always higher-order functions?**

#### ✅ **How to Answer in an Interview**

- Clarify misconception.
    

#### 💡 **Answer**

No. Arrow functions can be **regular functions**. They become HOFs **only when they take or return a function**.

---

### **4️⃣ Can you give a real-world use case?**

#### ✅ **How to Answer in an Interview**

- Show practical relevance.
    

#### 💡 **Answer**

Event listeners are implemented using HOFs:

```js
button.addEventListener("click", () => alert("Clicked!"));
```

Here, `addEventListener` is a higher-order function.

---

## 🎯 **Interview Tips**

✅ Always **define HOF clearly**.  
✅ Provide **examples of both cases (takes/returns a function)**.  
✅ Relate to **real-world usage like event listeners and array methods**.

# **5️⃣ What is the difference between pure and impure functions?**

---

## ✅ **How to Answer in an Interview**

- Start by defining a **pure function** (no side effects, same input → same output).
    
- Define **impure function** (may have side effects or return different output for same input).
    
- Provide **clear examples of both**.
    

---

## 💡 **Answer**

|Feature|Pure Function ✅|Impure Function ❌|
|---|---|---|
|Output|Same input → always same output|Output may vary for same input|
|Side Effects|No side effects|Has side effects (e.g., modifying external variables, API calls)|
|Predictability|Easy to test and debug|Harder to predict behaviour|

---

## 🧩 **Example – Pure Function**

```js
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5 (always same output)
```

---

## 🧩 **Example – Impure Function**

```js
let counter = 0;
function increment() {
  counter++;
  return counter;
}

console.log(increment()); // 1
console.log(increment()); // 2 (output changes due to external state)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why are pure functions preferred?**

#### ✅ **How to Answer in an Interview**

- Explain benefits.
    

#### 💡 **Answer**

Pure functions are:  
✅ Predictable and easy to test.  
✅ Enable functional programming.  
✅ Avoid unintended side effects.

---

### **2️⃣ Are all functions with return values pure?**

#### ✅ **How to Answer in an Interview**

- Clarify misconception.
    

#### 💡 **Answer**

No. A function can return a value but still be impure if it **modifies external state or depends on external variables**.

---

### **3️⃣ Give a real-world example of an impure function.**

#### ✅ **How to Answer in an Interview**

- Mention API calls, DOM manipulation.
    

#### 💡 **Answer**

```js
function updateDOM() {
  document.body.style.background = "blue"; // Side effect
}
```

This function is impure because it **changes external state (DOM)**.

---

### **4️⃣ How do pure functions help in React?**

#### ✅ **How to Answer in an Interview**

- Connect to frontend usage.
    

#### 💡 **Answer**

React components **should ideally be pure functions** of their props, making UI predictable and easier to debug.

---

## 🎯 **Interview Tips**

✅ Always **define in simple terms first**.  
✅ Show **examples for both pure and impure**.  
✅ Relate to **React functional components for extra points**.

# **6️⃣ What is IIFE (Immediately Invoked Function Expression)?**

---

## ✅ **How to Answer in an Interview**

- Start by defining IIFE as a **function that runs immediately after it is defined**.
    
- Explain that it is used for **creating a private scope and avoiding polluting the global namespace**.
    
- Provide both **syntax and practical use case**.
    

---

## 💡 **Answer**

An **IIFE (Immediately Invoked Function Expression)** is a function that is **executed immediately after its creation**.

It is written as a **function expression wrapped in parentheses**, followed by `()` to execute it.

---

## 🧩 **Example**

```js
(function () {
  console.log("IIFE executed!");
})(); 
// Output: IIFE executed!
```

---

### **Real-World Use Case – Creating Private Scope**

```js
const counter = (function () {
  let count = 0;
  return {
    increment: () => ++count,
    decrement: () => --count,
    getCount: () => count
  };
})();

console.log(counter.increment()); // 1
console.log(counter.getCount()); // 1
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is IIFE useful?**

#### ✅ **How to Answer in an Interview**

- Mention avoiding global pollution.
    

#### 💡 **Answer**

IIFE creates a **private scope** for variables, preventing them from leaking into the global scope.

---

### **2️⃣ Can you write an arrow function IIFE?**

#### ✅ **How to Answer in an Interview**

- Show modern syntax.
    

#### 💡 **Answer**

Yes:

```js
(() => {
  console.log("Arrow IIFE executed!");
})();
```

---

### **3️⃣ Are IIFEs still used in modern JavaScript?**

#### ✅ **How to Answer in an Interview**

- Explain ES6 alternatives.
    

#### 💡 **Answer**

Less frequently, since ES6 modules and `let`/`const` provide block scope. But IIFEs are still useful for **isolated scripts**.

---

### **4️⃣ What happens if you remove the parentheses?**

#### ✅ **How to Answer in an Interview**

- Explain difference between declaration and expression.
    

#### 💡 **Answer**

Without parentheses, it becomes a **function declaration**, which cannot be executed immediately.

---

## 🎯 **Interview Tips**

✅ Define IIFE in **one simple line first**.  
✅ Provide **both syntax and a real-world example**.  
✅ Mention that **IIFE is less common now due to ES6 modules**.

# **7️⃣ What are the limitations of arrow functions?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **arrow functions have lexical `this`** and do **not behave like normal functions** in some cases.
    
- List key limitations with examples.
    
- Highlight situations where **regular functions are preferred**.
    

---

## 💡 **Answer**

Arrow functions are **concise** but have some **limitations**:

|Limitation|Explanation|
|---|---|
|**No own `this`**|Arrow functions inherit `this` from their lexical scope, so they **cannot be used as object methods or constructors**.|
|**No `arguments` object**|Arrow functions do not have their own `arguments` object.|
|**Cannot be used as constructors**|Using `new` with arrow functions throws an error.|
|**No `super` or `new.target`**|They cannot access these keywords.|

---

## 🧩 **Examples**

```js
// 1️⃣ No own `this`
const obj = {
  name: "Alice",
  greet: () => console.log(this.name)
};
obj.greet(); // undefined (inherits global `this`)

// 2️⃣ No `arguments` object
const showArgs = () => console.log(arguments); 
showArgs(1, 2); // ReferenceError: arguments is not defined

// 3️⃣ Cannot be used as constructors
const Person = () => {};
const p = new Person(); // TypeError
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why do arrow functions not have their own `this`?**

#### ✅ **How to Answer in an Interview**

- Explain lexical binding.
    

#### 💡 **Answer**

Because arrow functions **use lexical `this`**, meaning they take `this` from where they are defined, not from how they are called.

---

### **2️⃣ When should you avoid arrow functions?**

#### ✅ **How to Answer in an Interview**

- Mention specific scenarios.
    

#### 💡 **Answer**

Avoid them when:  
✅ You need to use `this` as a method context.  
✅ You need `arguments` object.  
✅ You want to use the function as a constructor.

---

### **3️⃣ Are arrow functions always better for callbacks?**

#### ✅ **How to Answer in an Interview**

- Clarify when they’re useful.
    

#### 💡 **Answer**

Arrow functions are great for short callbacks, but **avoid them for event listeners where `this` refers to the element**.

---

### **4️⃣ Do arrow functions affect performance?**

#### ✅ **How to Answer in an Interview**

- Explain there’s no significant difference.
    

#### 💡 **Answer**

Performance difference is negligible, but **regular functions offer more flexibility** in special cases like constructors.

---

## 🎯 **Interview Tips**

✅ Always **list the key 3–4 limitations** clearly.  
✅ Provide **real examples for each limitation**.  
✅ Mention that **lexical `this` is both a feature and limitation**.

# **8️⃣ What is the difference between `call()`, `apply()`, and `bind()`?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that all three are used to **set the `this` value** of a function.
    
- Then explain **how arguments are passed** and **when each method is used**.
    
- Provide a **comparison table** with examples.
    

---

## 💡 **Answer**

|Method|When It Executes|How Arguments Are Passed|Return Value|
|---|---|---|---|
|`call()`|Executes immediately|Arguments passed **individually**|Return value of the function|
|`apply()`|Executes immediately|Arguments passed as an **array**|Return value of the function|
|`bind()`|Does **not execute immediately**|Arguments passed individually|Returns a **new function** with `this` bound|

---

## 🧩 **Example**

```js
function greet(greeting, punctuation) {
  console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "Alice" };

greet.call(person, "Hello", "!");       // Hello, Alice!
greet.apply(person, ["Hi", "!!"]);      // Hi, Alice!!
const boundGreet = greet.bind(person, "Hey");
boundGreet("?");                        // Hey, Alice?
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use `apply()` over `call()`?**

#### ✅ **How to Answer in an Interview**

- Mention array-based arguments.
    

#### 💡 **Answer**

Use `apply()` when arguments are already **in an array**:

```js
Math.max.apply(null, [1, 2, 3]); // 3
```

---

### **2️⃣ When is `bind()` most useful?**

#### ✅ **How to Answer in an Interview**

- Explain usage in event handlers.
    

#### 💡 **Answer**

`bind()` is useful when you want to **create a new function with fixed `this`**, often for callbacks or event handlers:

```js
const button = document.querySelector("button");
button.addEventListener("click", greet.bind(person, "Welcome"));
```

---

### **3️⃣ Does `bind()` execute immediately?**

#### ✅ **How to Answer in an Interview**

- Clarify difference.
    

#### 💡 **Answer**

No, `bind()` **returns a new function**, which you can call later.

---

### **4️⃣ Can you pass extra arguments after binding?**

#### ✅ **How to Answer in an Interview**

- Show example.
    

#### 💡 **Answer**

Yes. Extra arguments can be passed later:

```js
const bound = greet.bind(person, "Hi");
bound("!!!"); // Hi, Alice!!!
```

---

## 🎯 **Interview Tips**

✅ Always **include a comparison table** for clarity.  
✅ Provide **real examples for each method**.  
✅ Mention **use cases for event handlers and function borrowing**.

# **9️⃣ What is `bind()`, `call()`, and `apply()` in JavaScript, and when do you use them?**

---

## ✅ **How to Answer in an Interview**

- Start by mentioning that all three methods are used to **set the `this` context of a function**.
    
- Briefly define each method and provide **use cases**.
    
- Show a **side-by-side example**.
    

---

## 💡 **Answer**

### **📌 1. `call()`**

- Executes the function **immediately**.
    
- Passes arguments **individually**.
    

✅ **Use case:** Function borrowing or method reuse.

```js
function greet(msg) {
  console.log(`${msg}, ${this.name}`);
}

const person = { name: "Alice" };
greet.call(person, "Hello"); // Hello, Alice
```

---

### **📌 2. `apply()`**

- Similar to `call()`, but **arguments are passed as an array**.
    

✅ **Use case:** When you already have arguments in an array.

```js
greet.apply(person, ["Hi"]); // Hi, Alice
```

---

### **📌 3. `bind()`**

- Does **not execute immediately**, but returns a **new function** with `this` permanently set.
    

✅ **Use case:** Event handlers, delayed function calls, partial application.

```js
const boundGreet = greet.bind(person, "Hey");
boundGreet(); // Hey, Alice
```

---

## 🧩 **Comparison Table**

|Method|Executes Immediately?|How to Pass Arguments|Return Value|
|---|---|---|---|
|call()|✅ Yes|Individually|Function's return value|
|apply()|✅ Yes|As an array|Function's return value|
|bind()|❌ No|Individually|A **new function** with bound `this`|

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is `bind()` commonly used in event handlers?**

#### ✅ **How to Answer in an Interview**

- Explain event context issue.
    

#### 💡 **Answer**

Because in event handlers, `this` may refer to the DOM element. `bind()` ensures the callback uses the desired `this`.

---

### **2️⃣ How does `bind()` enable partial function application?**

#### ✅ **How to Answer in an Interview**

- Show pre-filling arguments.
    

#### 💡 **Answer**

```js
function multiply(a, b) {
  return a * b;
}

const double = multiply.bind(null, 2);
console.log(double(5)); // 10
```

---

### **3️⃣ Which is faster: `call()` or `apply()`?**

#### ✅ **How to Answer in an Interview**

- Explain performance difference.
    

#### 💡 **Answer**

Both are similar in modern engines, but `call()` can be slightly faster because it doesn’t need to process an array.

---

### **4️⃣ Can you pass extra arguments to `bind()` after binding?**

#### ✅ **How to Answer in an Interview**

- Show example.
    

#### 💡 **Answer**

Yes, additional arguments can still be passed when calling the bound function.

```js
const bound = greet.bind(person, "Hi");
bound("!!!"); // Hi, Alice!!!
```

---

## 🎯 **Interview Tips**

✅ Always **define each method + when to use it**.  
✅ Provide **side-by-side examples**.  
✅ Mention **common use cases like function borrowing and event binding**.

---