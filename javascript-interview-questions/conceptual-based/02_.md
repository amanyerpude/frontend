
```markdown
# 🔒 Variables & Scope

1. 🌟 What is the difference between `var`, `let`, and `const` in JavaScript?  
2. 🌟 What is hoisting in JavaScript?  
3. What is the Temporal Dead Zone?  
4. 🌟 What is the `this` keyword in JavaScript and how does it behave in various scenarios?
5. Types of scope in JavaScript?
6. 🌟What is lexical scope?
7. What is variable hoisting in JavaScript? 🌟Write code.
```


--------------------------------------------------------------------------
# **1️⃣ What is the difference between `var`, `let`, and `const` in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Begin by explaining that all three are used for variable declaration but differ in **scope**, **hoisting**, and **reassignment rules**.
    
- Provide a **comparison table** for clarity.
    
- Show a code example for each.
    

---

## 💡 **Answer**

`var`, `let`, and `const` are all used to declare variables in JavaScript, but they differ in **scope**, **hoisting**, and **mutability**.

### 🔹 **Key Differences**

|Feature|`var`|`let`|`const`|
|---|---|---|---|
|**Scope**|Function-scoped|Block-scoped|Block-scoped|
|**Hoisting**|Hoisted & initialized as `undefined`|Hoisted but in **TDZ** until declared|Hoisted but in **TDZ** until declared|
|**Reassignment**|Allowed|Allowed|❌ Not allowed|
|**Redeclaration**|Allowed|❌ Not allowed|❌ Not allowed|

---

## 🧩 **Example**

```js
// var
var a = 10;
var a = 20; // Redeclaration allowed

// let
let b = 10;
// let b = 20; // ❌ Error (cannot redeclare)

// const
const c = 10;
c = 20; // ❌ Error (cannot reassign)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What happens when you use `var` inside a block `{}`?**

#### ✅ **How to Answer in an Interview**

- Mention that `var` ignores block scope.
    

#### 💡 **Answer**

```js
if (true) {
  var x = 10;
}
console.log(x); // 10 (var is function-scoped, not block-scoped)
```

---

### **2️⃣ Can you modify objects declared with `const`?**

#### ✅ **How to Answer in an Interview**

- Explain that `const` prevents reassignment, not mutation.
    

#### 💡 **Answer**

```js
const obj = { name: "John" };
obj.name = "Mike"; // ✅ Allowed (mutation)
obj = {};          // ❌ Error (reassignment not allowed)
```

---

### **3️⃣ Why is `let` preferred over `var`?**

#### ✅ **How to Answer in an Interview**

- Mention modern best practices.
    

#### 💡 **Answer**

`let` prevents issues caused by hoisting and function scope leaks, making code **safer and more predictable**.

---

### **4️⃣ What happens if you access a `let` variable before declaration?**

#### ✅ **How to Answer in an Interview**

- Mention **Temporal Dead Zone (TDZ)**.
    

#### 💡 **Answer**

Accessing it before declaration results in **ReferenceError** because the variable is in TDZ.

---

## 🎯 **Interview Tips**

✅ Always include **scope, hoisting, and reassignment rules**.  
✅ Show that **const prevents reassignment but allows mutation**.  
✅ Mention that **modern JS prefers `let` & `const` over `var`**.

# **2️⃣ What is hoisting in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **hoisting moves variable and function declarations to the top of their scope** during compilation.
    
- Clarify that **only declarations are hoisted, not initializations**.
    
- Show how it behaves differently for `var`, `let`, `const`, and functions.
    

---

## 💡 **Answer**

Hoisting is JavaScript's default behaviour of **moving declarations to the top of their scope** during the compile phase.

- **Variable declarations (`var`)** are hoisted but initialized with `undefined`.
    
- **`let` and `const`** are hoisted but remain in the **Temporal Dead Zone (TDZ)** until declared.
    
- **Function declarations** are hoisted with their entire definition.
    
- **Function expressions** behave like variables.
    

---

## 🧩 **Example**

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ReferenceError (TDZ)
let b = 10;

// Function declaration hoisted
sayHello(); // "Hello"
function sayHello() {
  console.log("Hello");
}

// Function expression NOT hoisted
sayHi(); // ❌ TypeError
var sayHi = function() { console.log("Hi"); };
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why does `var` behave differently from `let` and `const`?**

#### ✅ **How to Answer in an Interview**

- Mention historical behaviour of JavaScript.
    

#### 💡 **Answer**

`var` was designed before block scope existed in JavaScript. It is **function-scoped** and **hoisted with initialization as `undefined`**, whereas `let` and `const` are **block-scoped** and remain in **TDZ**.

---

### **2️⃣ Are arrow functions hoisted?**

#### ✅ **How to Answer in an Interview**

- Clarify that arrow functions are like function expressions.
    

#### 💡 **Answer**

Arrow functions are **not hoisted**. They behave like variables declared with `const` or `let`.

---

### **3️⃣ Why is understanding hoisting important?**

#### ✅ **How to Answer in an Interview**

- Explain that it helps avoid bugs.
    

#### 💡 **Answer**

Because **accessing variables/functions before declaration** can lead to unexpected `undefined` values or runtime errors due to TDZ.

---

### **4️⃣ Does hoisting happen in strict mode?**

#### ✅ **How to Answer in an Interview**

- Clarify that hoisting is part of the language, not mode-dependent.
    

#### 💡 **Answer**

Yes, hoisting always happens, but strict mode prevents certain behaviours like **using undeclared variables**.

---

## 🎯 **Interview Tips**

✅ Show **examples for both variables and functions**.  
✅ Mention **TDZ for `let` and `const`**.  
✅ Bonus points for differentiating **function declaration vs expression hoisting**.

# **3️⃣ What is the Temporal Dead Zone (TDZ)?**

---

## ✅ **How to Answer in an Interview**

- Start by defining TDZ as the **period between variable hoisting and its initialization**.
    
- Explain that accessing a `let` or `const` variable in TDZ **throws a ReferenceError**.
    
- Contrast it with `var`, which is hoisted and initialized to `undefined`.
    

---

## 💡 **Answer**

The **Temporal Dead Zone (TDZ)** is the time between **when a variable is hoisted** and **when it is initialized** in the code.

- Variables declared with `let` and `const` are **hoisted but not initialized**.
    
- Accessing them **before their declaration** results in a **ReferenceError**.
    

---

## 🧩 **Example**

```js
console.log(a); // ReferenceError (TDZ)
let a = 10;

console.log(b); // ReferenceError (TDZ)
const b = 20;

console.log(c); // undefined (var is hoisted and initialized)
var c = 30;
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why does TDZ exist?**

#### ✅ **How to Answer in an Interview**

- Explain that TDZ enforces safer code.
    

#### 💡 **Answer**

TDZ prevents accessing variables **before they are declared**, making code more predictable and avoiding errors caused by premature access.

---

### **2️⃣ Does TDZ apply to `function` declarations?**

#### ✅ **How to Answer in an Interview**

- Clarify that functions behave differently.
    

#### 💡 **Answer**

No. **Function declarations are hoisted with their definition**, so they can be called before declaration.

---

### **3️⃣ Does TDZ apply to `class` declarations?**

#### ✅ **How to Answer in an Interview**

- Mention that classes also have TDZ.
    

#### 💡 **Answer**

Yes. Classes are **hoisted but not initialized**, so using them before declaration throws a **ReferenceError**.

```js
const obj = new MyClass(); // ReferenceError
class MyClass {}
```

---

### **4️⃣ How can TDZ prevent bugs?**

#### ✅ **How to Answer in an Interview**

- Give a practical reason.
    

#### 💡 **Answer**

TDZ prevents **using variables before initialization**, which is a common source of runtime bugs in older JavaScript using `var`.

---

## 🎯 **Interview Tips**

✅ Always **contrast TDZ behaviour with `var` hoisting**.  
✅ Mention that **both `let` and `const` are block-scoped and affected by TDZ**.  
✅ Bonus points for mentioning **classes also have TDZ**.

# **4️⃣ What is the `this` keyword in JavaScript and how does it behave in various scenarios?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that `this` refers to the **context** in which a function is called.
    
- Clarify that its value **depends on how the function is invoked**, not where it is defined.
    
- Cover behaviour in **global scope, object methods, arrow functions, event handlers, and classes**.
    

---

## 💡 **Answer**

The `this` keyword refers to the **execution context** of a function. Its value is determined at **runtime**, based on **how the function is called**.

---

### **Behaviour in Different Scenarios**

|Scenario|Value of `this`|
|---|---|
|**Global Scope (Non-Strict)**|`window` (in browsers) or `global` (Node.js)|
|**Global Scope (Strict Mode)**|`undefined`|
|**Inside Object Method**|The object on which the method is called|
|**Standalone Function (Non-Strict)**|`window` or `global`|
|**Standalone Function (Strict)**|`undefined`|
|**Arrow Function**|Inherits `this` from its **lexical scope**|
|**Constructor Function / Class**|The newly created instance|
|**Event Handler**|The element that triggered the event|

---

## 🧩 **Example**

```js
// Global Scope
console.log(this); // window (non-strict) | undefined (strict mode)

// Object Method
const obj = {
  name: "John",
  greet() {
    console.log(this.name);
  },
};
obj.greet(); // "John"

// Arrow Function
const arrow = () => console.log(this);
arrow(); // Inherits from parent scope

// Constructor
function Person(name) {
  this.name = name;
}
const p = new Person("Alice");
console.log(p.name); // "Alice"
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How does `this` work inside an arrow function?**

#### ✅ **How to Answer in an Interview**

- Explain that arrow functions **do not have their own `this`**.
    

#### 💡 **Answer**

Arrow functions inherit `this` from their **lexical (outer) scope**.

```js
const obj = {
  name: "John",
  greet: () => console.log(this.name),
};
obj.greet(); // undefined (inherits global `this`)
```

---

### **2️⃣ How can you explicitly set `this`?**

#### ✅ **How to Answer in an Interview**

- Mention `call()`, `apply()`, and `bind()`.
    

#### 💡 **Answer**

You can explicitly set `this` using:

```js
function greet() { console.log(this.name); }
const user = { name: "Alice" };

greet.call(user);  // "Alice"
greet.apply(user); // "Alice"
const bound = greet.bind(user);
bound();           // "Alice"
```

---

### **3️⃣ What is the difference between `this` in strict mode vs non-strict mode?**

#### ✅ **How to Answer in an Interview**

- Explain global scope behaviour.
    

#### 💡 **Answer**

- **Non-strict mode** → `this` refers to the global object.
    
- **Strict mode** → `this` is `undefined` in standalone functions.
    

---

### **4️⃣ How does `this` behave in event handlers?**

#### ✅ **How to Answer in an Interview**

- Explain DOM-specific behaviour.
    

#### 💡 **Answer**

Inside event handlers, `this` refers to the **element that received the event**.

```js
document.querySelector("button").addEventListener("click", function () {
  console.log(this); // The <button> element
});
```

---

## 🎯 **Interview Tips**

✅ Always mention that **`this` is determined by how a function is called**.  
✅ Include **arrow functions vs normal functions**.  
✅ Mention **explicit binding methods (`call`, `apply`, `bind`)**.

---
