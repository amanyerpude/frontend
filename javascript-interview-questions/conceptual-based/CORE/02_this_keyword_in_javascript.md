- youtube_link
	- ### [Javascript Interview Questions ( 'this' Keyword ) - Output Based, Scope, Implicit Binding, etc](https://www.youtube.com/watch?v=rv7Q11KWmKU&pp=ygUadGhpcyBrZXl3b3JkIGluIGphdmFzY3JpcHQ%3D "Javascript Interview Questions ( 'this' Keyword ) - Output Based, Scope, Implicit Binding, etc")

--------------------------------------------------------------------------


--------------------------------------------------------------------------
- this keyword in Javascript | this in arrow function explained by Frontend Master
- Video_Link : https://youtu.be/kvTzkt8BwGc?si=8pnDhOcIg0gpFkK8


This response draws exhaustively from the provided source material, detailing every concept and rule related to the `this` keyword in JavaScript, its execution context, and associated functions (`call`, `apply`, `bind`, and arrow functions).

---

## I. Introduction and Agenda

The primary goal of the presentation is to explore the **`this` keyword in JavaScript** and clear up all doubts surrounding it.

The specific agenda points covered are:

1. The ways a function can be called in JavaScript.
2. What the **Execution Context (EC)** is and how it helps in understanding `this`.
3. The **four rules** needed to find the value of `this` (which allow finding the value within seconds).
4. What a **Lexical Scope** is.
5. How the value of `this` works in **Arrow Functions**.
6. How the value of `this` works in **Event Listeners**.
7. How **`call`, `bind`, and `apply`** methods work.
8. Solving output-based questions using the knowledge and skills learned.
9. A concluding Q&A session.

---

## II. The Water Analogy (Scenario)

Before diving into the four ways to call a function, a scenario involving water is presented.

- If water is put into a **glass**, its shape changes according to the glass.
- If water is put into a **bucket**, its shape changes according to the bucket.
- If water is put into a **bowl**, its shape changes according to the bowl.
- This example is later used to **relate to `this`**, illustrating that the value of `this` is contextual.

---

## III. Four Ways to Call a Function

The value of `this` depends on _how_ a function is called. In each of these four ways, the value of `this` inside the function will be set differently.

Using a sample function `showMessage()`:

1. **Direct Call (Default Binding):** Calling the function directly using the moon bracket syntax (e.g., `showMessage()`).
2. **Using the `new` Keyword (Constructor Call):** Calling the function with `new` (e.g., `new showMessage()`).
    - This method returns an object.
    - If no arguments are passed, the parentheses can be skipped (e.g., `new showMessage`).
3. **Using `call` or `apply` (Explicit Binding):** Calling the function using `.call()` or `.apply()`.
4. **Method Invocation (Implicit Binding):** Creating an object (`const obj1`), assigning the function to a property (`obj1.showMessage = showMessage`), and then calling it using the dot operator (`obj1.showMessage()`).

---

## IV. Execution Context (EC)

Understanding the Execution Context is necessary to grasp the working of the `this` keyword.

### A. Code Execution Phases

JavaScript code executes in two phases:

1. **Memory Allocation Phase:** Memory is allocated. **Scope setting** and **variable initialization** occur.
    - For variables declared with `var`, the default value of `undefined` is assigned.
    - The complete body of functions is assigned.
    - Variables are attached to their respective scopes.
2. **Code Running Phase:** The code is run. The JavaScript engine knows the default values and locations of variables and functions.

### B. Hoisting

**Hoisting** is simply the result of the memory allocation phase, where variables and functions are assigned before execution. Because allocation occurs first, accessing variables before declaration does not cause errors.

### C. Execution Context Creation and Function

- An **Execution Context is created when a function is called**.
- The EC is an **area in memory where code executes**.
- When a function is called, the EC is created and **pushed onto the call stack**.
- The EC can be conceptualized as a box created for every function call. If there are 20 function calls, 20 ECs are created.
- The EC has access to the **Global Scope** and all resources the function requires.

### D. The `this` Variable in EC

- Every Execution Context possesses a special variable of **object type** known as **`this`**.
- When an EC is created, a new object is created "magically".
- **Default Value:** If the `this` value is not specified during the function call, the default value of `this` is the **Window Object**.
- **EC Lifecycle:** Once a function's execution is finished, the EC is deleted, and its corresponding `this` value is also deleted.
- **Conclusion:** The number of function calls equals the number of Execution Contexts, which equals the number of different `this` values.

---

## V. The Four Rules of `this`

The value of `this` inside any function depends entirely on how that function is called.

|Rule|Method of Calling|Value of `this`|Exception/Condition|
|:--|:--|:--|:--|
|**Rule 1: Default Binding**|Simple Function Call (e.g., `showMessage()`)|**Window Object**|If **Strict Mode** (`'use strict'`) is on, `this` is **`undefined`**.|
|**Rule 2: Constructor Call**|Using the `new` Keyword (e.g., `new showMessage()`)|**Newly Created Object**|The `new` keyword creates an empty object and sets `this` to that object.|
|**Rule 3: Explicit Binding**|Using `call` or `apply` (e.g., `fn.call(obj)`)|The **Object Passed as the First Argument**|`call` and `apply` are used specifically to set a custom `this` value.|
|**Rule 4: Implicit Binding**|Method Invocation (Using Dot Operator, e.g., `obj.method()`)|The **Object Itself** upon which the method was called|The object acts as the context for the function.|

---

## VI. Lexical Scope

Lexical scope dictates how variables are looked up and is crucial for understanding arrow functions.

- **Definition:** Lexical scope is a scope that exists only at **author time** (when the code is being written).
- **Fixed Scope:** Lexical means "fixed". Unlike Block, Function, and Global scopes, which become active when the code runs, lexical scope is defined when the code is written. The scope of a variable cannot be changed at runtime.
- **Lookup:** JavaScript lookup is based on the lexical scope.
    - To find a variable, the engine first looks in the **current scope**.
    - If not found, it moves one level up to the **parent scope**.
    - If still not found, it goes to the **Global Scope**.
- **Analogy:** The lookup process can be understood using an elevator analogy, starting at ground zero and moving up floors until the item is returned.

---

## VII. `this` in Arrow Functions

- **Lexical Lookup:** In arrow functions, the value of `this` is **always found lexically**.
- **No Binding:** Arrow functions **do not have their own `this` binding**. Internally, `this` inside an arrow function is **always `undefined`**.
- **Mechanism:** Since an arrow function's `this` is undefined, the JavaScript engine looks one level up (to the parent scope) to find what `this` is bound to.
    - If defined globally, `this` is the **Window Object**.
    - If the arrow function is inside a regular function, it inherits the `this` value of the parent function, even if that parent function's `this` was explicitly set using `call`.
- **Object Literal Warning (The Fundamental Mistake):** Defining an arrow function inside an object literal (e.g., `const obj = { func: () => this }`) does **not** create a new scope. The curly braces represent an Object Literal Syntax, not a block-level scope. In this case, the arrow function looks up to the **Global/Window Scope**.

---

## VIII. `this` in Event Listeners

- When attaching an event listener (e.g., `click`, `keyup`) to a DOM element using `addEventListener`, the value of `this` inside the handler function will point to **the DOM element itself** upon which the event listener was attached.

---

## IX. `call`, `apply`, and `bind` Methods

These three similar methods are used to set a **custom `this` value** inside a function.

### A. `call` Method

- **Function:** Used to control the `this` value and **immediately invoke** the function.
- **Arguments:** The custom `this` object is passed as the **first argument**. Any additional parameters are passed as **comma-separated arguments** after the `this` object.

### B. `apply` Method

- **Function:** Works **exactly like `call`** (controls `this` and invokes immediately).
- **Arguments:** The custom `this` object is the first argument. The only difference is that additional parameters are sent within an **array**.
    - Internally, the `apply` method structures the array elements to be received as standard arguments in the function.

### C. `bind` Method

- **Function:** Fixes the value of `this` permanently inside a function.
- **Return Value:** `bind` **returns a new function**; it does **not** invoke the original function immediately.
- **Arguments:** The custom `this` object is the first argument. Additional arguments are passed in a **comma-separated way**.
- **Permanence:** Once `this` has been permanently fixed using `bind`, subsequent attempts to change `this` using `call` or `apply` on the bound function will fail; the permanently fixed value remains.
- **Use Case:** `bind` is highly beneficial when passing a function as a callback (e.g., to `setTimeout`), ensuring that the required `this` context is retained.

---

## X. Practice Question Outcomes

The following details were observed during the practice questions:

1. **Variable Access:** To access a variable within an object (that is not a property of `this`), the `this` keyword is not required. `this` is used to access keys/properties on the object.
2. **Arrow Function in Object:** Arrow functions determine `this` based on their lexical parent. Even when an arrow function method is assigned to a variable and then called globally, it still references the object context because its lexical parent is the object.
3. **Callback `this`:** When a function is passed as a callback (e.g., to `setTimeout`), the invoking mechanism (like `setTimeout`) does not attach a custom `this` value, resulting in **`undefined`** (or Window Object, depending on the environment and strict mode).
4. **Mixed Function Types in Object:**
    - A **normal function** inside an object uses Implicit Binding (Rule 4), and `this` points to the object itself.
    - An **arrow function** inside an object looks up lexically. Since the surrounding braces are not a scope, it goes to the Global/Window object, resulting in `undefined` if the property is not global.
5. **Nested Implicit Binding:** When calling a function deeply nested in objects (e.g., `user.childObject.getDetails()`), Rule 4 applies: `this` points to the **immediate parent object** upon which the method was called (`childObject`), not the grandparent object (`user`).

## Summary of Key Takeaways

The source highlights **six** things that must be remembered to understand `this`:

1. The **four rules** of `this`.
2. How **`this` behaves in arrow functions** (lexically bound).
3. How **`this` behaves in event handlers** (bound to the DOM element).

--------------------------------------------------------------------------


--------------------------------------------------------------------------
- this keyword in JavaScript 🔥 | Ep.06 - Namaste JavaScript Season 2 🙏
- Video_Link : https://youtu.be/9T4z98JcHR0?si=BRD5T3u7aF6kSONY

The `this` keyword in JavaScript is cited as one of the most **confusing topics**. The challenge lies in that it **behaves very differently when it is in different circumstances**. Mastering the foundation of the `this` keyword is crucial for day-to-day coding and success in interviews.

Below is a detailed breakdown of how the `this` keyword behaves in various circumstances, drawing comprehensively from the provided source material.

---

## 1. `this` in Global Space

The space outside of any function is referred to as the **global space**.

|Concept|Detail|Source Citations|
|:--|:--|:--|
|**General Value**|In the global space, the value of `this` will always represent the **global object**.||
|**Runtime Dependence**|The global object varies depending on the JavaScript runtime environment.||
|**Value in Browsers**|In the case of browsers, the global object is the **`window` object**.||
|**Value in Node.js**|In Node.js, the value of the global object is **`Global`**.||

---

## 2. `this` Inside a Function

When `this` is used inside a regular function, its behavior depends on two primary factors: the strict mode setting and how the function is called.

### Dependence on Strict vs. Non-Strict Mode

The `this` keyword works differently in strict mode and non-strict mode.

1. **Strict Mode (`use strict`)**:
    
    - The value of `this` inside the function is **`undefined`**.
    - Strict mode implements stricter rules for JavaScript.
2. **Non-Strict Mode (Default)**:
    
    - The value of `this` inside the function is the **`window` object** (or the global object).
    - This happens due to a phenomenon called **`this` substitution**.

### The Concept of `this` Substitution

`This` substitution is a phenomenon that occurs **only in non-strict mode**.

- If the value of the `this` keyword is initially **`undefined` or `null`**.
- JavaScript will **replace this keyword with the global object**.
- This is why, in non-strict mode in a browser, the initial undefined value is replaced by the `window` object.

### Dependence on Function Invocation

The value of the `this` keyword inside a function also depends on **how the function is called** (runtime binding).

- **Called Without Reference (Normal Call, e.g., `X()`):** If the function is called without any reference of an object (in strict mode), the value of `this` is **`undefined`**.
- **Called With Reference (e.g., `window.X()`):** If the function is executed using an object reference (like `window.X`), the calling object (e.g., `window`) becomes the value of `this`.

---

## 3. `this` Inside Objects Methods

A function that is made a part of an object is known as a **method**.

|Concept|Detail|Source Citations|
|:--|:--|:--|
|**Value of `this`**|When `this` is used inside a method, its value is the **object where this method is present**.||
|**Reference**|If you call the method as `obj.x()`, `this` inside `x` refers to `obj`. For example, `this.a` inside the method references the property `a` of the object.||

---

## 4. Overriding `this` using Call, Apply, and Bind

`Call`, `Apply`, and `Bind` are three important functions used when you need to **share methods** between objects or explicitly set the value of `this`.

- These three methods are used to **set the value of `this`** inside a function.
- The example provided shows how to reuse the `printName` method from the `student` object for a different object, `student2`.
- By using the `.call()` method (`student.printName.call(student2)`), the value of `this` inside the `printName` function is **overridden** and becomes `student2`.
- The argument passed inside `.call()` determines the value that `this` will take.
- Note: While only `.call()` was demonstrated, the viewer is instructed to learn about `.apply()` and `.bind()` as they are crucial for a complete understanding of `this` and are frequent interview questions.

---

## 5. `this` Inside Arrow Functions

Arrow functions handle the `this` keyword fundamentally differently than traditional functions.

- **No Own `this` Binding:** Arrow functions **do not have their own `this` binding**.
- **Enclosing Lexical Context:** They **retain the value of their enclosing lexical context**.
- **Lexical Definition:** "Lexical" refers to how the code is written and where the object is present inside the code.

### Case 1: Arrow Function as a Top-Level Method

If an arrow function is defined as a method inside an object at the top level (global context is the enclosing lexical context):

- The value of `this` will be the **global object** (e.g., `window` in a browser).
- It does not behave like a method of the object; it behaves as if it were written in the global space.

### Case 2: Nested Arrow Function

If an arrow function is nested inside a regular function (which is an object method):

- The arrow function's **enclosing lexical context is the regular function**.
- The arrow function will behave exactly as `this` would behave inside that enclosing function.
- In this scenario, since the regular function (the enclosing context) is a method called via the object (`obj2.x()`), the `this` inside the arrow function will refer to **`obj2`**.

---

## 6. `this` Inside DOM Elements

When using the `this` keyword inside event handlers for Document Object Model (DOM) elements (e.g., an `onclick` handler in HTML):

- The value of `this` provides a **reference to the HTML element itself**.
- For example, if used within an `onclick` handler on a button, `this` refers to the **HTML Button Element**.
- This allows interaction with the element, such as accessing properties like `this.tagname`, which would return "BUTTON".

---

## 7. Omitted Topics

The source material explicitly mentions that the behavior of `this` inside **JavaScript classes and constructors** is different but is **not covered** because object-oriented programming (OOP) and classes had not been taught in the series yet. However, it is explicitly stated that the information provided is generally sufficient for daily coding and interview preparation, as classes are not always written in JavaScript development.

---

## Final Review and Summary Points

The topic of the `this` keyword is often misunderstood. Developers must move beyond superficial knowledge and understand the in-depth concepts provided.

Key takeaways and recurring points mentioned in the source include:

- The value of `this` can be highly confusing due to its differing behavior in different circumstances.
- Understanding `this` in functions requires knowing the difference between **strict and non-strict modes** and the behavior of **`this` substitution**.
- The value of `this` in functions depends on **how the function is called** (runtime binding).
- In arrow functions, always look for the **enclosing lexical context**.
- The functions **`call`, `apply`, and `bind`** are essential for manipulating the value of `this`.
- JavaScript is celebrated as an amazing and beautiful language, provided one understands how it works behind the scenes.

The speaker encourages viewers to take notes and complete the homework of watching videos on `call`, `apply`, and `bind`. Viewers are also requested to like, share, and comment on the video, including trying to explain the definition of `this` in their own words.

--------------------------------------------------------------------------


--------------------------------------------------------------------------

- Javascript Interview Questions ( 'this' Keyword ) - Output Based, Scope, Implicit Binding, etc
- Video_Link : https://youtu.be/rv7Q11KWmKU?si=_EOA_fWU63pijONL


This response covers all details mentioned in the provided source regarding the JavaScript `this` keyword, organized for clarity and learning.

---

## The JavaScript `this` Keyword: Concepts and Contexts

The `this` keyword in JavaScript is considered one of the most confusing topics, sometimes causing even senior developers difficulty. Due to its complexity, it is a highly important topic for JavaScript interviews, allowing interviewers to pose tricky questions.

### I. General Definition and Object Binding

**Definition:** In JavaScript, the `this` keyword is used to reference something, typically an object. Just as the pronoun "this" in English references a specific item (e.g., "fruits are kept in this bucket," referencing the bucket), JavaScript uses `this` for referencing. Since all elements in JavaScript, including functions, are first-class objects, the meaning of `this` depends entirely on the **context** it is currently in.

**Types of Object Binding:** There are two types of object binding in JavaScript:

1. **Implicit Binding:** This is applied when a function within an object is invoked using the **dot notation**. In these scenarios, `this` points to the object used to invoke the function, or simply the object on the left-hand side of the dot.
2. **Explicit Binding:** This is applied using the methods `call`, `bind`, and `apply`. This type of binding is slated for discussion in the next video in the series.

### II. Behavior of `this` in Different Contexts

The value of `this` changes depending on where it is executed:

#### 1. Global Context

- In the global context, `this` points to the **global object**.
- When run in a browser environment, printing `this` results in the **window object**.
- _Example:_ Running `this.a = 5` globally and then logging `this` shows the window object containing `a = 5`.

#### 2. Normal Functions

- **Standalone Function Call:** If a normal function (like `getParam`) is called outside of an object, `this` targets its parent object, which is again the **window object**.
- **Function Inside an Object (Implicit Binding):** If a normal function is defined within an object, `this` points to that immediate **parent object**.
    - _Example:_ In `user.getDetails()`, `this` points to the `user` object.
- **Nested Object:** If a normal function is nested within a child object inside a parent object, the function only points to the **immediate parent** (the inner child object), not the outer object.

#### 3. Arrow Functions

- The primary characteristic of the arrow function is that the value of `this` is inherited from the **outer scope** or the **outer normal function**.
- If an arrow function is executed globally or directly inside an object without an enclosing normal function, it targets the **window object**.
- _Nested Example:_ If an arrow function (`nested arrow`) is placed inside a normal function (`getDetails`), and `getDetails` is a method of an object (`user`), the arrow function inherits the reference of `this` from `getDetails`. Because `getDetails` points to the `user` object, the nested arrow function also points to the `user` object.

#### 4. Classes and Constructors

- Inside a class, `this` points to **everything that is inside the constructor**.
- When a new object is created using the `new` keyword and the class (e.g., `new User('push')`), the constructor defines the properties (`this.name`) and the object gains access to methods defined in the class.

### III. Essential JavaScript Interview Questions

The source discusses several tricky output-based questions related to `this`:

#### Question 1: Basic Implicit Binding

- **Scenario:** An object with `firstName: push` and a method `getName` returning `this.firstName`. The method also has a local variable called `firstName`.
- **Outcome:** The output is **"push"**.
- **Reasoning:** `this` points to the parent object (`user`), not the local function scope.

#### Question 2: Object Creation and `this` Reference

- **Scenario:** A function `makeUser` returns an object `{ name: 'john', ref: this }`. The code then attempts to access `user.ref.name`.
- **Initial Problem:** When `makeUser` is called, the parent object is the **window object**. Therefore, `this` assigned to `ref` points to the window object, which lacks a `name` property. Output is empty/undefined.
- **Solution/Fix:** To make `ref` point to the `user` object, `ref` must be defined as a **function** that returns `this`: `ref: function() { return this; }`. The access must then be changed to `user.ref().name`.
- **Fixed Output:** **"john"**.

#### Question 3: `setTimeout` and Loss of Context

- **Scenario:** A `user` object with a `logMessage` method logging `this.name`. `setTimeout` calls `user.logMessage` after one second.
- **Initial Problem:** `setTimeout` uses the method as a **callback**. The function is copied and executes independently, losing access to the `user` object. `this` defaults to the **window object**.
- **Initial Output:** **Undefined**.
- **Solution/Fix:** Wrap the call inside an **anonymous function** within the `setTimeout`: `setTimeout(function() { user.logMessage(); }, 1000)`. This invokes it as a method of the `user` object.
- **Fixed Output:** **"pushagarwal"**.

#### Question 4: Arrow Function vs. Normal Function in an Object

- **Scenario:** An object has two methods: `greet` (normal function) and `farewell` (arrow function), both accessing `this.name`.
- **Output Analysis:**
    - `greet` (Normal): `this` points to the `user` object. Output: **"Hello push"**.
    - `farewell` (Arrow): `this` points to the outer scope (the **window object**) because there is no parent normal function. Output: **"Good bye undefined"**.

#### Question 5: Calculator Object Implementation

- **Task:** Create a `calculator` object with methods `read`, `sum`, and `mul` (or `multiply`).
- **Implementation Details:**
    - The `read` method prompts the user for two values, stored as `this.a` and `this.b`.
    - The values prompted by the user must be converted into numbers (e.g., by adding a `+` prefix to the prompt call) because `prompt` accepts input as a string.
    - `sum` returns `this.a + this.b`.
    - `multiply` returns `this.a * this.b`.

#### Question 6: Using the `arguments` Array

- **Scenario:** Global `length = 4`. Object `obj` with `length = 5` and a method that takes a `callback` and other arguments (e.g., 2, 3). The method calls the callback using `arguments()`.
- **Analysis:**
    - The `arguments` keyword captures all passed parameters as an array.
    - The specific array in this case is `[callback function, 2, 3]`.
    - When the function is called via `arguments()`, it executes with `this` targeting its parent object, which is the **arguments array itself**.
    - The array object has a standard `length` property.
- **Output:** The length of the array is 3. The output is **3**.

#### Question 7: Implementing Chainable Methods (`calc`)

- **Task:** Implement a `calc` object/function that allows infinite chaining of methods (`add(10).multiply(2).subtract(30)`).
- **Core Requirement:** For chaining to work, every method (`add`, `multiply`, `subtract`) must perform its operation on an internal `this.total` variable and then **return the entire object (`return this`)**.
- **Implementation Details:**
    1. Initialize `calc` with `total = 0`.
    2. Define methods (`add`, `multiply`, `subtract`) that update `this.total` and then return `this`.
- _Note:_ This specific question was asked during the speaker's Cast24 interview.

### IV. Other Details

- The presenter uses **VS Code** with simple HTML, CSS, and JavaScript files to demonstrate the code. They use Live Server to run the HTML file and demonstrate the output in the console.
- The speaker encourages viewers to follow them on Twitter at `twitter.com/push_eon`.
- Viewers can access a blog post containing the video's content and interview questions via a link in the description.
- The speaker offered to create a separate, in-depth video on classes, constructors, or the `new` keyword if requested.
- The next video in the series will explain the explicit binding methods (`call`, `bind`, and `apply`), which is a very important topic for JavaScript interviews.

--------------------------------------------------------------------------