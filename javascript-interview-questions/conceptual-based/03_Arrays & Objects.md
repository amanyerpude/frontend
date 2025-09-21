
```markdown
# 🧱 Arrays & Objects

1. What is the difference between an object and an array in JavaScript?  
2. What are different ways to create objects in JavaScript?  
3. What is the difference between `map()` and `forEach()`?  
4. What is the difference between `map()` and 🌟`filter()`?  
5. 🌟What is the difference between 🌟`find()` and `findIndex()`?  
6. 🌟What is the difference between `slice()` and 🌟`splice()`?  
7. What are object methods like `Object.keys()`, `Object.values()`, and `Object.entries()`?  
8. 🌟What is the difference between `Object.freeze()` and `Object.seal()`?  
9. 🌟What is the difference between shallow copy and deep copy?  
10. What is destructuring in JavaScript?  
11. How do you clone an object or array in JavaScript?  
12. 🌟What is a prototype in JavaScript?
13. 🌟Difference between array constructor and `Array.of()`
14. 🌟Able to modify and transform objects (general ablity to handle objects)
```

--------------------------------------------------------------------------
# **1️⃣ What is the difference between an object and an array in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Begin by stating that both objects and arrays are **non-primitive data types**.
    
- Explain that **objects store data as key-value pairs**, while **arrays store ordered data with numeric indices**.
    
- Mention use-cases for each.
    

---

## 💡 **Answer**

- **Object** → Stores data as **key-value pairs**. Keys are usually strings or symbols.
    
- **Array** → Stores **ordered collections** of data with numeric indices.
    

Both are reference types, but **arrays have built-in methods for ordered operations (push, pop, map, filter)**.

---

## 🧩 **Example**

```js
// Object
const user = { name: "Alice", age: 25 };

// Array
const numbers = [10, 20, 30];

console.log(user.name);      // "Alice"
console.log(numbers[1]);     // 20
```

---

### **Key Differences**

|Feature|Object|Array|
|---|---|---|
|Data Structure|Key-value pairs|Ordered list (indexed)|
|Keys|Strings or Symbols|Numeric indices (0,1,2,...)|
|Use Cases|Representing entities|Collections, lists, iterations|
|Methods|`Object.keys()`, `Object.values()`|`map()`, `filter()`, `push()`|

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Is an array an object in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Explain that arrays are specialized objects.
    

#### 💡 **Answer**

Yes. Arrays are objects with **integer-based keys** and a `length` property.

```js
console.log(typeof []); // "object"
```

---

### **2️⃣ When should you use an object vs an array?**

#### ✅ **How to Answer in an Interview**

- Provide practical use cases.
    

#### 💡 **Answer**

- Use **arrays** for **ordered lists** (like users, products).
    
- Use **objects** for **entities with properties** (like a single user).
    

---

### **3️⃣ Can objects have numeric keys like arrays?**

#### ✅ **How to Answer in an Interview**

- Explain key conversion.
    

#### 💡 **Answer**

Yes, but keys are **converted to strings**:

```js
const obj = { 1: "a" };
console.log(Object.keys(obj)); // ["1"]
```

---

### **4️⃣ What is the difference between an array-like object and an array?**

#### ✅ **How to Answer in an Interview**

- Explain that array-like objects lack array methods.
    

#### 💡 **Answer**

Array-like objects (like `arguments`) have indices but **don’t have array methods** (`map`, `filter`).

```js
function test() {
  console.log(arguments.length); // Works
  // arguments.map(...) ❌ Error
}
```

---

## 🎯 **Interview Tips**

✅ Always mention that arrays are **specialized objects with numeric keys**.  
✅ Use **examples to compare access via index vs key**.  
✅ Mention **array-like objects** for bonus points.

# **2️⃣ What are different ways to create objects in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by mentioning that objects can be created in **multiple ways**.
    
- List **all major approaches** – object literal, `new Object()`, constructor functions, ES6 classes, `Object.create()`, and factory functions.
    
- Provide examples for each.
    

---

## 💡 **Answer**

There are several ways to create objects in JavaScript:

---

### **1️⃣ Object Literal (Most Common)**

```js
const user = { name: "Alice", age: 25 };
```

---

### **2️⃣ Using `new Object()`**

```js
const user = new Object();
user.name = "Alice";
user.age = 25;
```

---

### **3️⃣ Constructor Function**

```js
function User(name, age) {
  this.name = name;
  this.age = age;
}
const user = new User("Alice", 25);
```

---

### **4️⃣ ES6 Class**

```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
const user = new User("Alice", 25);
```

---

### **5️⃣ Using `Object.create()`**

```js
const proto = { greet() { console.log("Hello"); } };
const user = Object.create(proto);
user.name = "Alice";
```

---

### **6️⃣ Factory Function**

```js
function createUser(name, age) {
  return { name, age };
}
const user = createUser("Alice", 25);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Which method is most common?**

#### ✅ **How to Answer in an Interview**

- Mention industry preference.
    

#### 💡 **Answer**

The **object literal** syntax (`{}`) is the simplest and most widely used for creating plain objects.

---

### **2️⃣ When would you use `Object.create()`?**

#### ✅ **How to Answer in an Interview**

- Mention prototype-based inheritance.
    

#### 💡 **Answer**

`Object.create()` is useful when you want to create an object with a specific prototype, enabling **prototypal inheritance**.

---

### **3️⃣ What is the difference between a constructor function and a class?**

#### ✅ **How to Answer in an Interview**

- Explain that classes are syntactic sugar.
    

#### 💡 **Answer**

Both achieve the same result.

- Constructor functions were the **old way**.
    
- ES6 classes provide **clearer syntax** for creating objects and inheritance.
    

---

### **4️⃣ What is the difference between `Object.assign()` and `Object.create()`?**

#### ✅ **How to Answer in an Interview**

- Clarify purpose.
    

#### 💡 **Answer**

- `Object.assign()` copies properties from one or more objects to a target object.
    
- `Object.create()` creates a new object with the specified prototype.
    

---

## 🎯 **Interview Tips**

✅ Mention **at least 3–4 approaches**.  
✅ Show that you know **modern approaches (class, factory function)**.  
✅ Bonus points for explaining **when to use each method**.

# **3️⃣ What is the difference between `map()` and `forEach()`?**

---

## ✅ **How to Answer in an Interview**

- Begin by explaining that both methods **iterate over arrays**, but they serve different purposes.
    
- Highlight that `map()` **returns a new array**, while `forEach()` **does not return anything**.
    
- Show **side-effect vs transformation use cases**.
    

---

## 💡 **Answer**

Both `map()` and `forEach()` iterate over arrays, but they differ in behaviour:

|Feature|`map()`|`forEach()`|
|---|---|---|
|**Return Value**|Returns a **new array**|Returns **undefined**|
|**Purpose**|Used for **transformation**|Used for **side effects**|
|**Chaining**|Can be chained with other methods|Cannot be chained|

---

## 🧩 **Example**

```js
const numbers = [1, 2, 3];

// map()
const squared = numbers.map(num => num * num);
console.log(squared); // [1, 4, 9]

// forEach()
numbers.forEach(num => console.log(num * num));
// Logs 1, 4, 9 but returns undefined
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you prefer `map()` over `forEach()`?**

#### ✅ **How to Answer in an Interview**

- Explain that `map()` is used when transformation is required.
    

#### 💡 **Answer**

Use `map()` when you need to **return a new array** based on transformations.  
Use `forEach()` when you just want to **execute side effects** (e.g., logging, updating external variables).

---

### **2️⃣ Is `map()` faster than `forEach()`?**

#### ✅ **How to Answer in an Interview**

- Mention performance differences.
    

#### 💡 **Answer**

Performance is nearly identical in modern engines. The difference is semantic, not speed.

---

### **3️⃣ Can you break out of `map()` or `forEach()` early?**

#### ✅ **How to Answer in an Interview**

- Clarify behaviour.
    

#### 💡 **Answer**

No, you **cannot use `break` or `return` to stop iteration**. For early exit, use a regular `for` loop or `some()`/`every()`.

---

### **4️⃣ What if you return a value inside `forEach()`?**

#### ✅ **How to Answer in an Interview**

- Explain return behaviour.
    

#### 💡 **Answer**

Returning a value inside `forEach()` has **no effect**, since it always returns `undefined`.

---

## 🎯 **Interview Tips**

✅ Always **highlight that `map()` returns a new array, `forEach()` does not**.  
✅ Mention **side-effect vs transformation** use cases.  
✅ Show that you understand **why they cannot be used interchangeably**.

# **4️⃣ What is the difference between `map()` and `filter()`?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **both return a new array**, but their purpose differs.
    
- `map()` **transforms every element**, while `filter()` **returns only elements that satisfy a condition**.
    
- Provide a **clear example showing both methods side by side**.
    

---

## 💡 **Answer**

- **`map()`** → Transforms each element and returns a **new array of the same length**.
    
- **`filter()`** → Returns a **new array with only the elements that pass a condition**.
    

---

## 🧩 **Example**

```js
const numbers = [1, 2, 3, 4, 5];

// map() - Square each number
const squares = numbers.map(n => n * n); 
console.log(squares); // [1, 4, 9, 16, 25]

// filter() - Keep only even numbers
const evens = numbers.filter(n => n % 2 === 0); 
console.log(evens); // [2, 4]
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Can `map()` be used to filter elements?**

#### ✅ **How to Answer in an Interview**

- Explain why it's not ideal.
    

#### 💡 **Answer**

Yes, but it's not recommended. You can return `null` or `undefined` for unwanted elements, but **filter() is the correct method** for filtering.

---

### **2️⃣ Does `filter()` change the original array?**

#### ✅ **How to Answer in an Interview**

- Explain immutability.
    

#### 💡 **Answer**

No. Both `map()` and `filter()` return **new arrays**, leaving the original array unchanged.

---

### **3️⃣ What happens if `filter()` condition always returns false?**

#### ✅ **How to Answer in an Interview**

- Explain edge case.
    

#### 💡 **Answer**

It returns an **empty array**.

---

### **4️⃣ Can you chain `filter()` and `map()`?**

#### ✅ **How to Answer in an Interview**

- Show practical chaining.
    

#### 💡 **Answer**

Yes, chaining is very common:

```js
const result = numbers.filter(n => n % 2 === 0).map(n => n * 2);
console.log(result); // [4, 8]
```

---

## 🎯 **Interview Tips**

✅ Always **highlight transformation vs filtering**.  
✅ Show that both return **new arrays** (immutability).  
✅ Mention **chaining as a common pattern**.

# **5️⃣ What is the difference between `find()` and `findIndex()`?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that both methods **search for the first element that satisfies a condition**.
    
- The difference is **what they return** – `find()` returns the **element**, while `findIndex()` returns the **index**.
    

---

## 💡 **Answer**

- **`find()`** → Returns the **first element** in the array that matches the condition.
    
- **`findIndex()`** → Returns the **index of the first matching element**. If not found, returns `-1`.
    

---

## 🧩 **Example**

```js
const numbers = [10, 20, 30, 40];

const foundValue = numbers.find(n => n > 25);
console.log(foundValue); // 30

const foundIndex = numbers.findIndex(n => n > 25);
console.log(foundIndex); // 2
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What if no element matches the condition?**

#### ✅ **How to Answer in an Interview**

- Explain behaviour for both methods.
    

#### 💡 **Answer**

- `find()` → Returns `undefined`.
    
- `findIndex()` → Returns `-1`.
    

---

### **2️⃣ Are `find()` and `filter()` the same?**

#### ✅ **How to Answer in an Interview**

- Clarify the difference.
    

#### 💡 **Answer**

No.

- `find()` → Returns **only the first match**.
    
- `filter()` → Returns **all matching elements in an array**.
    

---

### **3️⃣ Can you chain `find()` or `findIndex()` with other methods?**

#### ✅ **How to Answer in an Interview**

- Explain chaining.
    

#### 💡 **Answer**

Yes, but they **return a value or index**, not an array. If you need further transformations, apply them on the array first.

---

### **4️⃣ Is `find()` faster than `filter()`?**

#### ✅ **How to Answer in an Interview**

- Explain short-circuit behaviour.
    

#### 💡 **Answer**

Yes, `find()` stops **as soon as it finds the first match**, while `filter()` checks the entire array.

---

## 🎯 **Interview Tips**

✅ Always highlight **element vs index return value**.  
✅ Mention **short-circuiting for performance**.  
✅ Provide a **side-by-side example** for better clarity.

# **6️⃣ What is the difference between `slice()` and `splice()`?**

---

## ✅ **How to Answer in an Interview**

- Start by saying both are used to work with arrays but have **very different purposes**.
    
- Emphasize that `slice()` is **non-mutating**, while `splice()` **modifies the original array**.
    
- Provide a **comparison table** for clarity.
    

---

## 💡 **Answer**

|Feature|`slice()`|`splice()`|
|---|---|---|
|**Purpose**|Extracts a portion of an array|Adds/removes elements from an array|
|**Mutates Array?**|❌ No (returns a new array)|✅ Yes (modifies the original array)|
|**Return Value**|Extracted elements|Removed elements (if any)|

---

## 🧩 **Example**

```js
const numbers = [1, 2, 3, 4, 5];

// slice(start, end)
const sliced = numbers.slice(1, 4); 
console.log(sliced); // [2, 3, 4]
console.log(numbers); // [1, 2, 3, 4, 5] (unchanged)

// splice(start, deleteCount, ...items)
const spliced = numbers.splice(1, 2, 9, 10); 
console.log(spliced); // [2, 3] (removed elements)
console.log(numbers); // [1, 9, 10, 4, 5] (modified)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Can `splice()` be used to insert elements?**

#### ✅ **How to Answer in an Interview**

- Explain usage.
    

#### 💡 **Answer**

Yes. You can insert without removing any elements:

```js
const arr = [1, 2, 3];
arr.splice(1, 0, 10); 
console.log(arr); // [1, 10, 2, 3]
```

---

### **2️⃣ When should you use `slice()`?**

#### ✅ **How to Answer in an Interview**

- Explain immutability.
    

#### 💡 **Answer**

Use `slice()` when you want to **copy part of an array without modifying the original**.

---

### **3️⃣ How do you copy an entire array using `slice()`?**

#### ✅ **How to Answer in an Interview**

- Mention the trick.
    

#### 💡 **Answer**

```js
const copy = arr.slice();
```

---

### **4️⃣ Does `splice()` return a new array?**

#### ✅ **How to Answer in an Interview**

- Explain return value.
    

#### 💡 **Answer**

Yes, but the returned array **only contains the removed elements**. The original array is modified.

---

## 🎯 **Interview Tips**

✅ Emphasize **mutating vs non-mutating behaviour**.  
✅ Always provide a **side-by-side example**.  
✅ Mention **insert, delete, and replace capabilities of `splice()`**.

# **7️⃣ What are object methods like `Object.keys()`, `Object.values()`, and `Object.entries()`?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that these methods are **used to extract properties and values from objects**.
    
- Provide a short description of each method.
    
- Give **examples with a single object**.
    

---

## 💡 **Answer**

JavaScript provides several built-in methods to work with object properties:

|Method|Description|Return Type|
|---|---|---|
|**`Object.keys(obj)`**|Returns an array of **keys** of the object|`Array` of strings|
|**`Object.values(obj)`**|Returns an array of **values** of the object|`Array` of values|
|**`Object.entries(obj)`**|Returns an array of **[key, value] pairs**|`Array` of arrays|

---

## 🧩 **Example**

```js
const user = { name: "Alice", age: 25, role: "Admin" };

console.log(Object.keys(user));   
// ["name", "age", "role"]

console.log(Object.values(user)); 
// ["Alice", 25, "Admin"]

console.log(Object.entries(user)); 
// [["name", "Alice"], ["age", 25], ["role", "Admin"]]
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How can you loop through both keys and values?**

#### ✅ **How to Answer in an Interview**

- Show `Object.entries()` with `for...of`.
    

#### 💡 **Answer**

```js
for (const [key, value] of Object.entries(user)) {
  console.log(`${key}: ${value}`);
}
```

---

### **2️⃣ What happens if you use these methods on an array?**

#### ✅ **How to Answer in an Interview**

- Explain behaviour on arrays.
    

#### 💡 **Answer**

Arrays are objects with numeric keys, so:

```js
const arr = ["a", "b"];
console.log(Object.keys(arr));   // ["0", "1"]
console.log(Object.values(arr)); // ["a", "b"]
```

---

### **3️⃣ Are inherited properties included?**

#### ✅ **How to Answer in an Interview**

- Mention own properties only.
    

#### 💡 **Answer**

No. These methods **only return the object's own enumerable properties**, not those from the prototype chain.

---

### **4️⃣ How can you convert an object to a Map?**

#### ✅ **How to Answer in an Interview**

- Use `Object.entries()` with `new Map()`.
    

#### 💡 **Answer**

```js
const map = new Map(Object.entries(user));
console.log(map.get("name")); // "Alice"
```

---

## 🎯 **Interview Tips**

✅ Always list **all three methods with short examples**.  
✅ Mention that these methods **ignore non-enumerable and inherited properties**.  
✅ Bonus points if you show **how they can be combined with loops**.

# **9️⃣ What is the difference between shallow copy and deep copy?**

---

## ✅ **How to Answer in an Interview**

- Start by defining both terms.
    
- Explain that **shallow copy** only copies the first level, while **deep copy** copies nested objects as well.
    
- Provide **examples** using spread operator, `Object.assign()`, and JSON methods.
    

---

## 💡 **Answer**

- **Shallow Copy** → Copies only the **first-level properties**. If the object contains nested objects, they are **still referenced**.
    
- **Deep Copy** → Creates a **complete copy**, including nested objects, so changes in the copy **don’t affect the original**.
    

---

## 🧩 **Example**

```js
const obj = { name: "Alice", address: { city: "NY" } };

// Shallow Copy
const shallow = { ...obj };
shallow.address.city = "LA";
console.log(obj.address.city); // "LA" (original affected)

// Deep Copy
const deep = JSON.parse(JSON.stringify(obj));
deep.address.city = "Chicago";
console.log(obj.address.city); // "LA" (original unaffected)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How can you create a shallow copy of an object?**

#### ✅ **How to Answer in an Interview**

- Mention multiple methods.
    

#### 💡 **Answer**

- Using **spread operator**:
    
    ```js
    const copy = { ...obj };
    ```
    
- Using **Object.assign()**:
    
    ```js
    const copy = Object.assign({}, obj);
    ```
    

---

### **2️⃣ How can you create a deep copy in JavaScript?**

#### ✅ **How to Answer in an Interview**

- Mention JSON and libraries.
    

#### 💡 **Answer**

- Using JSON methods (works for simple objects):
    
    ```js
    const deep = JSON.parse(JSON.stringify(obj));
    ```
    
- Using structuredClone (new method):
    
    ```js
    const deep = structuredClone(obj);
    ```
    
- Using libraries like **Lodash (`_.cloneDeep()`)** for complex objects.
    

---

### **3️⃣ Why is deep copy more expensive than shallow copy?**

#### ✅ **How to Answer in an Interview**

- Explain recursion.
    

#### 💡 **Answer**

Deep copy requires recursively copying every nested object, which **takes more memory and processing time**.

---

### **4️⃣ What are the pitfalls of JSON deep copy?**

#### ✅ **How to Answer in an Interview**

- Mention limitations.
    

#### 💡 **Answer**

JSON deep copy **does not work with**:

- Functions
    
- `undefined`
    
- Circular references
    
- `Date`, `Map`, `Set`, etc.
    

---

## 🎯 **Interview Tips**

✅ Always **demonstrate nested object issue with shallow copy**.  
✅ Mention **structuredClone()** (modern method) for extra points.  
✅ Highlight **real-world scenarios** where deep copy is necessary.

---

Moving to **Question 10** 👇

---

# **🔟 What is destructuring in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that destructuring is a **syntax for extracting values from arrays or objects**.
    
- Mention that it **reduces boilerplate code** and makes assignments **cleaner and more readable**.
    
- Provide **examples for both arrays and objects**.
    

---

## 💡 **Answer**

Destructuring is a syntax introduced in ES6 that allows you to **unpack values from arrays or objects into individual variables**.

---

## 🧩 **Example – Object Destructuring**

```js
const user = { name: "Alice", age: 25 };

// Without destructuring
const name1 = user.name;
const age1 = user.age;

// With destructuring
const { name, age } = user;
console.log(name, age); // Alice 25
```

---

## 🧩 **Example – Array Destructuring**

```js
const colors = ["red", "green", "blue"];

// Without destructuring
const first = colors[0];
const second = colors[1];

// With destructuring
const [firstColor, secondColor] = colors;
console.log(firstColor, secondColor); // red green
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Can you set default values in destructuring?**

#### ✅ **How to Answer in an Interview**

- Show syntax with defaults.
    

#### 💡 **Answer**

Yes, you can set default values:

```js
const { name = "Guest", age = 18 } = {};
console.log(name, age); // Guest 18
```

---

### **2️⃣ Can you rename variables while destructuring?**

#### ✅ **How to Answer in an Interview**

- Show renaming syntax.
    

#### 💡 **Answer**

Yes:

```js
const { name: userName } = user;
console.log(userName); // Alice
```

---

### **3️⃣ How can you swap variables using array destructuring?**

#### ✅ **How to Answer in an Interview**

- Show simple trick.
    

#### 💡 **Answer**

```js
let a = 1, b = 2;
[a, b] = [b, a];
console.log(a, b); // 2 1
```

---

### **4️⃣ Can you destructure nested objects?**

#### ✅ **How to Answer in an Interview**

- Show nested syntax.
    

#### 💡 **Answer**

```js
const user = { name: "Alice", address: { city: "NY" } };
const { address: { city } } = user;
console.log(city); // NY
```

---

## 🎯 **Interview Tips**

✅ Show **both object and array destructuring**.  
✅ Mention **default values, renaming, and swapping** for extra points.  
✅ Give a **nested destructuring example** (commonly asked in interviews).

# **1️⃣1️⃣ How do you clone an object or array in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **cloning can be shallow or deep**.
    
- Show **multiple ways** to clone objects and arrays.
    
- Mention modern methods like **structuredClone()**.
    

---

## 💡 **Answer**

### 🔹 **Shallow Clone (First-Level Only)**

✅ **For Objects:**

```js
const obj = { name: "Alice" };

// Spread operator
const copy1 = { ...obj };

// Object.assign()
const copy2 = Object.assign({}, obj);
```

✅ **For Arrays:**

```js
const arr = [1, 2, 3];

// Spread operator
const copy1 = [...arr];

// slice()
const copy2 = arr.slice();

// Array.from()
const copy3 = Array.from(arr);
```

---

### 🔹 **Deep Clone (Nested Objects Too)**

✅ **Using JSON Methods:**

```js
const deepCopy = JSON.parse(JSON.stringify(obj));
```

✅ **Using structuredClone (Modern):**

```js
const deepCopy = structuredClone(obj);
```

✅ **Using Lodash (`_.cloneDeep()`):**

```js
const deepCopy = _.cloneDeep(obj);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between shallow copy and deep copy here?**

#### ✅ **How to Answer in an Interview**

- Mention nested object behaviour.
    

#### 💡 **Answer**

Shallow copy only duplicates the first level.  
Nested objects are still **shared references**.

```js
const obj = { nested: { city: "NY" } };
const shallow = { ...obj };

shallow.nested.city = "LA";
console.log(obj.nested.city); // "LA" (affected)
```

---

### **2️⃣ When should you avoid JSON-based deep copy?**

#### ✅ **How to Answer in an Interview**

- Mention limitations.
    

#### 💡 **Answer**

Avoid it when the object contains:

- Functions
    
- `undefined`
    
- Circular references
    
- `Date`, `Map`, `Set` (they won’t copy correctly)
    

---

### **3️⃣ What is the safest way to deep clone complex objects?**

#### ✅ **How to Answer in an Interview**

- Mention structuredClone or libraries.
    

#### 💡 **Answer**

Use **structuredClone()** (modern JS) or **Lodash’s `cloneDeep()`**, as they handle most data types correctly.

---

### **4️⃣ Are arrays also cloned with `structuredClone()`?**

#### ✅ **How to Answer in an Interview**

- Explain compatibility.
    

#### 💡 **Answer**

Yes, `structuredClone()` can deep copy arrays, objects, maps, sets, and more.

---

## 🎯 **Interview Tips**

✅ Always show **multiple methods** (spread, assign, slice).  
✅ Mention **shallow vs deep cloning**.  
✅ For bonus points, mention **structuredClone()** and **Lodash cloneDeep()**.

# **1️⃣2️⃣ What is a prototype in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that JavaScript uses **prototypal inheritance**, not classical inheritance.
    
- Define prototype as the **object from which other objects inherit properties and methods**.
    
- Mention the **prototype chain**.
    

---

## 💡 **Answer**

A **prototype** is an object that is **automatically associated with every JavaScript function and object**.

- Objects in JavaScript can **inherit properties and methods** from their prototype.
    
- This forms the **prototype chain**, enabling **inheritance and method sharing**.
    

---

## 🧩 **Example**

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log(`Hello, I'm ${this.name}`);
};

const alice = new Person("Alice");
alice.greet(); // "Hello, I'm Alice"
```

Here, `greet()` is defined on `Person.prototype`, and all instances of `Person` **inherit** it.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How does the prototype chain work?**

#### ✅ **How to Answer in an Interview**

- Explain lookup process.
    

#### 💡 **Answer**

When you access a property on an object:

1. JavaScript first checks the object itself.
    
2. If not found, it checks the object’s prototype.
    
3. This continues up the **prototype chain** until it reaches `Object.prototype`.
    

---

### **2️⃣ What is the difference between `__proto__` and `prototype`?**

#### ✅ **How to Answer in an Interview**

- Clarify confusion between the two.
    

#### 💡 **Answer**

- `prototype` → A property of **constructor functions** (used when creating objects).
    
- `__proto__` → A property of **instances**, pointing to the prototype of its constructor.
    

---

### **3️⃣ What happens if a property is not found in the prototype chain?**

#### ✅ **How to Answer in an Interview**

- Mention final fallback.
    

#### 💡 **Answer**

If not found in the entire prototype chain, JavaScript returns **`undefined`**.

---

### **4️⃣ Can you change an object’s prototype after creation?**

#### ✅ **How to Answer in an Interview**

- Mention `Object.setPrototypeOf()`.
    

#### 💡 **Answer**

Yes, but it’s **not recommended for performance reasons**:

```js
const obj1 = {};
const obj2 = { greet() { console.log("Hi"); } };

Object.setPrototypeOf(obj1, obj2);
obj1.greet(); // "Hi"
```

---

## 🎯 **Interview Tips**

✅ Always mention **prototypal inheritance vs classical inheritance**.  
✅ Explain **prototype chain lookup process**.  
✅ Include **example with constructor + prototype method**.

---
