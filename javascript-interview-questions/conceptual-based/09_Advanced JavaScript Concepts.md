
```markdown
# 🧪 Advanced JavaScript Concepts

1. 🌟What is the prototype in JavaScript?  
2. What is the prototype chain and how does inheritance work?  
3. 🌟What are JavaScript modules, and how do you import/export them?  
4. What is `bind()`, `call()`, and `apply()` in JavaScript, and when do you use them?  
5. What is `eval()` and why is it considered risky?  
6. What is a cursor in JavaScript? _(Is this related to database cursors or DOM selections?)_  
7. What is JavaScript sandboxing?
8. What is the Reflect API in JavaScript?
9. What is Proxy in JavaScript?
```

--------------------------------------------------------------------------
# **1️⃣ What is the prototype in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **JavaScript is a prototype-based language**, meaning objects can inherit properties from other objects via prototypes.
    
- Explain **every object has an internal `[[Prototype]]` property** (accessed via `__proto__` or `Object.getPrototypeOf`).
    
- Show **a simple example with functions and objects**.
    

---

## 💡 **Answer**

The **prototype** in JavaScript is an object that **is shared by all instances created from a function (constructor)**.

- Every object in JavaScript has a **hidden `[[Prototype]]` link**.
    
- Functions have a `.prototype` property that is used **when creating new objects with `new`**.
    
- Prototypes are **used for inheritance** – methods and properties can be shared.
    

---

## 🧩 **Example**

```js
function Person(name) {
  this.name = name;
}

// Adding a method to prototype
Person.prototype.sayHi = function () {
  console.log(`Hi, I'm ${this.name}`);
};

const p1 = new Person("Alice");
p1.sayHi(); // Hi, I'm Alice
```

✔ The `sayHi` method is **not copied to each object** but accessed via the **prototype**.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between `__proto__` and `.prototype`?**

#### ✅ **How to Answer in an Interview**

- `.prototype` → Belongs to **functions/constructors**.
    
- `__proto__` → Belongs to **objects** and **points to their prototype**.
    

#### 💡 **Answer**

```js
function Person() {}
const p = new Person();

console.log(Person.prototype); // Prototype object used for new instances
console.log(p.__proto__);      // Points to Person.prototype
```

---

### **2️⃣ Can you change an object’s prototype after creation?**

#### ✅ **How to Answer in an Interview**

- Yes, using `Object.setPrototypeOf(obj, newProto)` or `Object.create(proto)`.
    

#### 💡 **Answer**

```js
const animal = { eats: true };
const dog = {};

Object.setPrototypeOf(dog, animal);

console.log(dog.eats); // true
```

---

## 🎯 **Interview Tips**

✅ Always clarify **JavaScript is prototype-based, not class-based (though ES6 adds class syntax)**.  
✅ Show **how prototype allows method sharing instead of duplication**.  
✅ Be ready for follow-ups on **prototype chain (next question)**.

# **2️⃣ What is the prototype chain and how does inheritance work?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **the prototype chain is the mechanism that JavaScript uses to look up properties and methods on objects**.
    
- Explain that **if a property is not found on an object, JS checks its prototype, then the prototype’s prototype, and so on until `Object.prototype`**.
    
- Mention **this is how inheritance works in JS**.
    

---

## 💡 **Answer**

The **prototype chain** is a series of linked objects.

- When you access a property on an object:  
    1️⃣ JS first checks the object itself.  
    2️⃣ If not found, it **looks at its prototype (`__proto__`)**.  
    3️⃣ Continues until it reaches `Object.prototype`.  
    4️⃣ If not found, returns `undefined`.
    

This **chain of lookups is how inheritance works** in JavaScript.

---

## 🧩 **Example**

```js
const animal = { eats: true };
const dog = Object.create(animal); // dog.__proto__ → animal
dog.barks = true;

console.log(dog.barks); // true (own property)
console.log(dog.eats);  // true (inherited from animal)
console.log(dog.toString); // inherited from Object.prototype
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What happens if you try to access a property that doesn't exist anywhere in the chain?**

#### ✅ **How to Answer in an Interview**

- JS returns `undefined` when it can’t find the property after checking all prototypes.
    

---

### **2️⃣ How do classes use the prototype chain internally?**

#### ✅ **How to Answer in an Interview**

- ES6 `class` is **syntactic sugar** over prototypes.
    
- Methods defined in a class are **added to the prototype**.
    

#### 💡 **Answer**

```js
class Animal {
  eat() {
    console.log("Eating");
  }
}
const dog = new Animal();
dog.eat(); // Looks up in Animal.prototype
```

---

## 🎯 **Interview Tips**

✅ Always mention **lookup flow → object → prototype → Object.prototype → null**.  
✅ Clarify that **ES6 classes still use prototypes under the hood**.  
✅ Be ready for **follow-ups on Object.create(), new keyword, and inheritance patterns**.

# **3️⃣ What are JavaScript modules, and how do you import/export them?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **modules allow splitting code into reusable, isolated files**.
    
- Mention that **ES6 introduced native module syntax using `import` and `export`**.
    
- Explain **default vs named exports** with examples.
    

---

## 💡 **Answer**

A **JavaScript module** is a **separate file that contains code (functions, variables, classes) that can be reused in other files**.

### 🔹 **Benefits of Modules**

✔ Code reusability  
✔ Better organization  
✔ Avoids global variable pollution

---

### **Exporting**

```js
// utils.js
export const greet = () => console.log("Hello");
export const PI = 3.14;

// Default export
export default function add(a, b) {
  return a + b;
}
```

---

### **Importing**

```js
import add, { greet, PI } from "./utils.js";

add(2, 3);    // 5
greet();      // Hello
console.log(PI); // 3.14
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between default and named exports?**

#### ✅ **How to Answer in an Interview**

- Default export → Only **one per file**, can be imported with any name.
    
- Named exports → Multiple per file, must use **same name when importing**.
    

```js
export default function() {} // Default
export const x = 10;         // Named
```

---

### **2️⃣ What are dynamic imports?**

#### ✅ **How to Answer in an Interview**

- Dynamic imports **load modules at runtime**, using `import()`.
    

```js
import("./math.js").then((module) => {
  module.add(2, 3);
});
```

---

## 🎯 **Interview Tips**

✅ Always **show both export types**.  
✅ Mention that **modules run in strict mode by default**.  
✅ Be ready for follow-ups on **CommonJS (require/module.exports) vs ES Modules**.

# **4️⃣ What is `bind()`, `call()`, and `apply()` in JavaScript, and when do you use them?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **all three are used to control the value of `this` when calling a function**.
    
- Explain **key differences:**
    
    - `call()` → calls immediately, arguments comma-separated
        
    - `apply()` → calls immediately, arguments as an array
        
    - `bind()` → returns a new function without calling it immediately
        

---

## 💡 **Answer**

### 🔹 **bind()**

- Creates a **new function with a fixed `this` value** but does **not execute immediately**.
    

```js
const person = { name: "Alice" };
function greet(msg) {
  console.log(`${msg}, I'm ${this.name}`);
}
const sayHi = greet.bind(person);
sayHi("Hello"); // Hello, I'm Alice
```

---

### 🔹 **call()**

- Calls the function **immediately**, passing arguments **individually**.
    

```js
greet.call(person, "Hi"); // Hi, I'm Alice
```

---

### 🔹 **apply()**

- Similar to `call()`, but **arguments are passed as an array**.
    

```js
greet.apply(person, ["Hey"]); // Hey, I'm Alice
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use `bind()`?**

#### ✅ **How to Answer in an Interview**

- When you **want to create a new function with a fixed `this`**, for later use (e.g., event listeners, callbacks).
    

---

### **2️⃣ What is the difference between call/apply and bind?**

#### ✅ **How to Answer in an Interview**

- **call/apply → execute immediately**
    
- **bind → returns a new function for later execution**
    

---

## 🎯 **Interview Tips**

✅ Always **show examples for all three methods**.  
✅ Mention **use cases – callbacks, borrowing methods, event handlers**.  
✅ Be ready for follow-ups on **how arrow functions ignore `this` binding**.

# **5️⃣ What is `eval()` and why is it considered risky?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **`eval()` executes a string as JavaScript code**.
    
- Mention that **it can be dangerous because it can run malicious code and affect performance**.
    
- Show a simple example but also explain why it’s discouraged.
    

---

## 💡 **Answer**

The **`eval()` function** takes a **string and executes it as JavaScript code**.

```js
eval("console.log(2 + 3)"); // 5
```

---

### 🔹 **Why is it risky?**

1️⃣ **Security risk** – If user input is passed to `eval()`, attackers can inject malicious code.  
2️⃣ **Performance issues** – The code is evaluated at runtime, preventing optimizations.  
3️⃣ **Hard to debug** – Errors in evaluated code are harder to trace.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What are safe alternatives to eval()?**

#### ✅ **How to Answer in an Interview**

- Use JSON methods for parsing (`JSON.parse`).
    
- Use Function constructors or safer logic structures when possible.
    

```js
// Instead of eval("2+3"), do:
const result = Function("return 2 + 3")();
console.log(result); // 5
```

---

### **2️⃣ When is eval() ever necessary?**

#### ✅ **How to Answer in an Interview**

- Rarely – mostly in **dynamic code execution scenarios (REPLs, debugging tools)**.
    
- Should **not** be used for normal application logic.
    

---

## 🎯 **Interview Tips**

✅ Always **say eval() is unsafe and discouraged**.  
✅ Mention **security (XSS attacks)** as the biggest concern.  
✅ Be ready for follow-ups on **JSON parsing vs eval()**.

# **6️⃣ What is a cursor in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Explain that **the term "cursor" can mean different things based on context**.
    
- In **web browsers**, it usually refers to **the mouse pointer or text caret**.
    
- In **databases (Node.js, MongoDB)**, a cursor represents a **pointer to a set of results from a query**.
    
- Clarify **both use cases with examples**.
    

---

## 💡 **Answer**

### 🔹 **1. Cursor in Browser (Mouse Pointer or Text Caret)**

- Refers to the **visual pointer on screen** or **text insertion caret**.
    

```css
button { cursor: pointer; }   /* Changes mouse pointer to hand icon */
input:focus { caret-color: red; } /* Changes text cursor color */
```

---

### 🔹 **2. Cursor in Databases (Node.js / MongoDB)**

- Refers to an **object returned by a database query that can be iterated to fetch results**.
    

```js
const cursor = db.collection("users").find();
cursor.forEach(doc => console.log(doc));
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ In frontend JS, how can you change the cursor style dynamically?**

#### ✅ **How to Answer in an Interview**

- Use the **`style.cursor` property**.
    

```js
document.body.style.cursor = "wait";  // shows loading cursor
```

---

### **2️⃣ In MongoDB/Node.js, why use cursors instead of fetching all results at once?**

#### ✅ **How to Answer in an Interview**

- Cursors **allow fetching large datasets in batches**, reducing memory usage.
    

```js
const cursor = db.collection("users").find();
while (await cursor.hasNext()) {
  console.log(await cursor.next());
}
```

---

## 🎯 **Interview Tips**

✅ Clarify **which "cursor" the interviewer means (UI vs DB)**.  
✅ Give **examples for both frontend and backend use cases**.  
✅ Be ready for follow-ups on **pagination with database cursors**.

# **7️⃣ What is JavaScript sandboxing?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining **sandboxing is a security technique to run code in an isolated environment**.
    
- Mention that it **prevents malicious code from accessing sensitive data or APIs**.
    
- Give **examples of where sandboxing is used (browsers, iframes, Node.js VMs)**.
    

---

## 💡 **Answer**

**JavaScript sandboxing** means running code in a **restricted environment** so it cannot affect the rest of the application or access sensitive resources.

### 🔹 **Where it is used?**

✔ Browsers – **iframes with `sandbox` attribute**  
✔ Node.js – **`vm` module to execute untrusted code**  
✔ Security tools – To **test or execute code safely**

---

## 🧩 **Example (Browser iframe sandbox)**

```html
<iframe src="page.html" sandbox></iframe>
```

✔ The iframe cannot run scripts, submit forms, or open new windows without extra permissions.

---

## 🧩 **Example (Node.js sandbox using vm module)**

```js
const vm = require("vm");
const sandbox = { x: 2 };
vm.createContext(sandbox);

vm.runInContext("x += 3", sandbox);
console.log(sandbox.x); // 5
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is sandboxing important?**

#### ✅ **How to Answer in an Interview**

- To **safely execute untrusted code** without giving it access to system or sensitive APIs.
    

---

### **2️⃣ How is sandboxing different from CORS?**

#### ✅ **How to Answer in an Interview**

- **Sandboxing** → Isolates code execution.
    
- **CORS** → Controls cross-origin requests.
    

---

## 🎯 **Interview Tips**

✅ Always **mention both frontend (iframe sandbox) and backend (vm module)**.  
✅ Emphasize **security and isolation** as the main purpose.  
✅ Be ready for follow-ups on **real-world cases like online code editors or ad scripts**.

--------------------------------------------------------------------------

# ✅ Advanced JavaScript Concepts – Interview Prep

Each question below includes a beginner-friendly explanation, real code examples, the answer you would give in an interview, and any trailing (follow-up) questions you might encounter — with their answers too.

## 1. What is the prototype in JavaScript?

**Explanation:**  
In JavaScript, every object has a hidden internal property called `[[Prototype]]`, which refers to another object. You can think of this as a template or parent object. This prototype object enables **inheritance**, so if a property or method isn't found on the object itself, JavaScript looks for it in its prototype.

You can access the prototype using `.prototype` for functions/classes, or `Object.getPrototypeOf(obj)` for object instances.

**Example:**

javascript

``function Person(name) {   this.name = name; } Person.prototype.sayHello = function() {   return `Hi, I'm ${this.name}`; }; const john = new Person("John"); console.log(john.sayHello()); // Hi, I'm John``

**What to say in an interview:**  
"Prototypes allow JavaScript objects to inherit properties and methods from other objects. It's part of how inheritance works in JS — if an object doesn't have a property, it checks its prototype."

## 💬 Trailing Question: How do you set or change the prototype of an object?

**Answer:**  
Use `Object.create()` to create an object with a specific prototype, or `Object.setPrototypeOf(obj, prototype)` to modify one manually.

**Example:**

javascript

`let animal = { eats: true }; let rabbit = Object.create(animal); console.log(rabbit.eats); // true`

**What to say:**  
"I use `Object.create()` to create an object with a given prototype. I can also use `Object.setPrototypeOf()` to change the prototype explicitly, though it’s not recommended for performance reasons."

## 2. What is the prototype chain and how does inheritance work?

**Explanation:**  
When an object is missing a property, JavaScript looks up the prototype chain:

- Starts with the object itself
    
- Then its prototype (`[[Prototype]]`)
    
- Then that prototype’s prototype, and so on…
    
- Until it reaches `null`
    

This chain enables inheritance — objects can "inherit" behavior from other objects.

**Example:**

javascript

`let animal = {   eats: true,  walk() { console.log("Animal walks"); } }; let rabbit = Object.create(animal); rabbit.jump = true; rabbit.walk(); // inherited from animal`

**What to say in an interview:**  
"The prototype chain is how JavaScript implements inheritance. If an object doesn’t have a property, JavaScript looks up through the prototype chain until it finds the property or reaches null."

## 💬 Trailing Question: What is the prototype of built-in types like arrays or functions?

**Answer:**  
Built-in types like arrays, functions, and objects all have their own prototypes:

javascript

`console.log(Array.prototype);  // prototype for all arrays console.log(Function.prototype); // prototype for all functions`

**What to say:**  
"Native JavaScript objects like arrays and functions have prototype objects too, like Array.prototype. When I use array methods like `map` or `push`, they come from this prototype."

## 3. What are JavaScript modules, and how do you import/export them?

**Explanation:**  
JavaScript **modules** are individual files that encapsulate logic and can export functions, variables, or classes for other files to use. Modules help keep code organized, reusable, and maintainable.

**Syntax:**

- **Exporting**
    

javascript

`// utils.js export function add(a, b) {   return a + b; }`

- **Importing**
    

javascript

`// app.js import { add } from './utils.js'; console.log(add(2, 3)); // 5`

**What to say in an interview:**  
"Modules let me split my code into files and reuse pieces of functionality using export and import. It improves structure and avoids polluting the global scope."

## 💬 Trailing Question: What's the difference between a named and default export?

**Answer:**

- **Named export:** Can export several items using `export { item1, item2 }` — requires the same name when importing.
    
- **Default export:** Only one per file — can import with any name.
    

**Example:**

javascript

`// Default export export default function greet() {   console.log("Hi"); }`

javascript

`import sayHello from './greet.js'; // can name it anything`

**What to say:**  
"Default exports send one thing from a module, and I can name it anything when importing. Named exports let me share multiple functions or values and require the same name during import."

## 4. What is `bind`, `call`, and `apply` in JavaScript, and when do you use them?

**Explanation:**  
All three methods allow you to change the value of `this` inside a function.

- **call:** Calls a function immediately with a specific `this` value and individual arguments.
    
- **apply:** Same as `call`, but takes arguments as an array.
    
- **bind:** Returns a new function with `this` set permanently — doesn’t execute it immediately.
    

**Example:**

javascript

``function greet(greeting) {   console.log(`${greeting}, ${this.name}`); } const person = { name: "Alice" }; greet.call(person, "Hi");         // Hi, Alice greet.apply(person, ["Hello"]);   // Hello, Alice const boundGreet = greet.bind(person); boundGreet("Hey");                // Hey, Alice``

**What to say in an interview:**  
"`call` and `apply` let me run a function with a different `this` context right away, and `bind` is used when I want to permanently fix `this` for future use."

## 💬 Trailing Question: When would you use bind?

**Answer:**  
Use `bind` when passing a method as a callback and want to preserve its original `this`.

**Example:**

javascript

`const button = {   label: "Click me",  clickHandler() {    console.log(this.label);  } }; setTimeout(button.clickHandler.bind(button), 1000);`

**What to say:**  
"I use `bind` to ensure that `this` stays correct when methods are passed around, for example in `setTimeout` or event listeners."

## 5. What is eval?

**Explanation:**  
`eval` is a function in JavaScript that executes a string as code. This means it takes a string and runs it as JavaScript within the current scope.

**Example:**

javascript

`let code = "2 + 2"; console.log(eval(code)); // 4 let x = 10; eval("x = x * 2"); console.log(x); // 20`

**What to say in an interview:**  
"`eval` lets me execute a string as code, but it's rarely recommended because it can open up security risks, debugging problems, and performance issues. Safer alternatives almost always exist."

## Trailing Question: When should you avoid using eval?

**Answer:**  
You should avoid `eval` almost always, especially with user-generated strings. It can execute malicious code (security risk), slow down performance, and make code harder to maintain or debug. Native JavaScript features (like dynamic object access, `Function` constructor, or JSON methods) are safer and preferred.

**What to say:**  
"I avoid `eval` because it can run unsafe code if the content isn't trusted, and it's bad for code speed and readability."

## 6. What is a cursor in JavaScript? (Context clarification: Often refers to database or iterators in JS)

**Explanation:**

- In databases (like MongoDB), a **cursor** is an object returned from a query, used to iterate over results one at a time without loading everything into memory.
    
- In standard JavaScript, the closest analogy is an **iterator**—a protocol allowing you to step through data structures, often used with `for...of` loops or custom iteration logic.
    

**Example (MongoDB-style pseudo-JS):**

javascript

`let cursor = db.collection.find(); while (cursor.hasNext()) {   print(cursor.next()); }`

**Example (JavaScript iterators):**

javascript

`let arr = [1, 2, 3]; let iterator = arr[Symbol.iterator](); console.log(iterator.next().value); // 1`

**What to say in an interview:**  
"In database contexts, a cursor lets me traverse query results one row at a time. In JavaScript, iterators serve a similar idea—allowing controlled traversal over a data set."

## Trailing Question: How are iterators and generators connected?

**Answer:**  
A **generator** function returns an iterator each time it's called. It allows you to produce values one by one, pausing and resuming as needed (using `yield`).

**Example:**

javascript

`function* nums() {   yield 1;  yield 2;  yield 3; } let gen = nums(); console.log(gen.next().value); // 1`

**What to say:**  
"Generators are special functions that build iterators, letting me return (yield) values one at a time, which is efficient for handling large or infinite sequences."
