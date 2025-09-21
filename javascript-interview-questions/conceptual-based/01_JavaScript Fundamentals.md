
```markdown
# 🧠 JavaScript Fundamentals

1. What are the different data types in JavaScript?  
2. Is JavaScript a dynamically typed or statically typed language?  
3. What is the `typeof` operator in JavaScript?  
4. What is `NaN`, and how is it different from `null` and `undefined`?  
5. 🌟What is the difference between `null` and `undefined`?  
6. What is the difference between undeclared and undefined variables?  
7. 🌟What is the difference between `==` and `===` in JavaScript?  
8. When would you use `==` vs `===` in real-world code?  
9. What is the output of `3 + 2 + "7"` and why?  
10. 🌟What is the difference between pass by value and pass by reference in JavaScript?  
11. What does `preventDefault()` do in an event handler?  
12. Walk me through what happens when you type a URL and press Enter in the browser.
```


--------------------------------------------------------------------------
# **1️⃣ What are the different data types in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by categorising data types into **primitive** and **non-primitive (reference)**.
    
- Mention that JavaScript is **dynamically typed**, meaning variable types can change at runtime.
    
- Give examples of each type rather than just listing them.
    

---

## 💡 **Answer**

JavaScript has two main categories of data types:

### 🔹 **Primitive Types** (Immutable, stored by value)

1. **String** – Text data. Example: `"Hello"`.
    
2. **Number** – Integers & floats. Example: `42`, `3.14`.
    
3. **Boolean** – `true` or `false`.
    
4. **Null** – Represents an intentional empty value.
    
5. **Undefined** – Variable declared but not assigned a value.
    
6. **Symbol (ES6)** – Unique, immutable identifiers.
    
7. **BigInt (ES11)** – Very large integers beyond `Number.MAX_SAFE_INTEGER`.
    

### 🔹 **Non-Primitive Types** (Mutable, stored by reference)

- **Object** – Key-value collections (includes arrays, functions, dates).
    
    ```js
    let person = { name: "John", age: 30 };
    ```
    

JavaScript is **dynamically typed**, meaning variables can hold different types at runtime:

```js
let x = 42;   // number
x = "Hello";  // string
```

---

## 🧩 **Example**

```js
let name = "Alice";        // String
let age = 25;              // Number
let isAdmin = false;       // Boolean
let score;                 // Undefined
let big = 1234567890n;     // BigInt
let uniqueId = Symbol();   // Symbol
let person = { name, age } // Object
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why does `typeof null` return `"object"`?**

#### ✅ **How to Answer in an Interview**

- Acknowledge that this is a well-known bug in JavaScript.
    
- Briefly explain the historical reason behind it.
    

#### 💡 **Answer**

`typeof null` returns `"object"` because of a legacy bug in the first implementation of JavaScript.  
Although `null` is a **primitive type**, its internal tag was mistakenly set as an object reference in early versions and was never fixed for backward compatibility.

---

### **2️⃣ What is the difference between `undefined` and `null`?**

#### ✅ **How to Answer in an Interview**

- Explain that `undefined` is the default uninitialized state.
    
- `null` is an intentional empty value assigned by the developer.
    

#### 💡 **Answer**

- **undefined** → A variable is declared but not assigned any value.
    
- **null** → A deliberate assignment to represent "no value".
    

```js
let a;       // undefined
let b = null; // null
```

---

### **3️⃣ Are arrays and functions separate data types?**

#### ✅ **How to Answer in an Interview**

- Clarify that arrays and functions are **special kinds of objects**.
    

#### 💡 **Answer**

No, arrays and functions are **not separate data types**.

- **Arrays** are objects with numeric keys.
    
- **Functions** are callable objects.
    

```js
console.log(typeof []); // "object"
console.log(typeof function(){}); // "function"
```

---

## 🎯 **Interview Tips**

✅ Always differentiate **primitive vs reference types**.  
✅ Mention **dynamic typing** to show deeper understanding.  
✅ Be ready for follow-ups about `typeof null`, `BigInt`, `Symbol`.

# **2️⃣ Is JavaScript a dynamically typed or statically typed language?**

---

## ✅ **How to Answer in an Interview**

- Start by defining **dynamic vs static typing**.
    
- State clearly that JavaScript is **dynamically typed**.
    
- Explain with an example showing that variables can change type at runtime.
    
- Mention the optional use of **TypeScript** for static typing.
    

---

## 💡 **Answer**

JavaScript is a **dynamically typed language**, meaning you don’t have to specify the type of a variable when declaring it.  
The type is determined **at runtime**, and a variable can hold values of different types over its lifetime.

In contrast, **statically typed languages** (like Java, C, TypeScript) require variables to have a fixed type at compile time.

---

## 🧩 **Example**

```js
let x = 10;      // x is a Number
x = "Hello";     // Now x is a String
x = true;        // Now x is a Boolean
```

This is valid in JavaScript because type checks happen at **runtime**, not at compile time.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is JavaScript considered loosely typed?**

#### ✅ **How to Answer in an Interview**

- Explain that "loosely typed" means variables are not strictly bound to a type.
    

#### 💡 **Answer**

JavaScript is **loosely typed** because:

- Variables can hold any type without explicit declaration.
    
- Type coercion is common, e.g., `"5" - 2` results in `3`.
    

---

### **2️⃣ How does TypeScript relate to static typing?**

#### ✅ **How to Answer in an Interview**

- Mention that TypeScript is a superset of JavaScript.
    

#### 💡 **Answer**

TypeScript adds **static typing** to JavaScript by allowing developers to define variable types at compile time.  
Example:

```ts
let x: number = 5;  // Error if assigned a string later
```

TypeScript compiles to plain JavaScript but helps catch type-related errors early.

---

### **3️⃣ What are the pros and cons of dynamic typing?**

#### ✅ **How to Answer in an Interview**

- Mention flexibility as a pro and runtime errors as a con.
    

#### 💡 **Answer**

✅ **Pros:**

- Flexibility in writing code.
    
- Faster prototyping and less boilerplate.
    

❌ **Cons:**

- More prone to runtime errors.
    
- Harder to maintain large codebases.
    

---

## 🎯 **Interview Tips**

✅ Show that you know **why JavaScript is dynamic**.  
✅ Mention **TypeScript** to show awareness of static typing in modern frontend development.  
✅ If asked for an example, **show type coercion or reassignment at runtime**.

# **3️⃣ What is the `typeof` operator in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that `typeof` is a **unary operator** used to determine the data type of a value.
    
- Mention that it returns a **string** describing the type.
    
- Highlight special cases like `typeof null` returning `"object"`.
    

---

## 💡 **Answer**

The `typeof` operator in JavaScript is used to **check the data type** of a value or variable.  
It returns a **string** representing the type.

---

## 🧩 **Example**

```js
console.log(typeof "Hello");   // "string"
console.log(typeof 42);        // "number"
console.log(typeof true);      // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object" (bug)
console.log(typeof {});        // "object"
console.log(typeof []);        // "object" (arrays are objects)
console.log(typeof function(){}); // "function"
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why does `typeof null` return `"object"`?**

#### ✅ **How to Answer in an Interview**

- Mention that it’s a well-known bug in JavaScript kept for backward compatibility.
    

#### 💡 **Answer**

`typeof null` returns `"object"` because of a bug in JavaScript’s early implementation, where `null`’s internal type tag was mistakenly set to object.  
This behaviour persists for compatibility reasons, even though `null` is a **primitive**.

---

### **2️⃣ What does `typeof NaN` return?**

#### ✅ **How to Answer in an Interview**

- Point out the counterintuitive result and why it happens.
    

#### 💡 **Answer**

```js
console.log(typeof NaN); // "number"
```

`NaN` (Not-a-Number) is still considered a **numeric value**, hence `typeof NaN` returns `"number"`.

---

### **3️⃣ Can `typeof` distinguish between arrays and objects?**

#### ✅ **How to Answer in an Interview**

- Clarify that `typeof` cannot differentiate arrays from objects.
    

#### 💡 **Answer**

No.

```js
typeof [] // "object"
typeof {} // "object"
```

To check for arrays, use `Array.isArray(arr)`.

---

### **4️⃣ What is the difference between `typeof` and `instanceof`?**

#### ✅ **How to Answer in an Interview**

- Explain that `typeof` checks **basic type**, while `instanceof` checks **prototype chain**.
    

#### 💡 **Answer**

- `typeof` → Good for primitives.
    
- `instanceof` → Good for checking if an object is created by a particular constructor.
    

```js
[] instanceof Array   // true
[] instanceof Object  // true
```

---

## 🎯 **Interview Tips**

✅ Always mention **special cases** like `null`, `NaN`, and arrays.  
✅ Be ready to compare `typeof` vs `instanceof` if asked.  
✅ For bonus points, show **real code output** for tricky cases.

# **4️⃣ What is `NaN`, and how is it different from `null` and `undefined`?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining what `NaN` means (Not-a-Number).
    
- Clarify that `NaN` is still of type **number**.
    
- Then explain how it differs from `null` (intentional empty value) and `undefined` (uninitialized variable).
    
- Provide examples of when each occurs.
    

---

## 💡 **Answer**

`NaN` stands for **Not-a-Number** and represents the result of an invalid number operation in JavaScript.  
It is still of type **number**, even though it indicates an invalid numeric value.

`null` and `undefined` are **different special values**:

- **null** → Intentional assignment of "no value".
    
- **undefined** → Variable is declared but not assigned any value.
    

---

## 🧩 **Example**

```js
console.log(0 / 0);       // NaN
console.log(parseInt("a"));// NaN
console.log(typeof NaN);  // "number"

let a;
console.log(a);           // undefined

let b = null;
console.log(b);           // null
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is `typeof NaN` `"number"`?**

#### ✅ **How to Answer in an Interview**

- Explain that NaN is part of JavaScript's Number type.
    

#### 💡 **Answer**

`NaN` is a special value of the **Number type** that represents an invalid numeric result.  
That’s why `typeof NaN` returns `"number"`.

---

### **2️⃣ How can you check if a value is `NaN`?**

#### ✅ **How to Answer in an Interview**

- Mention that `===` comparison doesn’t work because `NaN !== NaN`.
    

#### 💡 **Answer**

Use `Number.isNaN()` or `isNaN()`:

```js
console.log(NaN === NaN);       // false
console.log(Number.isNaN(NaN)); // true
console.log(isNaN("text"));     // true (after coercion)
```

---

### **3️⃣ How are `null` and `undefined` different?**

#### ✅ **How to Answer in an Interview**

- Explain meaning + default behaviour.
    

#### 💡 **Answer**

- **undefined** → Default for uninitialized variables.
    
- **null** → A deliberate value representing "no value".
    

```js
let x;      // undefined
let y = null; // null
```

---

### **4️⃣ Does `null` equal `undefined`?**

#### ✅ **How to Answer in an Interview**

- Show behaviour with `==` vs `===`.
    

#### 💡 **Answer**

```js
console.log(null == undefined);  // true  (type coercion)
console.log(null === undefined); // false (strict equality)
```

---

## 🎯 **Interview Tips**

✅ Always mention that **NaN is of type number**.  
✅ Use examples of **invalid operations** producing `NaN`.  
✅ Be ready for follow-ups about equality and type coercion.

# **5️⃣ What is the difference between `null` and `undefined`?**

---

## ✅ **How to Answer in an Interview**

- Start by stating that both represent “no value,” but in **different ways**.
    
- Emphasize that `undefined` is the **default value** for uninitialized variables, whereas `null` is **explicitly assigned** by developers.
    
- Mention how they behave with `typeof`, `==`, and `===`.
    

---

## 💡 **Answer**

- **undefined** → A variable is declared but not assigned a value.
    
- **null** → A deliberate assignment to represent “no value.”
    

### **Key Differences**

|Feature|`undefined`|`null`|
|---|---|---|
|**Meaning**|Variable not assigned any value|Intentional empty value|
|**Type**|`"undefined"`|`"object"` (legacy bug)|
|**Default Value**|Yes (for uninitialized variables)|No (must be assigned manually)|

---

## 🧩 **Example**

```js
let a;
console.log(a);           // undefined
console.log(typeof a);    // "undefined"

let b = null;
console.log(b);           // null
console.log(typeof b);    // "object" (bug)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Does `null == undefined` return true?**

#### ✅ **How to Answer in an Interview**

- Show that loose equality performs type coercion.
    

#### 💡 **Answer**

```js
console.log(null == undefined);  // true  (type coercion)
console.log(null === undefined); // false (strict equality)
```

---

### **2️⃣ When should you use `null` vs `undefined`?**

#### ✅ **How to Answer in an Interview**

- Explain that developers assign `null` intentionally.
    

#### 💡 **Answer**

- Use `null` when you want to **explicitly clear or reset** a variable.
    
- Let variables remain `undefined` if they are **not yet initialized**.
    

---

### **3️⃣ What does `typeof null` and `typeof undefined` return?**

#### ✅ **How to Answer in an Interview**

- Mention the legacy bug for `null`.
    

#### 💡 **Answer**

```js
console.log(typeof null);      // "object" (bug)
console.log(typeof undefined); // "undefined"
```

---

### **4️⃣ Is `void 0` the same as `undefined`?**

#### ✅ **How to Answer in an Interview**

- Mention that `void 0` is a safe way to get `undefined`.
    

#### 💡 **Answer**

Yes. `void 0` always evaluates to `undefined` and cannot be reassigned like `undefined` could in old JavaScript versions.

---

## 🎯 **Interview Tips**

✅ Always mention **intentional vs default value**.  
✅ Show examples of equality (`==` vs `===`).  
✅ Mention the `typeof null` bug for bonus points.

# **6️⃣ What is the difference between undeclared and undefined variables?**

---

## ✅ **How to Answer in an Interview**

- Begin by defining **undeclared** (variable not defined in the current scope).
    
- Define **undefined** (variable declared but not assigned a value).
    
- Show examples of both.
    
- Mention that using an undeclared variable throws a **ReferenceError**, while `undefined` is a valid value.
    

---

## 💡 **Answer**

- **Undeclared variable** → A variable that has never been declared in the scope. Accessing it causes a **ReferenceError**.
    
- **Undefined variable** → A variable that is declared but has not been assigned any value yet.
    

---

## 🧩 **Example**

```js
// ❌ Undeclared variable
console.log(x); // ReferenceError: x is not defined

// ✅ Undefined variable
let y;
console.log(y); // undefined
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What happens if you use an undeclared variable in strict mode?**

#### ✅ **How to Answer in an Interview**

- Mention that strict mode prevents accidental global variables.
    

#### 💡 **Answer**

In **strict mode**, using an undeclared variable **throws a ReferenceError** immediately.  
Without strict mode, assigning to an undeclared variable implicitly creates a **global variable** (bad practice).

```js
"use strict";
z = 10; // ReferenceError: z is not defined
```

---

### **2️⃣ What is the difference between `var`, `let`, and `const` with respect to declaration?**

#### ✅ **How to Answer in an Interview**

- Show that `var` can be hoisted, whereas `let` and `const` are block-scoped.
    

#### 💡 **Answer**

- `var` variables are hoisted and initialized with `undefined`.
    
- `let` and `const` are hoisted but **not initialized** → accessing them before declaration gives **ReferenceError (TDZ)**.
    

```js
console.log(a); // undefined
var a = 5;

console.log(b); // ReferenceError
let b = 10;
```

---

### **3️⃣ Can you check if a variable is undeclared without throwing an error?**

#### ✅ **How to Answer in an Interview**

- Mention `typeof` as a safe check.
    

#### 💡 **Answer**

Yes. Using `typeof` prevents errors:

```js
console.log(typeof x); // "undefined" (no error even if x is undeclared)
```

---

### **4️⃣ Why is accessing an undeclared variable different from accessing a property that doesn't exist?**

#### ✅ **How to Answer in an Interview**

- Clarify that objects return `undefined` for missing properties.
    

#### 💡 **Answer**

```js
console.log(person.age); // undefined (property doesn't exist)
console.log(age);        // ReferenceError (variable undeclared)
```

---

## 🎯 **Interview Tips**

✅ Show both **ReferenceError** and **undefined** outputs in examples.  
✅ Mention **strict mode behaviour**.  
✅ Knowing about **TDZ (Temporal Dead Zone)** gives bonus points.

# **7️⃣ What is the difference between `==` and `===` in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that `==` is **loose equality** and performs **type coercion**, while `===` is **strict equality** and does **not perform type coercion**.
    
- Provide examples that show the difference.
    
- Mention that **using `===` is considered best practice** in modern JavaScript.
    

---

## 💡 **Answer**

- `==` → Compares **values** after performing **type coercion**.
    
- `===` → Compares **values and types** without type coercion.
    

---

## 🧩 **Example**

```js
console.log(5 == "5");   // true  (type coercion)
console.log(5 === "5");  // false (different types)

console.log(null == undefined);  // true
console.log(null === undefined); // false

console.log(true == 1);  // true
console.log(true === 1); // false
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Which one should you prefer – `==` or `===`?**

#### ✅ **How to Answer in an Interview**

- Mention best practices for cleaner, predictable code.
    

#### 💡 **Answer**

Always **prefer `===` (strict equality)** to avoid unexpected type coercion.  
Use `==` only when **type coercion is intentional and well-understood**.

---

### **2️⃣ Why does `null == undefined` return true?**

#### ✅ **How to Answer in an Interview**

- Explain how loose equality treats `null` and `undefined` as equivalent.
    

#### 💡 **Answer**

Loose equality (`==`) considers `null` and `undefined` **loosely equal**, so:

```js
console.log(null == undefined);  // true
console.log(null === undefined); // false
```

---

### **3️⃣ What about objects with `==` and `===`?**

#### ✅ **How to Answer in an Interview**

- Explain that objects are compared **by reference**, not by value.
    

#### 💡 **Answer**

```js
let a = { x: 1 };
let b = { x: 1 };

console.log(a == b);   // false (different references)
console.log(a === b);  // false
console.log(a === a);  // true
```

---

### **4️⃣ Are there any tricky cases with `==`?**

#### ✅ **How to Answer in an Interview**

- Show how type coercion can lead to unexpected results.
    

#### 💡 **Answer**

```js
console.log(0 == false);    // true
console.log("" == 0);       // true
console.log([] == false);   // true
console.log([] == ![]);     // true
```

---

## 🎯 **Interview Tips**

✅ Show **type coercion pitfalls** to impress the interviewer.  
✅ Always recommend **using `===`** for cleaner, bug-free code.  
✅ If asked, mention that **`Object.is()`** can also be used for strict equality with slight differences.

# **8️⃣ When would you use `==` vs `===` in real-world code?**

---

## ✅ **How to Answer in an Interview**

- Begin by stating that **`===` is preferred** for most cases because it avoids unexpected type coercion.
    
- Explain that `==` can be used **only when intentional type coercion is desired**.
    
- Provide examples of both cases.
    

---

## 💡 **Answer**

In real-world code:

- ✅ **Use `===` (strict equality)** in almost all cases for predictable comparisons.
    
- ✅ **Use `==` (loose equality)** only when you **intentionally want type coercion**, such as checking for `null` or `undefined` in one go.
    

---

## 🧩 **Example**

```js
// Best Practice
let age = "18";
if (Number(age) === 18) {
  console.log("Adult");
}

// Intentional loose check for null or undefined
let value = null;
if (value == null) { 
  console.log("Value is null or undefined");
}
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is `value == null` sometimes preferred over `value === null`?**

#### ✅ **How to Answer in an Interview**

- Mention that loose equality can check for both `null` and `undefined`.
    

#### 💡 **Answer**

`value == null` returns **true** if `value` is either `null` or `undefined`.  
This is a common shorthand to check for both cases at once.

```js
let a;
if (a == null) console.log("No value"); // true
```

---

### **2️⃣ Are there any performance differences between `==` and `===`?**

#### ✅ **How to Answer in an Interview**

- Explain that performance difference is negligible in modern engines.
    

#### 💡 **Answer**

There is **no significant performance difference** in modern JavaScript engines. The choice is about **code clarity and avoiding bugs**, not speed.

---

### **3️⃣ What about comparing objects with `==` or `===`?**

#### ✅ **How to Answer in an Interview**

- Explain that both operators compare object references.
    

#### 💡 **Answer**

Both `==` and `===` compare **object references**, not contents:

```js
let a = {x:1};
let b = {x:1};

console.log(a === b); // false (different references)
```

---

### **4️⃣ How can you compare object values correctly?**

#### ✅ **How to Answer in an Interview**

- Mention deep comparison techniques.
    

#### 💡 **Answer**

Use JSON stringify or a deep equality function:

```js
JSON.stringify(a) === JSON.stringify(b); // true (value comparison)
```

---

## 🎯 **Interview Tips**

✅ Show a **real scenario** where `==` is acceptable (null/undefined check).  
✅ Mention that **modern best practice is to always use `===`**.  
✅ If asked, briefly explain **Object.is()** and deep equality for objects.

# **9️⃣ What is the output of `3 + 2 + "7"` and why?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining how JavaScript evaluates expressions **from left to right**.
    
- Show that numbers are added first, then type coercion occurs when a string is encountered.
    
- Emphasize that `+` acts as **both addition and string concatenation**.
    

---

## 💡 **Answer**

The output is **`57`** (a string).

### **Why?**

1. Expression is evaluated **left to right**.
    
2. `3 + 2` → Both are numbers → Result is `5`.
    
3. `5 + "7"` → Number + String → Number is converted to string → `"5" + "7"` → `"57"`.
    

---

## 🧩 **Example**

```js
console.log(3 + 2 + "7"); // "57"
console.log("3" + 2 + 7); // "327" (first operand is a string)
console.log(3 + (2 + "7")); // "327" (parentheses change evaluation order)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What will be the output of `"7" + 3 + 2`?**

#### ✅ **How to Answer in an Interview**

- Show that type coercion starts earlier because the first operand is a string.
    

#### 💡 **Answer**

Output → `"732"`  
Reason:

- `"7" + 3` → `"73"`
    
- `"73" + 2` → `"732"`
    

---

### **2️⃣ What about `"7" - 3`?**

#### ✅ **How to Answer in an Interview**

- Explain that `-` only works with numbers.
    

#### 💡 **Answer**

Output → `4` (number)  
Reason: The `-` operator forces numeric conversion: `Number("7") - 3`.

---

### **3️⃣ How does `+` behave with different types?**

#### ✅ **How to Answer in an Interview**

- Explain that `+` is the only operator that performs concatenation.
    

#### 💡 **Answer**

- If **both operands are numbers**, it adds them.
    
- If **any operand is a string**, it performs **string concatenation**.
    

---

### **4️⃣ How can you avoid such coercion issues?**

#### ✅ **How to Answer in an Interview**

- Mention explicit conversion methods.
    

#### 💡 **Answer**

Use `Number()` or `String()`:

```js
console.log(3 + 2 + Number("7")); // 12
console.log(String(3 + 2) + "7"); // "57"
```

---

## 🎯 **Interview Tips**

✅ Always **explain step-by-step evaluation order**.  
✅ Show similar tricky examples (`"7" + 3 + 2`, `"7" - 3`).  
✅ Mention **explicit type conversion** to avoid bugs.

# **🔟 What is the difference between pass by value and pass by reference in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **primitive values are passed by value**, while **objects (including arrays and functions) are passed by reference**.
    
- Clarify that JavaScript **always passes arguments by value**, but in the case of objects, the value is a reference to the object.
    
- Provide examples showing how changes affect (or don’t affect) the original variable.
    

---

## 💡 **Answer**

- **Pass by value** → A copy of the value is passed. Changing the parameter does **not** affect the original variable.
    
- **Pass by reference** → A reference (memory address) is passed. Changes inside the function **affect the original object**.
    

---

## 🧩 **Example**

```js
// Pass by value (primitives)
let x = 10;
function modifyValue(a) {
  a = 20;
}
modifyValue(x);
console.log(x); // 10 (unchanged)

// Pass by reference (objects)
let obj = { value: 10 };
function modifyObj(o) {
  o.value = 20;
}
modifyObj(obj);
console.log(obj.value); // 20 (changed)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Does JavaScript always use pass by value?**

#### ✅ **How to Answer in an Interview**

- Explain that even for objects, the reference itself is passed **by value**.
    

#### 💡 **Answer**

Yes. Technically, **everything in JavaScript is passed by value**.

- For primitives → value is copied.
    
- For objects → the **reference itself** is copied, but both copies point to the same object.
    

---

### **2️⃣ How can you prevent a function from modifying an object argument?**

#### ✅ **How to Answer in an Interview**

- Mention object cloning techniques.
    

#### 💡 **Answer**

Create a **shallow or deep copy** before passing:

```js
let objCopy = { ...obj };      // shallow copy
let arrCopy = [...arr];        // array copy
```

---

### **3️⃣ Are arrays passed by reference?**

#### ✅ **How to Answer in an Interview**

- Clarify that arrays are objects.
    

#### 💡 **Answer**

Yes. Arrays are objects, so they are **passed by reference**:

```js
let arr = [1, 2];
function addItem(a) { a.push(3); }
addItem(arr);
console.log(arr); // [1, 2, 3]
```

---

### **4️⃣ How to achieve true pass by value for objects?**

#### ✅ **How to Answer in an Interview**

- Mention deep cloning.
    

#### 💡 **Answer**

Use deep copy techniques:

```js
let newObj = JSON.parse(JSON.stringify(obj)); // deep copy
```

---

## 🎯 **Interview Tips**

✅ Explain **primitive vs reference types** clearly.  
✅ Use **examples for both cases**.  
✅ Bonus points if you clarify **that JS technically always passes by value, but for objects, the value is a reference**.

# **1️⃣1️⃣ What does `preventDefault()` do in an event handler?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that `preventDefault()` is used to **stop the browser’s default behaviour** for a particular event.
    
- Give **real-world examples** like preventing form submission or disabling link navigation.
    
- Clarify that it does **not stop event propagation** (unlike `stopPropagation()`).
    

---

## 💡 **Answer**

`preventDefault()` is a method available on the **event object** that stops the browser from performing its default action for that event.

For example:

- Preventing a link from navigating.
    
- Preventing form submission when validation fails.
    

---

## 🧩 **Example**

```html
<form id="myForm">
  <button type="submit">Submit</button>
</form>

<script>
document.getElementById("myForm").addEventListener("submit", function(event) {
  event.preventDefault(); // Stops form from submitting
  console.log("Form submission prevented!");
});
</script>
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between `preventDefault()` and `stopPropagation()`?**

#### ✅ **How to Answer in an Interview**

- Explain that one stops default behaviour and the other stops event bubbling.
    

#### 💡 **Answer**

- `preventDefault()` → Stops browser’s default behaviour.
    
- `stopPropagation()` → Stops the event from bubbling up the DOM tree.
    

```js
event.preventDefault();  // Prevents form submission
event.stopPropagation(); // Stops parent handlers from being triggered
```

---

### **2️⃣ When would you use `preventDefault()` in real projects?**

#### ✅ **How to Answer in an Interview**

- Mention practical scenarios.
    

#### 💡 **Answer**

- **Form validation** → Prevent submission if fields are invalid.
    
- **Custom link behaviour** → Prevent `<a>` from navigating.
    
- **Drag & drop events** → Prevent default browser handling.
    

---

### **3️⃣ Does `preventDefault()` cancel event listeners?**

#### ✅ **How to Answer in an Interview**

- Clarify that it only affects the default browser behaviour.
    

#### 💡 **Answer**

No. `preventDefault()` does **not cancel event listeners**. Other event handlers will still run unless `stopPropagation()` is also called.

---

### **4️⃣ Can `preventDefault()` be called on all events?**

#### ✅ **How to Answer in an Interview**

- Explain that it only works on events with default behaviour.
    

#### 💡 **Answer**

No. It only works on events that have default browser behaviour (like form submit, link click, drag events, etc.).

---

## 🎯 **Interview Tips**

✅ Show at least **one practical example** (form submission is best).  
✅ Mention the **difference from `stopPropagation()`**.  
✅ Bonus points for explaining that **default behaviour varies by event type**.

# **1️⃣2️⃣ Walk me through what happens when you type a URL and press Enter in the browser.**

---

## ✅ **How to Answer in an Interview**

- Start with a **high-level flow** (DNS → TCP → HTTP → Rendering).
    
- Walk through the key steps in order.
    
- Keep it concise but structured—interviewers like **step-by-step clarity**.
    
- Mention key concepts like DNS lookup, TCP handshake, HTTP request/response, HTML parsing, and rendering.
    

---

## 💡 **Answer**

When you type a URL and press Enter, the browser performs these steps:

### **1️⃣ DNS Resolution**

- The browser checks cache for the IP of the domain.
    
- If not found, it queries a DNS server to resolve the domain name to an IP address.
    

### **2️⃣ TCP Handshake & TLS Setup (if HTTPS)**

- The browser establishes a TCP connection (3-way handshake).
    
- If HTTPS, a TLS handshake happens to encrypt communication.
    

### **3️⃣ HTTP Request Sent**

- The browser sends an HTTP request (GET) to the server.
    

### **4️⃣ Server Processes Request**

- The server processes the request and sends back an HTTP response with headers and HTML content.
    

### **5️⃣ Browser Receives Response**

- The browser parses the HTML, builds the DOM, downloads CSS, JS, and images.
    

### **6️⃣ Rendering**

- CSSOM and DOM are combined into a render tree.
    
- Layout is computed, and pixels are painted to the screen.
    
- JS execution (if any) modifies the DOM dynamically.
    

---

## 🧩 **Example Diagram (in words)**

**URL → DNS Lookup → TCP/TLS → HTTP Request → HTTP Response → Parse HTML → Build DOM + CSSOM → Render Page → JS Execution.**

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is DNS, and why is it needed?**

#### ✅ **How to Answer in an Interview**

- Explain DNS as the “phonebook” of the internet.
    

#### 💡 **Answer**

DNS (Domain Name System) converts **domain names** (like `google.com`) into **IP addresses** that computers use to communicate.

---

### **2️⃣ What is the difference between HTTP and HTTPS?**

#### ✅ **How to Answer in an Interview**

- Mention encryption and security.
    

#### 💡 **Answer**

- **HTTP** → Data is sent in plain text.
    
- **HTTPS** → Adds TLS encryption for secure communication.
    

---

### **3️⃣ What happens after the first HTML is loaded?**

#### ✅ **How to Answer in an Interview**

- Mention parsing and additional requests.
    

#### 💡 **Answer**

The browser parses HTML and makes additional requests for CSS, JS, and images. It builds the DOM and CSSOM, executes JS, and then renders the page.

---

### **4️⃣ What is the difference between DNS lookup and caching?**

#### ✅ **How to Answer in an Interview**

- Mention browser and OS caching.
    

#### 💡 **Answer**

Browsers cache DNS results. If cached, DNS lookup is skipped; otherwise, a DNS query is made to resolve the IP.

---

### **5️⃣ Where does the browser store cookies in this process?**

#### ✅ **How to Answer in an Interview**

- Connect HTTP response with cookies.
    

#### 💡 **Answer**

Cookies are sent by the server via `Set-Cookie` headers in the response. They are stored in the browser and sent back in subsequent requests to the same domain.

---

## 🎯 **Interview Tips**

✅ Keep the answer **step-by-step, not a long paragraph**.  
✅ Mention DNS, TCP, HTTP, and rendering phases.  
✅ If the interviewer asks for more depth, be ready to talk about **CDNs, caching, and JS execution order**.

--------------------------------------------------------------------------
--------------------------------------------------------------------------
