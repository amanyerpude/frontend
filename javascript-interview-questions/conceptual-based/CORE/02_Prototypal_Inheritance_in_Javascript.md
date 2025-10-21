
--------------------------------------------------------------------------
- Prototypal Inheritance in Javascript __proto__ `[[Prototype]]` prototype by Frontend Master
- Video_Link : https://youtu.be/8_tFfRj4NE0?si=QD3wPLYSmrfDPiuO



--------------------------------------------------------------------------

--------------------------------------------------------------------------
- Prototypes & Prototypal Inheritance Explained - Javascript Interview
- Video_Link : https://youtu.be/AOPmqw9scfc?si=ndkzrPYV1flA0gOR



--------------------------------------------------------------------------

--------------------------------------------------------------------------
- OOP / Prototypal Inheritance in JavaScript | Tutorial 006 in Hindi
- Video_Link : https://youtu.be/tHrERc0-z_g?si=Ph2TxRIvPRfV1QPK 

This response draws heavily and comprehensively from the provided source transcript, ensuring all details are included and cited accurately. The response is formatted for easy reading, understanding, and learning, as requested.

---

## JavaScript Object-Oriented Programming (OOP) / Prototypal Inheritance Tutorial Summary

This tutorial covers advanced JavaScript concepts including OOP, which is also referred to as **Prototypal Inheritance**. The goal is to provide a detailed understanding of topics often found confusing by developers.

### I. Video Agenda and Preparatory Notes

The video covers the following main topics:

- Methods, the `this` keyword, and the Window Object.
- `call`, `apply`, and `bind` methods.
- Warnings regarding common coding mistakes.
- The `this` keyword inside Arrow Functions.
- Short Syntax for writing methods.
- Factory Functions and memory-related problems, and their solutions.
- Detailed discussion of `proto` and `prototype` (and their difference).
- The `new` keyword.
- Constructor Functions used with `new`.
- The `class` keyword.
- Examples using the `class` keyword.
- The `super` keyword.
- Method Overriding.
- Getters and Setters.
- Static Methods and Properties.

The viewer is requested to **keep a notebook and pen** ready and make short notes because the concepts covered, such as the `this` keyword, often confuse people.

### II. Methods and the `this` Keyword

#### 1. Defining Methods

- A **Method** is defined as a **Function inside an Object**.
- Example: Creating an object named `person` with keys like `firstName` and `age`.
- To add a method (e.g., `about`), the key's value is set to a function.

#### 2. The Problem with Hardcoding

- If the function body uses hardcoded values (e.g., `Person Name is Harshith`), and the object's properties change (e.g., `firstName` changes to "Mohit"), the method's output becomes incorrect.
- The solution is to use **Template Strings** and reference the properties dynamically.

#### 3. Understanding `this`

- Using `this.Firstname` and `this.Age` solves the hardcoding problem.
- The value of `this` is not known when the code is written; it is determined at **runtime**.
- **Definition:** `this` is **the object that is calling the function** (or method).
    - _Example:_ If `person.about()` is called, the object calling the function is `person`; therefore, `this` inside the `about` method refers to the entire `person` object.

#### 4. Reusing Functions (The Power of `this`)

- A function (e.g., `personInfo`) can be defined _outside_ an object.
- This function can then be set as the value of a method key (e.g., `about`) in multiple objects (`person1`, `person2`, `person3`).
- When `person1.about()` is called, `this` refers to `person1`. When `person2.about()` is called, `this` refers to `person2`. This demonstrates how `this` dynamically adapts based on the calling object.

### III. The Window Object and Global Context

#### 1. Global `this`

- If `this` is written directly in the file (outside a defined object context) when running JavaScript in a browser, it refers to the **Window Object**.
- The Window Object is JavaScript’s **Global Object** and contains methods like `alert` and `confirm`.
- `this` and `window` are the same in this context (`this === window` returns `true`).

#### 2. `this` in Global Functions

- When a function (e.g., `myFunk`) is defined globally and called directly, `console.log(this)` inside it prints the **Window Object**.
- This is because the Window Object is implicitly calling the function (e.g., `window.myFunk()`).

#### 3. Strict Mode Warning

- Using `"use strict"` inside a function or at the top of the file changes the behavior.
- In **Strict Mode**, if a function is called globally, `this` inside that function will be **undefined**, not the Window Object.

### IV. `call`, `apply`, and `bind` Methods

These three methods are very important topics for JavaScript interviews. They allow explicit control over the `this` keyword.

#### 1. `call`

- The `.call()` method allows you to **call any function**.
- **Usage:** The first argument passed to `.call()` sets the value of `this` (the object whose methods are being _borrowed_ or used).
- **Parameters:** Any subsequent arguments are passed **individually** to the original function.
- _Example:_ `user1.about.call(user2)` calls `user1`'s method but ensures `this` refers to `user2`, allowing `user2`'s data (Mohit, 9) to be printed.

#### 2. `apply`

- `apply` is functionally similar to `call`.
- **Difference:** Arguments (parameters) must be passed as an **array (list)**, whereas `call` takes them individually.

#### 3. `bind`

- `bind` does **not call the function immediately**.
- **Usage:** `bind` returns a **new function** with the specified `this` context (and any optional parameters) permanently bound to it.
- The returned function must be stored in a variable and invoked later.

### V. Warnings Regarding Method References

A common mistake is storing a method reference without binding its context.

- If a method reference (e.g., `user1.about`) is stored in a variable (e.g., `myFunk`), only the function's definition is stored.
- When `myFunk()` is called, it is called globally, causing `this` inside the function to default to the Window Object. Since the Window Object does not have `firstName` or `age` properties, the output is `undefined`.
- **Solution:** When storing the reference, use `.bind()` to explicitly set the desired `this` context: `const myFunk = user1.about.bind(user1)`.

### VI. The `this` Keyword in Arrow Functions

The behavior of `this` inside arrow functions is unique and different from regular functions.

- **No Own `this`:** Arrow functions **do not have their own `this`**.
- **Lexical Scoping:** An arrow function gets its `this` value from its **surrounding environment (lexical scope)**.
- If an arrow function is used as a method inside an object, its `this` will look **one level up**. For a globally defined object, this usually means `this` refers to the **Window Object**.
- **Cannot Be Changed:** The `this` context of an arrow function **cannot be changed** using `call`, `apply`, or `bind`.

### VII. Short Syntax Methods

The source introduces a simplified way to write methods inside objects:

- Instead of writing `key: function() {}`, you can use the syntax `key() {}`.
- This creates a method inside the object, and this syntax is the more accurate way to define methods.

### VIII. Factory Functions and Memory Issues (The Evolution of Solutions)

The ultimate goal of OOP in JavaScript is to efficiently create many similar objects (e.g., 1 million user objects).

#### 1. Initial Factory Function Approach

- A function (`createUser`) is built to take user data (first name, age, etc.) as input.
- This function creates an empty object, adds properties and methods (`about`, `is18`), and returns the object.

#### 2. The Memory Problem

- When a million users are created using this method, the methods (`about`, `is18`) are **recreated and stored a million times** in memory, even though their definitions are identical. This is inefficient.

#### 3. Solution 1: Separate Methods Object (Reference Storage)

- Create a separate object (`userMethods`) to hold the common methods.
- Inside the factory function, set the new user object's method key (e.g., `user.about`) equal to the reference of the function stored in `userMethods`.
- This ensures the methods are created only once, and the user object only stores the **reference (address)** to that method.

#### 4. Solution 1's Limitation

- If a new method (e.g., `sing`) is added to `userMethods`, the developer must manually go back into the factory function and add a reference for that new method to every object created. This is tedious and error-prone.

### IX. Prototypes and Inheritance Chains

To solve the manual linking problem, we use JavaScript's built-in prototype mechanism.

#### 1. The Desired Mechanism

- If JavaScript fails to find a property (e.g., `key1`) on an object (`obj2`), it should automatically look up to a linked object (`obj1`) and retrieve the property from there.

#### 2. `Object.create()`

- An empty object can be created using `Object.create()`.
- When using `Object.create(obj1)`, the newly created object (`obj2`) is linked to `obj1`. If a property is missing on `obj2`, JavaScript automatically looks in `obj1`.
- If the property is added directly to `obj2`, JavaScript finds it there first and stops looking up the chain.

#### 3. The `[[Prototype]]` / `__proto__` Link

- The internal reference property that creates this link is called the `[[Prototype]]` (officially in specifications).
- In browsers, this is often exposed as `__proto__` (often pronounced "dunder proto").
- `Object.create(obj1)` sets `obj2`'s `__proto__` property to point to `obj1`.

#### 4. Solution 2: Using `Object.create` in the Factory Function

- In the factory function, create the user object using `const user = Object.create(userMethods)`.
- This automatically sets the new user object’s `__proto__` to the `userMethods` object.
- Now, all methods are accessible without manual reference setting. JavaScript checks the user object, finds no method, follows the `__proto__` link to `userMethods`, and executes the function there. This is much cleaner.

#### 5. The Function's `prototype` Property

- In JavaScript, a function is a combo of a function and an object; they can be treated as objects (e.g., adding custom properties like `hello.myOwnProperty`).
- Every function provides a **free space** property called `prototype`.
- The `prototype` is simply a **plain object** (initially containing only a `constructor` property) that we can use.
- **Crucial Distinction:** The `prototype` property is **only provided by functions**. Objects and arrays do not have a `prototype` property.
    - **`proto`:** A reference used for chaining.
    - **`prototype`:** A simple object that comes free with functions.

#### 6. Solution 3: Using the Constructor Function's `prototype`

- Since the factory function (`createUser`) provides a free `prototype` object, we can store all common methods directly inside `createUser.prototype`.
- We then modify the object creation step to link to this prototype: `const user = Object.create(createUser.prototype)`.
- This achieves the same prototype chaining as Solution 2 but eliminates the need for a separate, manually named `userMethods` object. The user object's `__proto__` is set to the constructor function's `prototype`.

### X. The `new` Keyword and Constructor Functions

The `new` keyword automates the process of linking the new object to the function’s prototype. Functions used with `new` are called **Constructor Functions**.

#### 1. What the `new` Keyword Does (Three Steps)

1. **Creates an Empty Object:** It automatically creates an empty object. This empty object is assigned as the value of `this`.
2. **Sets the Prototype Link:** It automatically sets the new object's `__proto__` to point to the Constructor Function’s `prototype` property (`newObject.__proto__ = Constructor.prototype`).
3. **Returns `this`:** It automatically returns the `this` object (the newly created instance). (Therefore, you do not need to manually write `return user` or `return this` inside the function when using `new`).

#### 2. Applying `new` to Factory Functions

- When using `new` (e.g., `new CreateUser(...)`), the manual `Object.create(CreateUser.prototype)` step is removed.
- Inside the constructor function, properties are set using `this.firstName = firstName`.
- If `new` is forgotten, the prototype link is not created, and the methods defined on the prototype will not be accessible.

#### 3. Constructor Function Conventions

- To signal to other developers that a function must be called with `new`, the function name should **start with a Capital Letter** (e.g., `CreateUser`).

#### 4. `hasOwn Property`

- When using a `for...in` loop to iterate over object keys, it will return keys that are directly on the object _and_ keys that are inherited from the prototype (e.g., `about`, `sing`).
- `object.hasOwnProperty(key)` is used to check if a key is an object's **own property** (not inherited). This allows developers to filter loop results to only include properties added directly in the constructor.

#### 5. Prototypes in Built-in Types (Arrays)

- Array methods (like `filter`, `forEach`) are not stored directly on the array instance.
- Internally, arrays are created using the `Array Constructor` (e.g., `new Array()`).
- All array methods are stored in `Array.prototype`. When you call a method on an array instance, the prototype chain is used to find and execute the method.
- The array's prototype can be checked using `Object.getPrototypeOf(myArray)`. Although `prototype` is usually an object, the `Array.prototype` is actually an array (`Array.isArray(Array.prototype)` returns true).

### XI. The `class` Keyword (ES6 Classes)

The process of manually creating a constructor function and then separately adding methods to its `prototype` is tedious.

#### 1. Classes are Syntactic Sugar

- JavaScript Classes are **"fake"**. They are syntactic sugar, meaning they perform the same internal prototypal inheritance work (creating a constructor and setting the prototype) but offer a cleaner syntax.

#### 2. Class Syntax

- Classes are defined using the `class` keyword (e.g., `class CreateUser`).
- The **`constructor`** method handles initialization, receiving parameters, and setting object properties using `this`.
- Methods (e.g., `about()`, `is18()`) are defined directly inside the class body. These methods are automatically added to the class's `prototype` object.

#### 3. Class Invocation Rules

- The constructor method is called whenever an object (instance) is created using `new`.
- A class constructor **cannot be invoked without `new`**.

### XII. Inheritance and the `super` Keyword

#### 1. Class Inheritance (Extends)

- To avoid repeating code (e.g., duplicating `name`, `age`, and methods like `eat` from `Animal` class to `Dog` class), the `extends` keyword is used.
- `class Dog extends Animal` makes `Dog` the **subclass** (or Derived Class) and `Animal` the **super class** (Base or Parent Class).
- If the subclass (`Dog`) has no constructor, JavaScript uses the super class's (`Animal`) constructor to set the inherited properties.

#### 2. The `super` Keyword

- If a subclass needs to add unique properties (e.g., `speed`), it must define its own constructor.
- Inside the subclass constructor, the `super()` keyword must be called **first**.
- **Purpose:** `super(name, age)` calls the parent (super) class's constructor, ensuring that the inherited properties (`name`, `age`) are initialized correctly before the subclass adds its own properties (`this.speed`).

#### 3. Method Overriding

- If a subclass defines a method that has the same name as a method in its super class (e.g., `eat`), this is called **Method Overriding**.
- When the method is called on the subclass instance (e.g., `dog.eat()`), JavaScript first checks the subclass; if found, the subclass's version is executed, allowing for specific modifications.

### XIII. Getters and Setters

Getters and Setters allow methods to be treated syntactically like properties.

#### 1. Getters

- **The Need:** Methods (like `fullName` calculating `firstName + lastName`) must typically be called with parentheses (`person.fullName()`). The goal is to access them like a property (`person.fullName`).
- **Syntax:** Use the `get` keyword before the method name (e.g., `get fullName()`).
- The method is still executed, but parentheses are not required for the call.

#### 2. Setters

- **The Need:** To allow a user to update multiple related properties (like `firstName` and `lastName`) by assigning a single string to a pseudo-property (e.g., `person.fullName = "Mohit Vashisth"`).
- **Syntax:** Use the `set` keyword before the method name (e.g., `set fullName(value)`).
- The assigned value (the full name string) is passed as an argument.
- Inside the setter, logic is required to process the input (e.g., splitting the full name string by space, and using array destructuring to assign the parts to `this.firstName` and `this.lastName`).

### XIV. Static Methods and Properties

#### 1. Static Methods

- Normal methods are **instance-related** (called by an object: `person1.eat()`).
- **Static Methods** are related directly to the **Class itself**, not its instances.
- **Syntax:** Use the `static` keyword before the method definition (e.g., `static classInfo()`).
- **Calling:** They must be called directly on the class name (e.g., `Person.classInfo()`). They cannot be called on an object instance.
- **Use Cases:** Often used for logic related to initializing or running the application.

#### 2. Static Properties

- **Syntax:** Use the `static` keyword before the property name (e.g., `static DESC = "..."`).
- **Accessing:** Accessed directly using the class name (e.g., `Person.DESC`).
- They cannot be accessed via an object instance.

### XV. Future Topics

The remaining topics to be covered in the tutorial series include:

- How JavaScript Works (Execution Context, Code Reading, Memory Allocation).
- Hoisting.
- Closures.
- Asynchronous JavaScript.
- DOM Manipulation.
- Iterators and Generators.
- Interview questions like Debouncing and Recursion.

--------------------------------------------------------------------------
