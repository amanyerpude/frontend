
```markdown
# ⚙️ ES6+ Features

1. 🌟List some key features of ES6.  
2. 🌟What is the spread operator in JavaScript?  
3. 🌟What is the rest operator in JavaScript?  
4. What are template literals in JavaScript?  
5. 🌟What is a generator function in JavaScript?  
6. What is a polyfill in JavaScript?  
7. What is tree shaking in JavaScript?  
8. 🌟What is the difference between `defer` and `async`?
9. 🌟How can you abruptly stop a generator function?
```

--------------------------------------------------------------------------
# **1️⃣ List some key features of ES6**

---

## ✅ **How to Answer in an Interview**

- Start by saying **ES6 (ECMAScript 2015)** was a major update that introduced new syntax and features.
    
- Group features into **syntax improvements, new data structures, and new functionalities**.
    
- Give **practical examples** for 2–3 features instead of just listing.
    

---

## 💡 **Answer**

ES6 (ECMAScript 2015) brought major improvements to JavaScript, making code **more readable, modular, and powerful**.

### 🔹 **Key Features**

1. **`let` and `const`** – Block-scoped variable declarations.
    
2. **Arrow Functions** – Concise function syntax with lexical `this`.
    
3. **Template Literals** – String interpolation using backticks.
    
4. **Default Parameters** – Assign default values in functions.
    
5. **Destructuring** – Extract values from arrays/objects easily.
    
6. **Spread & Rest Operators** – Expand or collect values.
    
7. **Classes** – Object-oriented syntax over prototypes.
    
8. **Modules (`import`/`export`)** – Modular code structure.
    
9. **Promises** – Simplified asynchronous handling.
    
10. **New Data Structures** – `Map`, `Set`, `WeakMap`, `WeakSet`.
    

---

## 🧩 **Example**

```js
const PI = 3.14;      // const
let count = 5;        // let

const add = (a, b) => a + b; // Arrow function

console.log(`The sum is ${add(2, 3)}`); // Template literal
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What are some ES7+ features?**

#### ✅ **How to Answer in an Interview**

- Briefly mention that **JavaScript evolves yearly**, and list **1–2 key features per version**.
    
- Show awareness of commonly used features beyond ES6.
    

#### 💡 **Answer**

ES7 introduced:

1. **Exponentiation Operator (`**`)**
    
2. **`Array.prototype.includes()`**
    

Later versions added features like:

- **Async/Await (ES8)** – Easier async code.
    
- **Optional Chaining (`?.`)** and **Nullish Coalescing (`??`)** (ES11).
    

#### 🧩 **Example**

```js
console.log(2 ** 3); // 8
console.log([1, 2, 3].includes(2)); // true
```

---

### **2️⃣ Are `let` and `const` hoisted?**

#### ✅ **How to Answer in an Interview**

- Acknowledge that **all variables are hoisted**, but **`let` and `const` remain in TDZ (Temporal Dead Zone)**.
    
- Explain what TDZ means briefly.
    

#### 💡 **Answer**

- Yes, `let` and `const` are **hoisted but not initialised**.
    
- Accessing them **before declaration** results in a **ReferenceError** because they are in the TDZ.
    

#### 🧩 **Example**

```js
console.log(a); // ❌ ReferenceError
let a = 5;
```

---

## 🎯 **Interview Tips**

✅ Show that you know **ES6’s real-world impact** (cleaner, modular code).  
✅ Mention **let/const, arrow functions, promises, destructuring, modules** first.  
✅ If asked **ES5 vs ES6**, focus on **scope, async handling, and modules**.

# **2️⃣ What is the spread operator in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Begin by saying **the spread operator (`...`) expands iterable elements**.
    
- Mention it works with **arrays, objects, and function arguments**.
    
- Give **real-world examples** (array copy, merging objects, passing arguments).
    

---

## 💡 **Answer**

The **spread operator (`...`)** allows you to **expand elements of an array, object, or iterable** in places where multiple values are expected.

It is commonly used for:

1. **Copying arrays/objects**
    
2. **Merging arrays/objects**
    
3. **Passing multiple arguments to a function**
    

---

## 🧩 **Example**

```js
// Array copy & merge
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = [...arr1, ...arr2]; // [1, 2, 3, 4]

// Object copy
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const newObj = { ...obj1, ...obj2 }; // { a: 1, b: 2 }

// Function arguments
function sum(x, y, z) {
  return x + y + z;
}
console.log(sum(...[1, 2, 3])); // 6
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How is the spread operator different from the rest operator?**

#### ✅ **How to Answer in an Interview**

- Emphasise that **both use `...` but have opposite purposes**.
    
- Spread = **expands elements**.
    
- Rest = **collects elements into an array**.
    

#### 💡 **Answer**

- **Spread Operator (`...`)** → Expands iterable values.
    
- **Rest Operator (`...`)** → Collects remaining arguments into an array.
    

#### 🧩 **Example**

```js
const arr = [1, 2, 3];
console.log(...arr); // 1 2 3 (spread)

function show(...args) { 
  console.log(args); 
}
show(1, 2, 3); // [1, 2, 3] (rest)
```

---

### **2️⃣ Can the spread operator be used on objects?**

#### ✅ **How to Answer in an Interview**

- Say **yes, since ES2018**, it can be used to **shallow copy or merge objects**.
    

#### 💡 **Answer**

Yes, since **ES2018**, the spread operator works on objects as well.

#### 🧩 **Example**

```js
const obj1 = { x: 1 };
const obj2 = { y: 2 };
const merged = { ...obj1, ...obj2 }; 
// { x: 1, y: 2 }
```

---

## 🎯 **Interview Tips**

✅ Always mention **arrays, objects, and function arguments** use cases.  
✅ Don’t confuse **spread** with **rest** – interviewers love this trap.  
✅ If asked about deep copy, clarify **spread only does shallow copy**.

# **3️⃣ What is the rest operator in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **the rest operator (`...`) collects multiple elements into a single array/object**.
    
- Mention that it is used in **function parameters and destructuring**.
    
- Highlight that **spread and rest look the same but do the opposite**.
    

---

## 💡 **Answer**

The **rest operator (`...`)** is used to **collect multiple elements into a single variable**.

It is commonly used for:

1. **Handling variable number of function arguments**
    
2. **Collecting remaining properties in object/array destructuring**
    

---

## 🧩 **Example**

```js
// Function parameters
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4)); // 10

// Array destructuring
const [first, ...rest] = [10, 20, 30, 40];
console.log(rest); // [20, 30, 40]

// Object destructuring
const obj = { a: 1, b: 2, c: 3 };
const { a, ...others } = obj;
console.log(others); // { b: 2, c: 3 }
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How is the rest operator different from the spread operator?**

#### ✅ **How to Answer in an Interview**

- Point out that **spread expands** and **rest collects**.
    
- Both use `...` but serve **opposite purposes**.
    

#### 💡 **Answer**

- **Spread (`...`)** → Expands elements of an iterable.
    
- **Rest (`...`)** → Collects multiple values into a single array/object.
    

#### 🧩 **Example**

```js
const arr = [1, 2, 3];

// Spread
console.log(...arr); // 1 2 3

// Rest
function logAll(...values) {
  console.log(values);
}
logAll(1, 2, 3); // [1, 2, 3]
```

---

### **2️⃣ Can the rest operator be used multiple times in function parameters?**

#### ✅ **How to Answer in an Interview**

- Clarify that **only one rest parameter is allowed**, and it must be **the last parameter**.
    

#### 💡 **Answer**

No, you can only have **one rest parameter**, and it must **appear at the end** of the parameter list.

#### 🧩 **Example**

```js
// ✅ Valid
function example(a, ...rest) {}

// ❌ Invalid
function example(...rest, a) {} // Syntax Error
```

---

## 🎯 **Interview Tips**

✅ Always mention **function parameters + destructuring** use cases.  
✅ Interviewers often **ask the difference from spread**, so be ready.  
✅ Clarify that **rest works only at the end of the parameter list**.

# **4️⃣ What are template literals in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **template literals use backticks (`) instead of quotes**.
    
- Mention **string interpolation, multi-line strings, and embedded expressions**.
    
- Give **examples comparing normal strings vs template literals**.
    

---

## 💡 **Answer**

**Template literals** are strings defined using backticks (`) instead of quotes.

They allow:

1. **String interpolation** – Embed variables and expressions using `${}`.
    
2. **Multi-line strings** – Write strings across multiple lines easily.
    
3. **Expression evaluation** – Embed expressions directly inside strings.
    

---

## 🧩 **Example**

```js
// String interpolation
const name = "Alice";
console.log(`Hello, ${name}!`); // Hello, Alice!

// Multi-line string
const msg = `This is
a multi-line
string.`;
console.log(msg);

// Expression evaluation
console.log(`2 + 3 = ${2 + 3}`); // 2 + 3 = 5
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How are template literals better than string concatenation?**

#### ✅ **How to Answer in an Interview**

- Explain that template literals are **cleaner, easier to read**, and **support multi-line strings** without `\n`.
    

#### 💡 **Answer**

Template literals:  
✅ Remove the need for `+` when joining strings.  
✅ Allow multi-line strings naturally.  
✅ Support embedded expressions inside `${}`.

#### 🧩 **Example**

```js
// Old way
let msg1 = "Hello " + name + "!";

// Template literal
let msg2 = `Hello ${name}!`;
```

---

### **2️⃣ Can we use functions inside template literals?**

#### ✅ **How to Answer in an Interview**

- Yes, any **valid expression** can be placed inside `${}`.
    
- Functions can be **called directly**.
    

#### 💡 **Answer**

Yes, template literals can **call functions inside `${}`**.

#### 🧩 **Example**

```js
function greet(name) {
  return `Hello, ${name}`;
}
console.log(`${greet("Bob")}!`); // Hello, Bob!
```

---

## 🎯 **Interview Tips**

✅ Always **mention backticks** and show an example of **multi-line strings**.  
✅ Comparing with string concatenation shows **deeper understanding**.  
✅ Interviewers may ask about **tagged templates** (advanced use case).

# **5️⃣ What is a generator function in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **a generator function is a special function that can be paused and resumed**.
    
- Mention that it uses **`function*` syntax** and **`yield` keyword**.
    
- Explain that generators **return an iterator object** that follows the **iterator protocol**.
    

---

## 💡 **Answer**

A **generator function** is a special function in JavaScript that can **pause execution using `yield`** and **resume later**.

It is defined using the `function*` syntax and returns a **generator object**, which is an **iterator**.

---

## 🧩 **Example**

```js
function* numberGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = numberGenerator();

console.log(gen.next()); // { value: 1, done: false }
console.log(gen.next()); // { value: 2, done: false }
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true }
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How is a generator function different from a normal function?**

#### ✅ **How to Answer in an Interview**

- Explain that **normal functions run to completion**, whereas **generators can pause and resume**.
    
- Mention **`yield` and `function*` syntax** as key differences.
    

#### 💡 **Answer**

- **Normal Function** → Runs completely once called.
    
- **Generator Function** → Can pause using `yield` and resume using `next()`.
    

#### 🧩 **Example**

```js
function normal() { return 1; }

function* gen() {
  yield 1;
  yield 2;
}

const g = gen();
console.log(g.next()); // { value: 1, done: false }
```

---

### **2️⃣ What are practical use cases of generators?**

#### ✅ **How to Answer in an Interview**

- Mention **iterating over large data**, **lazy evaluation**, or **asynchronous workflows** (with `yield` and `next()`).
    

#### 💡 **Answer**

Generators are useful for:

1. **Lazy evaluation** – Generate values on demand.
    
2. **Custom iterators** – Create sequences without storing them fully.
    
3. **Async flows (before async/await)** – Used with libraries like Redux-Saga.
    

#### 🧩 **Example**

```js
function* infiniteCounter() {
  let i = 0;
  while (true) yield i++;
}

const counter = infiniteCounter();
console.log(counter.next().value); // 0
console.log(counter.next().value); // 1
```

---

## 🎯 **Interview Tips**

✅ Always mention **`function*` and `yield`**.  
✅ Highlight **pause/resume behaviour** as the key difference.  
✅ Use **simple examples** to show `next()` output.

# **6️⃣ What is a polyfill in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **a polyfill is a piece of code that provides modern functionality on older browsers that do not support it natively**.
    
- Mention that polyfills **mimic newer JavaScript features** like `Promise`, `fetch`, etc.
    
- Give a **short example** of a custom polyfill.
    

---

## 💡 **Answer**

A **polyfill** is a piece of code (usually JavaScript) that **implements a modern feature on browsers that do not support it**.

It helps maintain **cross-browser compatibility** by adding missing features.

---

## 🧩 **Example**

### Polyfill for `Array.prototype.includes`:

```js
if (!Array.prototype.includes) {
  Array.prototype.includes = function (value) {
    return this.indexOf(value) !== -1;
  };
}

console.log([1, 2, 3].includes(2)); // true
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How is a polyfill different from a transpiler like Babel?**

#### ✅ **How to Answer in an Interview**

- Explain that **Babel transpiles code into older syntax**, whereas **polyfills add missing functionality at runtime**.
    

#### 💡 **Answer**

- **Polyfill** → Adds missing methods/features (runtime support).
    
- **Transpiler (Babel)** → Converts new JS syntax into older JS syntax (compile-time support).
    

#### 🧩 **Example**

```js
// Babel converts this:
const add = (a, b) => a + b;

// Into:
var add = function(a, b) { return a + b; };
```

---

### **2️⃣ How do you include polyfills in a project?**

#### ✅ **How to Answer in an Interview**

- Mention **manual inclusion (custom polyfills)** or **using libraries like `core-js`**.
    
- In modern projects, polyfills are **auto-injected by Babel with correct configuration**.
    

#### 💡 **Answer**

Polyfills can be added:

1. Manually – Write your own function.
    
2. Using libraries – `core-js`, `polyfill.io`.
    
3. Via Babel – With `@babel/preset-env` and `useBuiltIns`.
    

---

## 🎯 **Interview Tips**

✅ Always clarify **polyfill ≠ transpiler**.  
✅ Show **real-world examples** like `Promise`, `fetch`, `Array.includes`.  
✅ Interviewers often ask **"write a polyfill for X"**, so be ready with a simple one.

# **7️⃣ What is tree shaking in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **tree shaking is a process of removing unused code during the build process**.
    
- Mention that it is used mainly with **ES6 module imports/exports**.
    
- Highlight that it **reduces bundle size and improves performance**.
    

---

## 💡 **Answer**

**Tree shaking** is an optimisation technique that **removes unused or "dead" code from the final JavaScript bundle**.

It works by **statically analysing ES6 `import`/`export` statements** and removing any code that is never used.

---

## 🧩 **Example**

```js
// utils.js
export function add(a, b) { return a + b; }
export function subtract(a, b) { return a - b; }

// main.js
import { add } from "./utils.js"; // Only 'add' is used

console.log(add(2, 3));
```

✅ A bundler like **Webpack/Rollup** will **remove `subtract()`** from the final bundle because it's unused.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How does tree shaking work internally?**

#### ✅ **How to Answer in an Interview**

- Explain that **tree shaking relies on static analysis of ES6 imports/exports**.
    
- Dynamic `require()` calls prevent tree shaking.
    

#### 💡 **Answer**

- Bundlers like Webpack/Rollup **analyse ES6 module exports at build time**.
    
- Any unused exports are **excluded from the final bundle**.
    
- It works only with **static imports**, not `require()`.
    

---

### **2️⃣ What are some tools that support tree shaking?**

#### ✅ **How to Answer in an Interview**

- Mention **Webpack, Rollup, Parcel, and ESBuild**.
    
- Explain that **Webpack requires `mode: production` to enable tree shaking**.
    

#### 💡 **Answer**

Tools that support tree shaking:  
✅ **Webpack** – Most popular (requires ES6 modules & production mode).  
✅ **Rollup** – Designed for ES modules, great for libraries.  
✅ **Parcel, ESBuild** – Support tree shaking out of the box.

---

## 🎯 **Interview Tips**

✅ Always mention **bundle size reduction as the main benefit**.  
✅ Say it **works best with ES modules, not CommonJS (`require`)**.  
✅ Interviewers may ask **why tree shaking may fail** → because of **dynamic imports or side effects**.

# **8️⃣ 🌟What is the difference between `defer` and `async`?**

---

## ✅ **How to Answer in an Interview**

- Start by saying both **`defer` and `async` are attributes for loading external scripts without blocking HTML parsing**.
    
- Then **compare their execution timing clearly**.
    
- Use a **table or bullet points** for clarity.
    

---

## 💡 **Answer**

Both **`defer`** and **`async`** allow non-blocking script loading, but they differ in execution timing:

|Attribute|Loading|Execution|
|---|---|---|
|**async**|Script loads in parallel with HTML parsing|Executes **immediately after loading** (may run before DOM is ready)|
|**defer**|Script loads in parallel with HTML parsing|Executes **after HTML parsing is complete**, in order|

---

## 🧩 **Example**

```html
<!-- async: Loads in parallel, executes as soon as it's ready -->
<script src="script.js" async></script>

<!-- defer: Loads in parallel, executes after HTML parsing -->
<script src="script.js" defer></script>
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use `async` vs `defer`?**

#### ✅ **How to Answer in an Interview**

- Explain **async is good for independent scripts** (e.g., analytics).
    
- **Defer is better for scripts that rely on DOM**.
    

#### 💡 **Answer**

- **Use `async`** → For scripts that **don’t depend on DOM** or other scripts (ads, analytics).
    
- **Use `defer`** → For scripts that **manipulate DOM** or need **to execute in order**.
    

---

### **2️⃣ What happens if both `async` and `defer` are used together?**

#### ✅ **How to Answer in an Interview**

- Mention that **`async` takes priority over `defer`**.
    

#### 💡 **Answer**

If both attributes are used together, **`async` wins** and the script will **behave like `async`**, executing as soon as it’s downloaded.

---

## 🎯 **Interview Tips**

✅ Always compare **loading vs execution timing** clearly.  
✅ Use **real-world scenarios** – analytics scripts → `async`, DOM scripts → `defer`.  
✅ Mention that **defer preserves execution order**, but async does not.

--------------------------------------------------------------------------
## 1. List some key features of ES6

**Explanation:**  
ES6 (ECMAScript 2015) introduced several major improvements and features to JavaScript, making the language more powerful and expressive:

- **let and const:** New ways to declare variables with block scope.
    
- **Arrow functions:** Shorter function syntax and lexical `this` binding.
    
- **Classes:** Class syntax for easier OOP-style code.
    
- **Template literals:** String interpolation and multi-line strings.
    
- **Destructuring:** Unpack values from arrays or objects into variables.
    
- **Default parameters:** Functions can have default values for parameters.
    
- **Spread and rest operators:** For expanding or collecting values.
    
- **Promises:** Native support for asynchronous programming.
    
- **Modules:** `import` and `export` statements for modular JS code.
    
- **Enhanced object literals:** Concise method and property declarations.
    
- **Iterators and generators:** For custom iteration logic.
    

**What to say in an interview:**  
"Some key features in ES6 include `let` and `const` for variable declarations, arrow functions, classes, template literals for string interpolation, destructuring, spread and rest operators, built-in Promises, and import/export modules. These features streamline code and improve readability."

## 2. What is the spread operator in JavaScript?

**Explanation:**  
The spread operator (`...`) allows an iterable (like an array or object) to be expanded into individual elements.

**Common uses:**

- Copy or merge arrays and objects.
    
- Expand items in function calls.
    

**Examples:**

javascript

`let arr1 = [1, 2]; let arr2 = [3, 4]; let combined = [...arr1, ...arr2]; // [1, 2, 3, 4] let person = { name: "Amy" }; let fullPerson = { ...person, age: 25 }; // { name: "Amy", age: 25 }`

**What to say in an interview:**  
"The spread operator lets me quickly copy or merge arrays and objects, or pass array elements as separate arguments to a function."

## 3. What is the rest operator in JavaScript?

**Explanation:**  
The rest operator (`...`) collects multiple elements into a single array or object, usually for function parameters or destructuring.

**Examples:**

javascript

`function sum(...numbers) {   return numbers.reduce((a, b) => a + b, 0); } let result = sum(1, 2, 3); // 6 let [first, ...others] = [10, 20, 30, 40]; // first: 10, others: [20, 30, 40]`

**What to say in an interview:**  
"The rest operator allows me to gather a variable number of arguments into an array—useful in function parameters and for destructuring arrays or objects."

## 4. What are template literals in JavaScript?

**Explanation:**  
Template literals are strings enclosed by backticks (` `) that support embedded expressions (using `${}`) and multi-line strings.

**Examples:**

javascript

``let name = "Ravi"; let message = `Hello, ${name}!`; // "Hello, Ravi!" let multiline = `This is a multi-line string!`;``

**What to say in an interview:**  
"Template literals let me create strings with embedded variables and write multi-line strings easily. I use backticks and interpolate values using `${}`."

## 5. What is a generator function in JavaScript?

**Explanation:**  
A generator function is declared with `function*` and can pause (`yield`) and resume its execution, returning multiple values one at a time.

**Example:**

javascript

`function* countUp() {   yield 1;  yield 2;  yield 3; } const counter = countUp(); console.log(counter.next().value); // 1 console.log(counter.next().value); // 2`

**What to say in an interview:**  
"A generator function lets me pause and resume the function’s execution using `yield`, which is useful for custom iteration, lazy evaluation, or asynchronous flows."

## 6. What is a polyfill in JavaScript?

**Explanation:**  
A polyfill is code (often a library or snippet) that adds a feature to JavaScript which a developer expects from newer standards, but is missing in older environments (like older browsers).

**Example:**

> If a browser doesn’t support `Array.prototype.includes()`, you can write a polyfill to add this function.

**What to say in an interview:**  
"A polyfill is code that allows me to use newer JavaScript features in environments that don’t support them natively, helping maintain compatibility with older browsers."

## 7. What is tree shaking in JavaScript?

**Explanation:**  
Tree shaking is the process of removing unused code from the final JavaScript bundle during build/compile time. It is especially useful with ES6 modules, where unused imports can be detected and dropped automatically by bundlers like Webpack or Rollup.

**What to say in an interview:**  
"Tree shaking is an optimization step in modern JS build tools that eliminates unused code from the bundle, making final files smaller and faster for users."


