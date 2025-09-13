## **📌 TypeScript – Core Concepts & Basics**

⭐ 1. **What is the difference between JavaScript and TypeScript?**  
⭐ 2. **What are the benefits and trade-offs of using TypeScript over JavaScript?**  
⭐ 3. **What are the main/basic data types in TypeScript?**  
⭐ 4. **What is `undefined` in TypeScript?**  
5. **What is the `null` type in TypeScript?**  
6. **What is the `any` type in TypeScript?**  
7. **What is the `void` type in TypeScript?**  
8. **What is the `never` type in TypeScript?**  
⭐ 9. **What are advanced types in TypeScript?**  
9. **How does TypeScript handle arrays?**  
10. **What are the three ways to declare variables in TypeScript?**  
11. **What is type inference in TypeScript?**

---

## **📌 Interfaces, Classes & Object Handling**

⭐ 13. **What is the purpose of using interfaces in TypeScript?**  
14. **What are interfaces in TypeScript?**  
⭐ 15. **What is the difference between classes and interfaces in TypeScript?**  
⭐ 16. **What is the difference between `interface` and `type` in TypeScript?**  
15. **Can TypeScript objects have optional properties?**  
16. **What is the `readonly` property in TypeScript?**  
17. **What is a type alias in TypeScript?**

---

## **📌 Enums, Generics & Utility Types**

⭐ 20. **What is an `enum` in TypeScript?**  
⭐ 21. **How many data types can be assigned to enums?**  
⭐ 22. **What is a Generic in TypeScript?**  
⭐ 23. **Are you aware of any utility types in TypeScript?**

---

## **📌 Union, Intersection & Operators**

⭐ 24. **What is union typing in TypeScript?**  
⭐ 25. **What is the difference between Union and Intersection types?**  
⭐ 26. **Which symbols are used to define Union and Intersection types?** (`|` and `&`)  
27. **What is the `in` operator in TypeScript?**  
28. **What is the `typeof` operator in TypeScript?**

---

## **📌 Project Setup & Compilation**

⭐ 29. **Do you have experience configuring a TypeScript project using `tsconfig.json`?**  
30. **What is the use of `tsconfig.json`?**  
31. **How do you compile TypeScript into JavaScript?**  
32. **Is TypeScript a strictly statically typed language?**

---

## **📌 Modules, OOP & Advanced Features**

33. **What are modules in TypeScript?**
    
34. **How does TypeScript support Object-Oriented Programming (OOP)?**
    
35. **What are decorators in TypeScript?**
    
36. **What are mixins in TypeScript?**
    

---

## **📌 Practical Usage**

⭐ 37. **Have you used TypeScript with popular frontend frameworks like React?**  
38. **What are the advantages and scenarios of using TypeScript in large projects?**


--------------------------------------------------------------------------
# ⭐ 1. **What is the difference between JavaScript and TypeScript?**

---
### 🔹 **🔸 What to say in the interview:**

> "JavaScript is a dynamic, loosely typed scripting language used to build web applications. TypeScript is a superset of JavaScript that adds optional static typing, interfaces, and other features. It helps catch bugs during development before the code runs. TypeScript code must be compiled to JavaScript, which is the language browsers understand."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- **JavaScript**: Flexible, doesn't require variable types, but that also means more room for hidden bugs.
    
- **TypeScript**: Adds rules (types) to your code. This helps catch mistakes **while writing** code rather than when users encounter errors in production.
    
- TypeScript eventually becomes JavaScript after compilation.
    

✅ Think of it as:  
**TypeScript = JavaScript + Safety Net**

---

### 🔹 **🔸 Real-world analogy:**

Imagine JavaScript is building a house without blueprints — you can do it, but you might only find structural issues once you move in.

TypeScript is like building with clear blueprints and engineering checks — you catch errors during construction, not after the house collapses.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can I run TypeScript directly in the browser?**

#### ✅ What to say:

> "No, browsers only understand JavaScript. TypeScript must be compiled into JavaScript using a compiler like `tsc` before it runs."

#### 🧠 Explanation:

The browser is like a waiter who only understands orders in English (JavaScript). If you speak in French (TypeScript), you’ll need a translator (the TypeScript compiler) first.

---

### ❓ Q2: **If TypeScript compiles to JavaScript, does it affect performance?**

#### ✅ What to say:

> "No, TypeScript doesn't affect runtime performance. It only helps during development. After compilation, it’s just JavaScript — so the performance is the same."

#### 🧠 Explanation:

TypeScript is like using Grammarly while writing — it won’t slow down the final document but helps improve it while you're drafting.

---

### ❓ Q3: **Can you add TypeScript to an existing JavaScript project gradually?**

#### ✅ What to say:

> "Yes, that’s one of TypeScript’s biggest strengths. You can rename `.js` files to `.ts`, and start adding types gradually. You don’t need to refactor the whole codebase at once."

#### 🧠 Explanation:

It’s like switching to a healthy diet one meal at a time — no need to go 100% clean overnight. TypeScript lets you adopt it bit by bit without breaking your existing setup.

---

# ⭐ 2. **What are the benefits and trade-offs of using TypeScript over JavaScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "The main benefit of TypeScript is static type checking, which helps catch bugs early during development. It improves code readability, refactoring, and documentation. TypeScript is especially helpful in large projects and teams.
> 
> The trade-offs are that it requires a build step, has a learning curve, and may slightly slow down development in the short term — but these are outweighed by the long-term benefits of safety and maintainability."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

**Benefits**:

- **Catches bugs early** → You know about the mistake _before_ running the code.
    
- **Code autocomplete & better IntelliSense** → Especially useful in VS Code.
    
- **Great for teams** → Everyone knows what kind of data is expected and returned.
    
- **Easier to refactor** → Changing a function’s structure shows all impacted areas.
    

**Trade-offs**:

- **You have to compile** `.ts` → `.js`.
    
- **Learning curve** → You need to learn types, interfaces, etc.
    
- **Slightly longer dev time initially** → Because you write more explicit code.
    

---

### 🔹 **🔸 Real-world analogy:**

- **TypeScript is like having spell check, grammar check, and a style guide while writing an essay.**
    
    - It takes a little longer while writing.
        
    - But the result is cleaner, error-free, and easier for others to read and edit.
        

Whereas **JavaScript** is like writing a freeform note with no tools — fast, but easy to mess up and hard to clean later.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Is TypeScript worth it for small projects?**

#### ✅ What to say:

> "For very small projects, JavaScript might be sufficient. But even in small codebases, TypeScript can provide helpful autocomplete and safety. The real value becomes clear as the project scales or gets handed to other developers."

#### 🧠 Explanation:

Imagine writing 50 lines of JS — manageable. Now imagine growing that into 5,000+ lines — that's where mistakes start slipping in. TypeScript prevents this snowballing.

**Frontend analogy**:  
Even a small form component can break if you pass in the wrong prop. TypeScript can warn you before it happens.

---

### ❓ Q2: **What if my whole team is fast with JavaScript — won’t TypeScript slow us down?**

#### ✅ What to say:

> "Initially, there’s a small learning curve and slight slowdown. But once the team adapts, the time saved in debugging and maintenance often outweighs the setup cost."

#### 🧠 Explanation:

It’s like learning touch typing. You’re slower at first, but eventually, you're much faster and more accurate — and spend less time fixing typos.

---

### ❓ Q3: **Can you use JavaScript and TypeScript together?**

#### ✅ What to say:

> "Yes, TypeScript allows mixing `.js` and `.ts` files. You can gradually migrate a JavaScript project to TypeScript step-by-step."

#### 🧠 Explanation:

TypeScript is very flexible — it lets you move file by file, so you’re not forced to rewrite everything in one go.

---
# ⭐ 3. **What are the main/basic data types in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript supports basic data types similar to JavaScript, but with type annotations. The main primitive types are: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, and `bigint`.  
> Additionally, it supports `any`, `unknown`, `void`, `never`, arrays, tuples, and custom object types."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Think of types as **labels** you give to your variables so TypeScript can warn you if something doesn’t match.

|Type|What it means|Example|
|---|---|---|
|`string`|A series of characters|`"Hello World"`|
|`number`|All numbers (integers, floats, etc.)|`42`, `3.14`|
|`boolean`|True or false|`true`, `false`|
|`null`|An intentional absence of value|`let x: null = null`|
|`undefined`|A variable that hasn’t been assigned|`let y: undefined = undefined`|
|`any`|Opts out of type checking|`let x: any = "anything"`|
|`unknown`|Like `any`, but safer (must check type before using)||
|`void`|Function returns nothing|`function log(): void {}`|
|`never`|Function never returns|`throw new Error()`|
|`object`|Anything not a primitive|`{ name: "Aman" }`|
|`Array`|List of items|`number[]`, `string[]`|
|`Tuple`|Fixed-length array with known types|`[string, number]`|

---

### 🔹 **🔸 Real-world analogy:**

Imagine you're designing a form in React:

- You want `email` to be a `string`.
    
- You want `age` to be a `number`.
    
- You want `isSubscribed` to be a `boolean`.
    

If someone tries to send `"twenty"` for age — TypeScript catches that _before_ it breaks your UI or API.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between `any` and `unknown`?**

#### ✅ What to say:

> "`any` disables all type checking — it's like opting out of TypeScript. `unknown` is similar but safer because TypeScript forces you to check its type before using it."

#### 🧠 Explanation:

- `any`: TypeScript shrugs and says, "Do what you want."
    
- `unknown`: TypeScript says, "Hold on. First, prove this is safe."
    

✅ Prefer `unknown` over `any` when working with values of uncertain type — e.g., parsing API data.

---

### ❓ Q2: **When would you use `void` and `never`?**

#### ✅ What to say:

> "`void` is used for functions that don’t return anything, like logging. `never` is for functions that never return — like infinite loops or functions that always throw an error."

#### 🧠 Explanation:

- `void`: Function completes but doesn’t return anything.
    
- `never`: Function _doesn’t complete_ — it crashes or runs forever.
    

```ts
function log(): void {
  console.log("Done");
}

function crash(): never {
  throw new Error("Crashed");
}
```

---

### ❓ Q3: **How do you type an array or a tuple in TypeScript?**

#### ✅ What to say:

> "For arrays, you use `type[]` like `string[]` or `number[]`. For tuples, you define the exact types and order, like `[string, number]`."

#### 🧠 Explanation:

- Array: All elements of the same type — like `["a", "b", "c"]`.
    
- Tuple: Different types in a fixed order — like `["John", 28]`.
    

Useful when returning multiple values from a function.

---
# ⭐ 4. **What is `undefined` in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`undefined` in TypeScript means a variable has been declared but hasn't been assigned a value yet. It is a built-in primitive type and can be explicitly used in type annotations. TypeScript also uses it to represent optional properties or uninitialized variables."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- `undefined` is a value that means: **“This exists, but hasn’t been given anything yet.”**
    
- It’s the default value for variables declared but not initialized.
    

```ts
let x: number;
console.log(x); // undefined
```

You can also use it in type annotations:

```ts
let status: string | undefined;
```

This means the variable can either be a string **or** not have a value yet.

---

### 🔹 **🔸 Real-world analogy:**

Think of `undefined` like a form field that was created but the user hasn’t filled in yet.

- The field exists (`let name`)
    
- But it’s empty (`name = undefined`)
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Is `undefined` the same as `null`?**

#### ✅ What to say:

> "No, they are different. `undefined` means a variable was declared but hasn't been assigned. `null` is an explicit assignment to mean 'no value'."

#### 🧠 Explanation:

- `undefined` = TypeScript didn’t assign anything yet
    
- `null` = You _intentionally_ said “there’s nothing here”
    

```ts
let x;         // x is undefined
let y = null;  // y is intentionally empty
```

---

### ❓ Q2: **When should I use `undefined` in type annotations?**

#### ✅ What to say:

> "When a value is optional or may not be set immediately — such as before a fetch call finishes or a user fills in a form — I’d include `undefined` in the type."

#### 🧠 Example:

```ts
let userEmail: string | undefined;
```

You might later check:

```ts
if (userEmail !== undefined) {
  sendEmail(userEmail);
}
```

This protects your app from crashing if the value’s not ready yet.

---

### ❓ Q3: **How does TypeScript handle uninitialized variables?**

#### ✅ What to say:

> "If a variable is declared but not initialized, TypeScript assumes it might be `undefined`. It will warn you if you try to use it before assigning."

#### 🧠 Explanation:

This avoids bugs like trying to `.trim()` an undefined string.

```ts
let message: string;
console.log(message.length); // ❌ TypeScript error
```

To fix:

```ts
let message: string = "Hello";
```

Or allow undefined:

```ts
let message: string | undefined;
```

---
#  5. **What is the `null` type in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`null` is a primitive type in TypeScript that represents an explicit absence of value. Unlike `undefined`, which indicates that a variable hasn't been assigned yet, `null` is intentionally assigned to indicate 'no value' or 'empty'. You can use it in union types like `string | null` when a value might be empty on purpose."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- `null` means: **“I’m deliberately saying this variable has no value.”**
    
- You assign it intentionally, often to reset a variable or placeholder.
    

```ts
let profilePicture: string | null = null;
```

Later in your code, once the image loads, you assign:

```ts
profilePicture = "https://image.url";
```

---

### 🔹 **🔸 Real-world analogy:**

`null` is like a reserved seat in a theatre. You’re saying,  
**“No one’s sitting here right now, but I might fill it later.”**

In contrast, `undefined` is like a seat that doesn’t even exist on the plan yet.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How is `null` different from `undefined` in TypeScript?**

#### ✅ What to say:

> "`undefined` usually means a variable hasn't been initialized yet, whereas `null` is a deliberate assignment to indicate an empty or missing value. TypeScript treats them as distinct types."

#### 🧠 Explanation:

- `undefined` is more accidental — no value has been set.
    
- `null` is intentional — you **set** the value to mean "nothing here."
    

```ts
let x: string | undefined; // not set yet
let y: string | null;      // purposely empty
```

---

### ❓ Q2: **Do I need to explicitly include `null` in type annotations?**

#### ✅ What to say:

> "Yes. In strict mode, TypeScript doesn't allow `null` unless you explicitly declare it in a union type — like `string | null`. Otherwise, assigning `null` will cause a type error."

#### 🧠 Example:

```ts
let message: string = null; // ❌ Error in strict mode
let message: string | null = null; // ✅ Allowed
```

---

### ❓ Q3: **When should I use `null` in frontend development?**

#### ✅ What to say:

> "I’d use `null` when a value is expected to be missing initially but could be populated later — like a selected item, API result, or image URL."

#### 🧠 Example:

```ts
let selectedUser: User | null = null;
```

- Before the user selects anything: `null`
    
- After selection: assign the `User` object
    

---
#  6. **What is the `any` type in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`any` is a special type in TypeScript that disables type checking. It tells the compiler to skip type safety for that variable, which makes it behave like plain JavaScript. While it offers flexibility, overusing `any` defeats the purpose of TypeScript and should be avoided when possible."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- `any` = **“Let me do whatever I want.”**
    
- The compiler won’t check for correctness — it assumes **you** know what you're doing.
    
- TypeScript gives up control.
    

```ts
let data: any = "Hello";
data = 42;
data = { name: "Aman" }; // All allowed
```

⚠️ It’s useful when:

- You’re migrating from JavaScript
    
- You genuinely don’t know the type yet (e.g. dynamic JSON)
    

---

### 🔹 **🔸 Real-world analogy:**

Using `any` is like disabling your car’s **seatbelt alarm**.  
It lets you drive however you want, but now you’ve removed the safety features.

It’s fine once in a while, but dangerous if used all the time — especially at scale.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When should I use `any`?**

#### ✅ What to say:

> "I’d use `any` temporarily — during early development or while integrating third-party libraries where types aren’t available. It’s also helpful when gradually migrating JavaScript code to TypeScript."

#### 🧠 Explanation:

Let’s say you’re fetching data from an old API and don’t have the structure yet. You can use `any` _until_ you define an interface later.

```ts
let result: any;
```

Later:

```ts
interface User {
  name: string;
  age: number;
}
let result: User;
```

---

### ❓ Q2: **What are the risks of using `any`?**

#### ✅ What to say:

> "It removes TypeScript’s ability to catch bugs. You might accidentally call methods or access properties that don’t exist, leading to runtime errors — the very thing TypeScript is meant to prevent."

#### 🧠 Example:

```ts
let user: any = "Shrey";
user.toUpperCase();       // OK
user.push("new value");   // Also OK — but will crash at runtime!
```

Because TypeScript isn’t checking anymore — you’re back to JS-style bugs.

---

### ❓ Q3: **What can I use instead of `any` for safer flexibility?**

#### ✅ What to say:

> "I can use `unknown`, which still requires type-checking before using the value. Or I can define a custom type or interface, even partially, to retain some type safety."

#### 🧠 Example:

```ts
let input: unknown = getData();

if (typeof input === "string") {
  console.log(input.toUpperCase());
}
```

✅ `unknown` is like `any`, but with a seatbelt.

---
#  7. **What is the `void` type in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`void` is a TypeScript type that represents the absence of a return value from a function. It’s typically used to annotate functions that perform an action but don’t return anything, like logging or triggering a side effect."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

When you define a function that doesn’t give you anything back — it just _does something_ — you use `void` as the return type.

```ts
function logMessage(msg: string): void {
  console.log(msg);
}
```

- This function returns **nothing**.
    
- `void` tells TypeScript: “Don’t expect a return value here.”
    

---

### 🔹 **🔸 Real-world analogy:**

Calling a `void` function is like **pressing a doorbell**.

- You _trigger_ an action (the sound).
    
- But you don’t expect the doorbell to return a value like `true` or `false`.
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can I return `null` or `undefined` from a `void` function?**

#### ✅ What to say:

> "Technically, you can return `undefined`, but it’s not required. Returning `null` is discouraged because it doesn’t match the meaning of `void`. TypeScript expects `undefined` or no return at all."

#### 🧠 Explanation:

```ts
function sayHi(): void {
  return; // ✅ OK
  // OR
  return undefined; // ✅ OK
  // BUT
  return null; // ❌ Error if strict mode is on
}
```

---

### ❓ Q2: **Where else is `void` used in TypeScript besides functions?**

#### ✅ What to say:

> "`void` can also appear in places like callback functions or event handlers, especially in frontend code. It’s a common return type for `onClick`, `setTimeout`, and similar side-effect functions."

#### 🧠 Example:

```ts
button.addEventListener("click", (): void => {
  console.log("Button clicked");
});
```

- You're not returning anything — just triggering a UI action.
    

---

### ❓ Q3: **Is `void` the same as `undefined`?**

#### ✅ What to say:

> "Not exactly. `void` is a return type, while `undefined` is a value. A function with a `void` return type may return `undefined`, but conceptually they’re different."

#### 🧠 Analogy:

- `undefined` is a missing **value**
    
- `void` is a missing **return**
    

So:

```ts
function doStuff(): void {
  return; // okay
}
```

But:

```ts
let x: void = undefined; // allowed, but rarely needed outside function return
```

---
#  8. **What is the `never` type in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`never` is a special type in TypeScript used for functions or expressions that never return. This includes functions that throw errors or enter infinite loops. It signals to the compiler that this code path is unreachable or will never complete."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Use `never` when your function is guaranteed to do one of the following:

- **Crash** (`throw new Error`)
    
- **Loop forever** (`while(true)`)
    
- **Exhaust all possible outcomes and still not return**
    

TypeScript uses `never` to catch logical errors like unhandled cases in a `switch`.

```ts
function fail(): never {
  throw new Error("Something went wrong");
}
```

---

### 🔹 **🔸 Real-world analogy:**

Imagine a trapdoor that **instantly drops you into a pit** before you do anything else. You never get to finish what you started.

That’s a `never` function — the rest of the code is unreachable.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How is `never` different from `void`?**

#### ✅ What to say:

> "`void` means the function returns nothing. `never` means the function never returns at all. With `void`, execution completes. With `never`, it crashes or runs infinitely."

#### 🧠 Example:

```ts
function log(): void {
  console.log("Hello"); // completes normally
}

function crash(): never {
  throw new Error("Boom!"); // never completes
}
```

✅ TL;DR:

- `void` = Done, but returned nothing
    
- `never` = Never even made it to "done"
    

---

### ❓ Q2: **When do we encounter `never` in real frontend projects?**

#### ✅ What to say:

> "It often shows up in error-handling functions, infinite polling loops, or when enforcing exhaustive checks in `switch` statements on types."

#### 🧠 Example: Exhaustiveness check

```ts
type ButtonType = "primary" | "secondary";

function renderButton(type: ButtonType) {
  switch (type) {
    case "primary":
      return "Blue";
    case "secondary":
      return "Gray";
    default:
      const _exhaustiveCheck: never = type; // ⛔ If new type added but not handled
      return _exhaustiveCheck;
  }
}
```

- TypeScript will now yell at you if you add `"danger"` to `ButtonType` but forget to handle it.
    

---

### ❓ Q3: **Can I assign `never` to any variable?**

#### ✅ What to say:

> "No — `never` is a bottom type. It can’t be assigned to anything except other `never` variables. But all types can technically be assigned to `never`, which is how it helps enforce unreachable code."

#### 🧠 Example:

```ts
let x: never = (() => { throw new Error("Oops") })(); // ✅ OK

let y: string = x; // ❌ Error
```

Because `never` should never occur — assigning it to a real type is not allowed.

---
# ⭐ 9. **What are advanced types in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Advanced types in TypeScript include combinations and transformations of existing types to express more complex behavior. Common advanced types include union types, intersection types, literal types, tuples, mapped types, conditional types, and utility types. These allow for highly expressive and type-safe code structures."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

These are types that go beyond the basics (string, number, boolean).  
They help describe _more flexible_ or _more strict_ data structures.

---

### ✅ Common Advanced Types (with examples):

|Type|Description|Example|
|---|---|---|
|**Union (`|`)**|Value can be one of multiple types|
|**Intersection (`&`)**|Combines multiple types into one|`type Admin = User & Permissions`|
|**Literal**|Type can only be a specific value|`type Role = "admin" \| "user"`|
|**Tuple**|Fixed-length arrays with specific types/order|`[string, number]`|
|**Enums**|Named set of constant values|`enum Status { Success, Failure }`|
|**Mapped**|Transform all properties of a type|`Partial<T>`, `Readonly<T>`|
|**Conditional**|Type based on a condition|`T extends U ? X : Y`|
|**Utility**|Built-in tools to modify types|`Partial<T>`, `Pick<T, K>`|

---

### 🔹 **🔸 Real-world analogy:**

Imagine you’re building a signup form in React:

- The user’s `id` could be a `number` from the DB or a `string` from localStorage → **Union**
    
- You combine `UserDetails` and `AddressDetails` into one object → **Intersection**
    
- A field like `userRole` can only be `"admin"`, `"editor"` or `"viewer"` → **Literal**
    
- The form returns `[name, age]` → **Tuple**
    

TypeScript lets you _enforce_ all this at compile time.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between union and intersection types?**

#### ✅ What to say:

> "Union types (`|`) mean the value can be one of several types. Intersection types (`&`) mean the value must satisfy all types at once."

#### 🧠 Example:

```ts
type A = { name: string };
type B = { age: number };

type Union = A | B;     // Must be A *or* B
type Intersection = A & B; // Must be A *and* B

const u: Union = { name: "Aman" }; // ✅
const i: Intersection = { name: "Aman", age: 25 }; // ✅
```

---

### ❓ Q2: **When would you use literal types?**

#### ✅ What to say:

> "Literal types restrict values to exact strings or numbers, which is useful for defining valid options. This improves autocomplete and avoids typos."

#### 🧠 Example:

```ts
type Theme = "dark" | "light";

function setTheme(theme: Theme) {
  // Only accepts "dark" or "light"
}
```

✅ This is very common in UI components (`variant`, `size`, `type`, etc.)

---

### ❓ Q3: **How do utility types relate to advanced types?**

#### ✅ What to say:

> "Utility types are built-in advanced types that help transform other types. For example, `Partial<T>` makes all properties optional, and `Readonly<T>` makes them immutable."

#### 🧠 Example:

```ts
interface User {
  name: string;
  age: number;
}

const draft: Partial<User> = {}; // Can omit both `name` and `age`
```

You’ll use these a lot when working with forms, APIs, or configs.

---
# 🔹 10 **How does TypeScript handle arrays?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript allows us to define the type of elements an array can contain using two syntaxes: `type[]` or `Array<type>`. This ensures type safety, meaning you can’t accidentally insert the wrong kind of data into an array."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

In JavaScript, you can throw anything into an array:

```js
let list = [1, "hello", true]; // 😬 no rules!
```

In TypeScript, you **tell it what kind of data** is allowed — and it enforces it:

```ts
let numbers: number[] = [1, 2, 3];       // ✅
numbers.push("hi");                     // ❌ Error!
```

Or:

```ts
let names: Array<string> = ["Shrey", "Aman"];
```

Both syntaxes are the same — just stylistic choice.

---

### 🔹 **🔸 Real-world analogy:**

A TypeScript array is like a **conveyor belt in a factory** labeled “only shoes.”  
If someone tries to put in a watermelon — TypeScript throws an error before the belt even starts.

---

### ✅ Tuple vs Array Summary

|Feature|Array|Tuple|
|---|---|---|
|Type|All items of same type|Fixed length with specific types|
|Example|`string[]`|`[string, number]`|
|Use case|List of names|API response: `[status, code]`|

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between `string[]` and `Array<string>`?**

#### ✅ What to say:

> "There’s no functional difference — `string[]` is shorthand for `Array<string>`. It’s just a matter of style preference."

#### 🧠 Example:

```ts
let list1: string[] = ["a", "b"];
let list2: Array<string> = ["a", "b"];
```

You’ll usually see `type[]` for primitives and `Array<Type>` when the type is complex or generic.

---

### ❓ Q2: **Can arrays be read-only in TypeScript?**

#### ✅ What to say:

> "Yes. You can mark arrays as `readonly` to prevent mutation. This is useful when you want to guarantee immutability."

#### 🧠 Example:

```ts
let readonlyNames: readonly string[] = ["John", "Jane"];
readonlyNames.push("Jack"); // ❌ Error
```

✅ Great for props in React components to avoid accidental mutation.

---

### ❓ Q3: **How do I type an array of objects?**

#### ✅ What to say:

> "You can define an array of objects by using an interface or type and applying it to the array."

#### 🧠 Example:

```ts
interface User {
  id: number;
  name: string;
}

let users: User[] = [
  { id: 1, name: "Shrey" },
  { id: 2, name: "Aman" },
];
```

✅ Ensures that every object in the array follows the `User` structure.

---
# 10. **What are the three ways to declare variables in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript follows JavaScript's three variable declaration keywords: `var`, `let`, and `const`.
> 
> - `var` is function-scoped and can lead to hoisting issues.
>     
> - `let` is block-scoped and allows reassignment.
>     
> - `const` is also block-scoped, but values can't be reassigned.
>     
> 
> TypeScript builds on this by allowing type annotations with all three."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

|Keyword|Scope|Reassignable|Use case|
|---|---|---|---|
|`var`|Function|✅ Yes|Legacy JS code, avoid in TS|
|`let`|Block|✅ Yes|For changing values|
|`const`|Block|❌ No|For fixed values (preferred in TS)|

You can also add type annotations:

```ts
let age: number = 25;
const name: string = "Shrey";
```

---

### 🔹 **🔸 Real-world analogy:**

Imagine variable declarations like **labels on storage boxes**:

- `var` = Old sticky notes that fall off if you're not careful.
    
- `let` = Reusable label — you can replace it if needed.
    
- `const` = Permanent label — write it once and you're done.
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Why is `var` considered outdated or risky in TypeScript?**

#### ✅ What to say:

> "`var` is function-scoped and hoisted, which can lead to unexpected behavior. `let` and `const` offer block scoping and are much safer in modern JavaScript and TypeScript development."

#### 🧠 Example:

```ts
function test() {
  console.log(a); // undefined, not error!
  var a = 10;
}
```

✅ Prefer `let` or `const` to avoid surprises like this.

---

### ❓ Q2: **When should I use `const` vs `let` in TypeScript?**

#### ✅ What to say:

> "Use `const` by default for variables that won’t change. Use `let` when reassignment is necessary — like counters, state updates, or loops."

#### 🧠 Example:

```ts
const maxUsers = 100; // ✅ Never changes
let currentUserCount = 0; // ✅ Increments over time
```

✅ Using `const` by default makes your code easier to reason about.

---

### ❓ Q3: **Can you add types to variables without assigning values?**

#### ✅ What to say:

> "Yes. You can declare a variable with a type and assign the value later — this is common for variables that will be updated after some async call."

#### 🧠 Example:

```ts
let response: string;
response = await fetchData(); // later assignment is okay
```

✅ This helps TypeScript catch errors _before_ a wrong value is assigned.

---
#  ⭐11. **What is type inference in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Type inference is a feature in TypeScript where the compiler automatically determines the type of a variable based on the assigned value. If you don’t explicitly annotate the type, TypeScript still understands and enforces it internally."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

TypeScript is smart.

If you do this:

```ts
let name = "Shrey";
```

TypeScript sees that it's a string and **locks it in** — now you can’t assign a number later.

```ts
name = 123; // ❌ Error
```

✅ You didn’t write `: string`, but it figured it out on its own — that’s type inference.

---

### 🔹 **🔸 Real-world analogy:**

It’s like watching someone walk into a room holding a football —  
you **infer** they’re a player without asking.

Similarly, if TypeScript sees `let isDark = true`, it infers it’s a `boolean`.

---

### ✅ Common Places Where Inference Happens:

|Scenario|Inferred Type|
|---|---|
|`let age = 21;`|`number`|
|`const tags = ["typescript", "react"];`|`string[]`|
|`function greet() { return "hi"; }`|`() => string`|
|`const isLoggedIn = true;`|`boolean`|

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Should I always rely on type inference?**

#### ✅ What to say:

> "Inference is great for simple cases, but for function arguments, return types, and object structures, I prefer explicit types — especially in shared codebases."

#### 🧠 Example:

```ts
// Bad — no clarity on input/output
function add(a, b) {
  return a + b;
}

// Good
function add(a: number, b: number): number {
  return a + b;
}
```

✅ Use inference for local values. Use annotations for clarity in reusable functions and APIs.

---

### ❓ Q2: **Does inference work with function parameters?**

#### ✅ What to say:

> "No — TypeScript can’t infer parameter types unless it’s from context, like callbacks. For standalone functions, you must specify parameter types."

#### 🧠 Example:

```ts
function square(n) {
  return n * n; // 🚨 What is 'n'? TS can’t infer
}
```

Fix:

```ts
function square(n: number): number {
  return n * n;
}
```

✅ Type safety restored.

---

### ❓ Q3: **How is type inference useful in frontend code?**

#### ✅ What to say:

> "It speeds up development by reducing the need for boilerplate type annotations. Especially in component logic, local variables, and destructured values — it keeps code clean without sacrificing safety."

#### 🧠 Example:

```ts
const [count, setCount] = useState(0); // Inferred as number
```

✅ You didn’t declare the type — but TS knows `count` is a `number` based on the default value `0`.

---
# ⭐ 13. **What is the purpose of using interfaces in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Interfaces in TypeScript define the **structure of an object** — including the properties it must have, their types, and whether they’re optional or readonly. They help ensure objects follow a consistent shape, which is especially useful for APIs, component props, and team collaboration."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

An **interface** is like a **contract** for how an object should look.

If you say:

```ts
interface User {
  name: string;
  age: number;
}
```

You’re telling TypeScript:

> “Any object that calls itself a `User` _must_ have a `name` that’s a string and an `age` that’s a number.”

✅ Example:

```ts
const u1: User = {
  name: "Shrey",
  age: 25,
}; // ✅ Fine

const u2: User = {
  name: "Shrey",
}; // ❌ Error: Missing age
```

---

### 🔹 **🔸 Real-world analogy:**

It’s like filling out a government form.

- The form template (interface) says: _"Provide full name (string), age (number), and email (string)"_
    
- If you leave one out or write your age as `"twenty"`, the system rejects it.
    

---

### ✅ Why Interfaces Matter in Frontend:

- Defining **React props**
    
- Validating **API response shapes**
    
- Creating **shared contracts** across teams
    

```ts
interface Props {
  title: string;
  isLoading: boolean;
}

function Header({ title, isLoading }: Props) {
  return <h1>{isLoading ? "Loading..." : title}</h1>;
}
```

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How is an interface different from a type alias?**

#### ✅ What to say:

> "Both can describe object shapes, but interfaces are better for object-oriented features like `extends`. Types are more flexible and can represent unions, primitives, and functions. Interfaces are generally preferred for objects and props."

#### 🧠 Example:

```ts
interface A {
  name: string;
}

type B = {
  name: string;
};
```

✅ In most use cases, they’re interchangeable for objects.

---

### ❓ Q2: **Can interfaces be extended or inherited?**

#### ✅ What to say:

> "Yes. Interfaces can extend other interfaces to build on top of existing ones. This allows reusable and modular object structures."

#### 🧠 Example:

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}

const e: Employee = {
  name: "Aman",
  employeeId: 101,
};
```

---

### ❓ Q3: **When would you choose an interface over a class?**

#### ✅ What to say:

> "Interfaces are purely structural — they describe what an object should look like. Classes provide both structure and behaviour. I'd use interfaces when I just need to enforce a shape, especially for props or APIs."

---
#  14. **What are interfaces in TypeScript?** _(Detailed Explanation)_

---

### 🔹 **🔸 What to say in the interview:**

> "Interfaces in TypeScript are used to define the shape of objects. They describe which properties and methods an object should have, along with their types. Interfaces support features like optional properties, readonly properties, method signatures, and inheritance through `extends`."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

You already know: Interfaces = **object blueprints**.

Let’s now look at what **extra power** they bring beyond just listing properties:

---

### ✅ Interface Features (with examples):

#### 🔸 1. **Basic shape**

```ts
interface User {
  name: string;
  age: number;
}
```

---

#### 🔸 2. **Optional properties**

```ts
interface User {
  name: string;
  age?: number; // optional
}
```

✅ Useful for fields that might not always exist (e.g., `bio`, `phoneNumber`).

---

#### 🔸 3. **Readonly properties**

```ts
interface User {
  readonly id: number;
  name: string;
}
```

✅ Once assigned, `id` can’t be changed — helps protect integrity (e.g., user ID, order ID).

---

#### 🔸 4. **Function types inside interfaces**

```ts
interface Button {
  label: string;
  onClick: () => void;
}
```

✅ Common for frontend props — especially React components.

---

#### 🔸 5. **Extending interfaces (inheritance)**

```ts
interface Animal {
  name: string;
}

interface Dog extends Animal {
  bark(): void;
}
```

✅ Allows reusability and clean code.

---

### 🔹 **🔸 Real-world analogy:**

If interfaces are like a **contract**, then `extends` is like saying:

> “This new contract includes everything from the old one — _plus_ a few extras.”

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can interfaces describe arrays or functions?**

#### ✅ What to say:

> "Yes. Interfaces can define function signatures and array-like structures by describing the expected shape."

#### 🧠 Examples:

```ts
// Function interface
interface Greeter {
  (name: string): string;
}

// Array-like interface
interface StringArray {
  [index: number]: string;
}

const names: StringArray = ["Shrey", "Aman"];
```

✅ This is helpful for reusable type-safe functions and structures.

---

### ❓ Q2: **Can interfaces be merged?**

#### ✅ What to say:

> "Yes, unlike type aliases, interfaces in TypeScript support declaration merging — you can define the same interface name multiple times and TypeScript will combine them."

#### 🧠 Example:

```ts
interface Box {
  width: number;
}

interface Box {
  height: number;
}

const b: Box = { width: 100, height: 200 }; // ✅ Merged
```

✅ Useful in extending types across modules or libraries.

---

### ❓ Q3: **Can interfaces be used for class contracts?**

#### ✅ What to say:

> "Yes. Interfaces are often used to enforce a structure that classes must follow using the `implements` keyword."

#### 🧠 Example:

```ts
interface Printable {
  print(): void;
}

class Invoice implements Printable {
  print() {
    console.log("Printing invoice...");
  }
}
```

✅ Ensures consistent class structures — great for OOP and component design.

---
# ⭐ 15. **What is the difference between classes and interfaces in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Interfaces define the **structure** of an object — like a contract — but contain no implementation.
> 
> Classes, on the other hand, define both **structure and behavior**. They can have constructors, methods, and actual code logic.
> 
> A class can implement an interface to guarantee it adheres to a specific shape."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

|Feature|Interface|Class|
|---|---|---|
|Structure|✅ Yes|✅ Yes|
|Logic/Behaviour|❌ No|✅ Yes (methods, constructor)|
|Instantiable?|❌ No (just a blueprint)|✅ Yes (can create objects)|
|Inheritance|`extends` (interfaces)|`extends` (classes)|
|Used for|Type-checking & contracts|Object creation + logic|

---

### 🔹 **🔸 Real-world analogy:**

- An **interface** is like a blueprint for a car: “Must have 4 wheels, an engine, and a steering wheel.”
    
- A **class** is the **actual car** built using that blueprint — with functioning parts and working buttons.
    

---

### ✅ Example:

```ts
interface Person {
  name: string;
  speak(): void;
}

class Employee implements Person {
  constructor(public name: string) {}

  speak() {
    console.log(`${this.name} says hello.`);
  }
}
```

✅ Here, `Employee` is _guaranteed_ to have everything the `Person` interface requires.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can a class extend another class and implement an interface at the same time?**

#### ✅ What to say:

> "Yes. TypeScript supports single class inheritance and multiple interface implementations. A class can extend one class and implement multiple interfaces."

#### 🧠 Example:

```ts
interface Drivable {
  drive(): void;
}

class Vehicle {
  start() {
    console.log("Starting engine...");
  }
}

class Car extends Vehicle implements Drivable {
  drive() {
    console.log("Driving car");
  }
}
```

✅ You get both inheritance and type safety.

---

### ❓ Q2: **When should I use a class vs an interface in frontend code?**

#### ✅ What to say:

> "I’d use **interfaces** to describe the shape of props, API data, or configs — basically anywhere I'm only concerned with structure.  
> I’d use **classes** when I need to encapsulate data and logic together, like in services or state models."

#### 🧠 Examples:

- `interface Props { title: string; }` → For React components
    
- `class FormHandler` → To manage complex form state and behavior
    

---

### ❓ Q3: **Can interfaces be used to type-check class instances?**

#### ✅ What to say:

> "Yes. If a class implements an interface, any instance of that class can be treated as the interface type. It’s helpful for dependency injection and enforcing consistency."

#### 🧠 Example:

```ts
interface Logger {
  log(msg: string): void;
}

class ConsoleLogger implements Logger {
  log(msg: string) {
    console.log(msg);
  }
}

function run(logger: Logger) {
  logger.log("Running app...");
}

const logger = new ConsoleLogger();
run(logger); // ✅ works because it matches interface
```

✅ This keeps your app **flexible and testable** — critical in large-scale apps.

---
# ⭐ 16. **What is the difference between `interface` and `type` in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`interface` and `type` are both used to define the shape of data in TypeScript, but they have some differences:
> 
> - `interface` is mainly used for describing the structure of objects, classes, or functions and supports **declaration merging**.
>     
> - `type` can define any type — including primitives, unions, intersections, and more — but **cannot** merge declarations.
>     
> 
> In general, use `interface` for object-like shapes and `type` when you need unions, intersections, or more flexibility."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Both `interface` and `type` let you **describe the shape** of something — like what properties it has and what their types are.  
But:

- `interface` = **object blueprints** with the ability to extend and merge
    
- `type` = **type aliases** that can represent anything (objects, primitives, unions)
    

---

### ✅ Example: Interface

```ts
interface Person {
  name: string;
  age: number;
}

interface Person {
  gender?: string; // Declaration merging allowed
}

const p: Person = { name: "Shrey", age: 30 };
```

✅ `interface` can be **merged** and extended.

---

### ✅ Example: Type

```ts
type Person = {
  name: string;
  age: number;
};

type ID = string | number; // Can represent non-object shapes

// ❌ Cannot re-declare `type Person` — no merging allowed
```

✅ `type` is more **flexible** but not mergeable.

---

### 🔹 **🔸 Real-world analogy:**

- **Interface** = A **blueprint** for building a specific kind of house. You can add extra rooms later (merge).
    
- **Type** = A **label** for anything — could be a house, car, or a mix — but once defined, you can’t alter it.
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When would you prefer `type` over `interface`?**

#### ✅ What to say:

> "When I need union types, intersections, or mapping over types — things that interfaces can’t do."

#### 🧠 Example:

```ts
type Status = "success" | "error";
type ApiResponse<T> = { data: T } | { error: string };
```

---

### ❓ Q2: **When would you prefer `interface` over `type`?**

#### ✅ What to say:

> "When defining object shapes that might be extended or implemented by classes, because `interface` supports declaration merging and class `implements`."

---

### ❓ Q3: **Can `interface` and `type` be used together?**

#### ✅ What to say:

> "Yes — you can combine them, for example, using a type alias for unions and interfaces for structure."

#### 🧠 Example:

```ts
type ID = string | number;

interface User {
  id: ID;
  name: string;
}
```

✅ Best of both worlds.

---
#  15 **Can TypeScript objects have optional properties?**

---

### 🔹 **🔸 What to say in the interview:**

> "Yes, TypeScript allows optional properties in objects by using the `?` symbol. This is useful when a property may or may not be present — like in partial data, API responses, or props. TypeScript won’t raise an error if the optional property is missing."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

If you’re not sure a property will always be there, just mark it as optional:

```ts
interface User {
  name: string;
  age?: number;
}
```

Now this is valid:

```ts
const u1: User = { name: "Shrey" }; // ✅ age is optional
```

✅ Optional properties let you write flexible and safer code.

---

### 🔹 **🔸 Real-world analogy:**

Think of an optional property like the “Apartment Number” on an address form.  
It’s not always there, and that’s fine — the rest of the address still works.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What happens if I try to access an optional property directly?**

#### ✅ What to say:

> "TypeScript will warn you that the value may be `undefined`, so you should add a check before using it."

#### 🧠 Example:

```ts
function greet(user: User) {
  if (user.age !== undefined) {
    console.log(`You are ${user.age} years old.`);
  }
}
```

✅ Helps avoid runtime crashes by encouraging safe access.

---

### ❓ Q2: **Can optional properties be used in function arguments?**

#### ✅ What to say:

> "Yes. You can mark function parameters as optional with `?`. This makes the argument optional during function calls."

#### 🧠 Example:

```ts
function greet(name: string, age?: number) {
  console.log(`Hello ${name}`);
  if (age !== undefined) console.log(`Age: ${age}`);
}

greet("Shrey");         // ✅ OK
greet("Aman", 27);      // ✅ OK
```

✅ Very common in React components with optional props.

---

### ❓ Q3: **Are optional properties the same as `undefined` types?**

#### ✅ What to say:

> "Not exactly. An optional property is _allowed_ to be missing, but it still has an implicit `undefined` type. You could also write it explicitly as `prop: string | undefined`, but using `?` is shorter and cleaner."

#### 🧠 Comparison:

```ts
// Both are valid, and mean similar things:
age?: number;               // optional (implicitly number | undefined)
age: number | undefined;    // explicit
```

✅ The `?` syntax is preferred for brevity.

---
#  16 (cont.) **What is the `readonly` property in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`readonly` in TypeScript is a modifier used on properties to make them immutable after their initial assignment. It helps enforce immutability by throwing a compile-time error if the value is changed after initialization."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- Add `readonly` before a property to say:
    

> “You can read this value, but you **can’t change it**.”

```ts
interface User {
  readonly id: number;
  name: string;
}

const user: User = { id: 1, name: "Shrey" };
user.id = 2; // ❌ Error: Cannot assign to 'id' because it is a read-only property
```

---

### 🔹 **🔸 Real-world analogy:**

`readonly` is like a **seat number on a flight ticket** — once it's printed, you can't change it. You can read it all you want, but the airline will yell if you try to sit somewhere else.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between `const` and `readonly`?**

#### ✅ What to say:

> "`const` is used for variables — it means the variable itself can’t be reassigned.  
> `readonly` is used for object properties — it means the specific property can’t be changed after initialization."

#### 🧠 Example:

```ts
const user = {
  id: 1,
  name: "Shrey"
};

user.id = 2; // ✅ Works unless we use `readonly`
```

But with:

```ts
interface User {
  readonly id: number;
}
const user: User = { id: 1 };
user.id = 2; // ❌ Compile-time error
```

✅ `const` protects _the binding_, `readonly` protects _the property_.

---

### ❓ Q2: **Can `readonly` be used with arrays or tuples?**

#### ✅ What to say:

> "Yes. TypeScript supports `readonly` arrays and tuples using `readonly` before the type or with `ReadonlyArray<T>`."

#### 🧠 Example:

```ts
const list: readonly number[] = [1, 2, 3];
list.push(4); // ❌ Error
```

✅ This is helpful in functional programming or React props to avoid mutations.

---

### ❓ Q3: **Can a class property be `readonly`?**

#### ✅ What to say:

> "Yes. In classes, `readonly` can be applied to class members, and they can only be set during initialization — either in the declaration or inside the constructor."

#### 🧠 Example:

```ts
class Product {
  readonly id: number;
  constructor(id: number) {
    this.id = id;
  }
}
```

✅ Attempting to change `id` outside the constructor will throw an error.

---
#  ⭐17. **What is a type alias in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "A type alias in TypeScript uses the `type` keyword to create a custom name for any type — whether it's a primitive, object, union, intersection, function, or tuple.  
> It's a flexible way to simplify and reuse complex types across your code."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

A **type alias** is like giving a nickname to a type — so you don’t have to repeat the same structure everywhere.

---

### ✅ Examples:

#### 🔸 Alias for an object:

```ts
type User = {
  name: string;
  age: number;
};
```

#### 🔸 Alias for union:

```ts
type Status = "loading" | "success" | "error";
```

#### 🔸 Alias for primitives:

```ts
type ID = number;
type Email = string;
```

#### 🔸 Alias for functions:

```ts
type Callback = (msg: string) => void;
```

✅ Clean, reusable, and readable.

---

### 🔹 **🔸 Real-world analogy:**

If you keep writing your full address everywhere, it’s tiring.  
So you create a shortcut like:

```ts
type HomeAddress = "Flat 202, XYZ Complex, Mumbai";
```

Now, whenever you need to refer to your address — just write `HomeAddress`.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When should I use a type alias instead of an interface?**

#### ✅ What to say:

> "Use `type` when you're working with unions, primitives, tuples, or need to compose types more flexibly.  
> Use `interface` for object structures, especially when you want to use inheritance or declaration merging."

#### 🧠 Example:

```ts
type ApiResponse = Success | Error; // ✅ Only possible with `type`, not `interface`
```

✅ `type` is more flexible, especially for non-object shapes.

---

### ❓ Q2: **Can I extend a type alias like an interface?**

#### ✅ What to say:

> "Yes, but instead of `extends`, we use intersections (`&`) to combine multiple types."

#### 🧠 Example:

```ts
type A = { a: number };
type B = { b: number };
type AB = A & B;

const val: AB = { a: 1, b: 2 };
```

✅ Interfaces use `extends`, types use `&`.

---

### ❓ Q3: **Can type aliases be recursive or nested?**

#### ✅ What to say:

> "Yes, type aliases can be nested and even recursive. This is especially useful for things like JSON trees or menu structures."

#### 🧠 Example:

```ts
type MenuItem = {
  title: string;
  children?: MenuItem[]; // recursive alias
};
```

✅ You’ll often use this in frontend tree-based structures (menus, folders, org charts).

---
# ⭐ 20. **What is an `enum` in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`enum` in TypeScript is a special data structure that defines a set of named constants. It helps represent a collection of related values in a readable and type-safe way.  
> Enums are useful when a variable can only take a limited set of options — like status codes, roles, or directions."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

You can think of an `enum` as a **group of labels for fixed values**.

Instead of this:

```ts
const status = "success"; // could be any string!
```

You write:

```ts
enum Status {
  Pending,
  Success,
  Failure
}

let s: Status = Status.Success;
```

✅ Now, the only allowed values are `Status.Pending`, `Status.Success`, or `Status.Failure`.

---

### 🔹 **🔸 Real-world analogy:**

Think of `enum` like a dropdown in a form — you can only choose from pre-defined options:  
👨‍💼 `"Admin"`, `"User"`, `"Guest"`  
🎯 `"Pending"`, `"Approved"`, `"Rejected"`

✅ Enums make sure you can’t select anything outside that list.

---

### 🔹 **🔸 Enum Types in TypeScript**

#### 1. **Numeric Enums (default)**

```ts
enum Direction {
  Up,    // 0
  Down,  // 1
  Left,  // 2
  Right  // 3
}
```

#### 2. **String Enums**

```ts
enum Role {
  Admin = "ADMIN",
  User = "USER",
  Guest = "GUEST"
}
```

✅ String enums are safer and easier to debug (e.g., logs show `"ADMIN"` instead of `0`)

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When should I use string enums vs numeric enums?**

#### ✅ What to say:

> "Use string enums when readability and clarity matter — especially for logging, API responses, or dropdown values. Use numeric enums when performance or memory is critical, like in low-level libraries."

#### 🧠 Example:

```ts
// ✅ Better logs and debugging
enum Status {
  Success = "SUCCESS",
  Error = "ERROR"
}
```

✅ You'll likely use **string enums** in most frontend projects.

---

### ❓ Q2: **Are enums compiled into JavaScript?**

#### ✅ What to say:

> "Yes. Enums are compiled into actual JavaScript objects with key-value pairs. That’s why they’re different from type unions like `"success" | "error"` which are purely compile-time constructs."

#### 🧠 Example:

```ts
enum Status {
  Success,
  Failure
}
```

Compiles to:

```js
{
  0: "Success",
  1: "Failure",
  Success: 0,
  Failure: 1
}
```

✅ You can access both name and value (bidirectional mapping).

---

### ❓ Q3: **What are the alternatives to using enums in TypeScript?**

#### ✅ What to say:

> "A common alternative is using union literal types — they're simpler and purely type-based.  
> For example, `type Status = "success" | "error"`. This doesn't produce extra JS code and works well for simple use cases."

#### 🧠 Example:

```ts
type Status = "success" | "error" | "pending";
```

✅ Better for lightweight apps or React props where enum power isn’t required.

---
# ⭐ 21. **How many data types can be assigned to enums?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript enums can hold either **numeric** or **string** values. By default, enums are numeric and auto-incremented. But you can explicitly assign string values for readability and safety. TypeScript does not support boolean or mixed-type enums."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

✅ Enums support **two types only**:

|Enum Type|Example|
|---|---|
|Numeric Enum|`enum Status { Pending = 0, Done = 1 }`|
|String Enum|`enum Role { Admin = "ADMIN" }`|

❌ You **cannot** do this:

```ts
enum Weird {
  One = 1,
  Text = "Two",
  Flag = true // ❌ Not allowed
}
```

✅ All values must be either:

- All numbers
    
- All strings
    

---

### 🔹 **🔸 Real-world analogy:**

Think of enums like **uniforms** in a team.

- One team chooses jersey numbers → numeric enums
    
- Another team uses printed names → string enums
    

But you can’t mix “Player #7” with “Player Blue” and “Player TRUE” — it confuses the system.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can I assign custom numbers in a numeric enum?**

#### ✅ What to say:

> "Yes. You can assign custom numeric values to any member. Unassigned members will auto-increment from the last set value."

#### 🧠 Example:

```ts
enum Status {
  Pending = 1,
  Approved = 5,
  Rejected // becomes 6
}
```

✅ Handy when you need to match backend values or DB IDs.

---

### ❓ Q2: **What happens if I mix types accidentally?**

#### ✅ What to say:

> "TypeScript will throw a compile-time error. Enums are not allowed to mix strings and numbers."

#### 🧠 Example:

```ts
enum Invalid {
  Ok = "yes",
  Error = 2 // ❌ Not allowed
}
```

✅ Keep them **all string** or **all number** — not both.

---

### ❓ Q3: **Which enum type is better for frontend apps?**

#### ✅ What to say:

> "String enums are generally preferred in frontend apps because they improve readability, debugging, and integrate better with APIs, logs, and UI elements."

#### 🧠 Example:

```ts
enum AlertType {
  Success = "SUCCESS",
  Warning = "WARNING",
  Error = "ERROR"
}
```

✅ Your logs and error messages will say `"ERROR"` instead of just `2` — easier to understand.

---
# ⭐ 22. **What is a Generic in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Generics in TypeScript allow you to write reusable and type-safe code by working with different data types without losing type information.  
> You define a generic with a type variable like `<T>`, which can be replaced with any actual type when the function, class, or interface is used."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Generics = **“I don’t know the type yet, but I’ll figure it out later — and I want to keep it safe.”**

Instead of this (no type safety):

```ts
function identity(arg: any): any {
  return arg;
}
```

You write this:

```ts
function identity<T>(arg: T): T {
  return arg;
}
```

Now, TypeScript knows exactly what type it is — even though you didn’t hardcode it.

```ts
identity<string>("hello");  // returns string
identity<number>(42);       // returns number
```

---

### 🔹 **🔸 Real-world analogy:**

Think of generics like **Tupperware** containers —  
You can put in rice, curry, or pasta — but the container always keeps track of what it’s holding, and it only gives back _exactly_ that.

✅ You get reusability + type safety.

---

### ✅ Common Use Cases

1. **Generic functions**
    

```ts
function wrapInArray<T>(value: T): T[] {
  return [value];
}
```

2. **Generic interfaces**
    

```ts
interface ApiResponse<T> {
  data: T;
  success: boolean;
}
```

3. **Generic React components**
    

```ts
type ListProps<T> = {
  items: T[];
  renderItem: (item: T) => JSX.Element;
};
```

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Why not just use `any` instead of generics?**

#### ✅ What to say:

> "`any` loses all type information. Generics retain the type throughout — so TypeScript can provide autocomplete, warnings, and better type inference."

#### 🧠 Example:

```ts
function logAny(arg: any) {
  arg.toFixed(); // ❌ No warning — might crash
}

function logTyped<T>(arg: T) {
  arg.toFixed(); // ✅ Error if T isn’t a number
}
```

✅ Generics give **safety**. `any` gives you **freedom (and chaos).**

---

### ❓ Q2: **Can I restrict what types a generic can accept?**

#### ✅ What to say:

> "Yes — that’s called a ‘generic constraint.’ You can use `extends` to restrict a generic to only certain shapes."

#### 🧠 Example:

```ts
function getLength<T extends { length: number }>(item: T): number {
  return item.length;
}

getLength("hello");   // ✅ Works
getLength([1, 2, 3]);  // ✅ Works
getLength(42);         // ❌ Error: number has no `length`
```

✅ You can safely assume the generic will have a `length` property.

---

### ❓ Q3: **Can I use multiple generics?**

#### ✅ What to say:

> "Yes — you can use multiple generic type variables to represent multiple input types and preserve their relationships."

#### 🧠 Example:

```ts
function pair<A, B>(a: A, b: B): [A, B] {
  return [a, b];
}

const result = pair<string, number>("Age", 30); // ✅ [string, number]
```

✅ Great for reusable data structures like pairs, maps, or responses.

---

Perfect — let’s wrap up this section with:

---

# ⭐ 23. **Are you aware of any utility types in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Yes. Utility types are built-in TypeScript helpers that allow you to transform existing types. They’re commonly used to make properties optional, readonly, pick specific keys, or remove certain properties from a type.
> 
> Popular ones include `Partial<T>`, `Required<T>`, `Readonly<T>`, `Pick<T, K>`, and `Omit<T, K>`."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Think of utility types as **tools that remix existing types** to get what you need — without rewriting everything.

---

### ✅ Most Common Utility Types

|Utility Type|What it does|Example|
|---|---|---|
|`Partial<T>`|Makes all properties optional|`Partial<User>`|
|`Required<T>`|Makes all optional properties required|`Required<User>`|
|`Readonly<T>`|Makes all properties read-only|`Readonly<User>`|
|`Pick<T, K>`|Keeps only selected properties|`Pick<User, "name">`|
|`Omit<T, K>`|Removes selected properties|`Omit<User, "password">`|
|`Record<K, T>`|Creates an object with specific keys and a common value type|`Record<string, number>`|
|`ReturnType<T>`|Extracts return type from a function|`ReturnType<typeof getUser>`|

---

### 🔹 **🔸 Real-world analogy:**

If a type is a pizza 🍕,  
Utility types are like cutting it into slices (`Pick`), removing toppings (`Omit`), or turning it into mini-pizzas (`Partial`) for a party tray.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When would you use `Partial<T>` in a frontend project?**

#### ✅ What to say:

> "When I want to create a draft version of an object — for example, in a form where not all fields are filled in yet — `Partial<T>` lets me avoid typing everything."

#### 🧠 Example:

```ts
interface User {
  name: string;
  email: string;
  password: string;
}

let formState: Partial<User> = {
  name: "Shrey"
}; // ✅ Only filling what I have
```

✅ Common with form handling, `useReducer`, or patch APIs.

---

### ❓ Q2: **How is `Omit<T, K>` useful in practice?**

#### ✅ What to say:

> "I use `Omit` when I want most of a type but need to exclude a few sensitive or irrelevant fields — like omitting a password before sending data to the frontend."

#### 🧠 Example:

```ts
type SafeUser = Omit<User, "password">;
```

✅ Useful for APIs, props, or log sanitization.

---

### ❓ Q3: **Can you combine multiple utility types together?**

#### ✅ What to say:

> "Yes — utility types can be composed to build very specific types. For example, I can use `Partial` and then `Pick`, or use `Omit` and then `Readonly`."

#### 🧠 Example:

```ts
type ReadonlyName = Readonly<Pick<User, "name">>;
```

✅ Now you have a `User` type with only the `name` field — and it’s readonly.

---
# ⭐ 24. **What is union typing in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Union typing in TypeScript allows a variable to hold **one of several defined types** using the `|` operator.  
> It’s useful when a value can be more than one type — for example, a function parameter that accepts both strings and numbers."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

Union types say:

> “This variable can be **A or B** — but not anything else.”

```ts
let id: string | number;

id = "abc";   // ✅
id = 123;     // ✅
id = true;    // ❌ Not allowed
```

✅ It restricts values to a known set — gives **flexibility without losing safety**.

---

### 🔹 **🔸 Real-world analogy:**

Think of union types like ordering a drink:

- You can choose **tea | coffee**
    
- But you can’t say **"beer"** — it’s not on the menu
    

✅ You choose _from_ options — but can’t go off-script.

---

### 🔹 **🔸 Where Union Types Are Useful:**

- React props (variant: `"primary" | "secondary" | "ghost"`)
    
- API responses (`string | null`)
    
- Function inputs (`number | string`)
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What happens if I access a method that's not shared by all union types?**

#### ✅ What to say:

> "TypeScript will throw an error unless you first **narrow the type** using `typeof`, `in`, or `instanceof`. It won't assume which type is active at runtime."

#### 🧠 Example:

```ts
function printId(id: string | number) {
  console.log(id.toUpperCase()); // ❌ Error

  if (typeof id === "string") {
    console.log(id.toUpperCase()); // ✅ Safe
  }
}
```

✅ This is called **type narrowing**.

---

### ❓ Q2: **Can union types be used in interfaces or type aliases?**

#### ✅ What to say:

> "Yes. You can use union types within `type` aliases or inside object properties to represent flexible data models."

#### 🧠 Example:

```ts
type AlertType = "success" | "error" | "warning";

interface AlertProps {
  type: AlertType;
  message: string;
}
```

✅ Great for strict prop options in UI components.

---

### ❓ Q3: **How does union differ from intersection types?**

#### ✅ What to say:

> "Union types mean ‘either/or’. Intersection types mean ‘both at once’.  
> Union makes the type broader — intersection makes it stricter."

#### 🧠 Example:

```ts
type A = { name: string };
type B = { age: number };

type Union = A | B;        // Either name or age (or both)
type Intersection = A & B; // Must have both name AND age
```

✅ Think of:

- Union = **any of the options**
    
- Intersection = **all of the ingredients combined**
    

---
# ⭐ 25. **What is the difference between Union and Intersection types?**

---

### 🔹 **🔸 What to say in the interview:**

> "Union types (`|`) mean a value can be **one of multiple types**.  
> Intersection types (`&`) mean a value must satisfy **all the combined types** at the same time.
> 
> So unions are more flexible, and intersections are more strict."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

|Type|Symbol|Meaning|Example Usage|
|---|---|---|---|
|**Union**|`|`|Value is **either** A or B|
|**Intersection**|`&`|Value must be **both** A and B|`{ name } & { age }`|

✅ Think of it like this:

```ts
type A = { name: string };
type B = { age: number };

type Union = A | B;        // Has name OR age (or both)
type Intersection = A & B; // Has name AND age
```

---

### 🔹 **🔸 Real-world analogy:**

- **Union**: A job posting that says "You must have a degree OR 5 years of experience."
    
- **Intersection**: A job posting that says "You must have a degree AND 5 years of experience."
    

✅ Unions offer alternatives, intersections require combinations.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can union types and intersection types be combined?**

#### ✅ What to say:

> "Yes, you can combine them to build complex types — for example, intersecting two unions, or intersecting a union with an object type."

#### 🧠 Example:

```ts
type A = { id: number } | { uuid: string };
type B = { isActive: boolean };

type Combined = A & B;
```

✅ This means:

- You must have `isActive`
    
- And **either** `id` or `uuid`
    

---

### ❓ Q2: **Which one should I use for React props or APIs?**

#### ✅ What to say:

> "Use **union types** when a prop or API response can vary — like a button `variant`.  
> Use **intersection types** when combining multiple pieces into one — like a prop that merges `User` and `Admin` data."

#### 🧠 Example:

```ts
type ButtonVariant = "primary" | "secondary"; // ✅ union

type CompleteUser = BasicInfo & Permissions;  // ✅ intersection
```

---

### ❓ Q3: **Are unions and intersections exclusive to object types?**

#### ✅ What to say:

> "No — you can use them with primitives, strings, functions, tuples, and more.  
> For example: `string | number`, `(a: string) => void | undefined`, etc."

#### 🧠 Example:

```ts
type ID = string | number;
type Callback = (() => void) & { delay: number };
```

✅ They're super flexible and appear everywhere in complex apps.

---
# ⭐ 26. **Which symbols are used to define Union and Intersection types in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "In TypeScript:
> 
> - The pipe symbol (`|`) is used for **union types**, meaning a value can be one of multiple types.
>     
> - The ampersand (`&`) is used for **intersection types**, meaning a value must satisfy all combined types."
>     

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- `|` (pipe) = "either this or that"
    
- `&` (ampersand) = "this and that"
    

✅ Example:

```ts
type A = { name: string };
type B = { age: number };

type Union = A | B;        // Either name OR age
type Intersection = A & B; // Both name AND age
```

---

### 🔹 **🔸 Real-world analogy:**

- `|` = "tea **or** coffee"
    
- `&` = "tea **with** sugar"
    

✅ You choose between options vs combine them.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Do these operators only apply to object types?**

#### ✅ What to say:

> "No — both union and intersection types can be used with strings, numbers, functions, arrays, tuples, and more."

#### 🧠 Example:

```ts
type ID = string | number;      // union with primitives
type Callback = (() => void) & { delay: number }; // intersection of function + object
```

---

### ❓ Q2: **Can you use parentheses to group types in complex unions/intersections?**

#### ✅ What to say:

> "Yes. Parentheses are supported and recommended when combining multiple unions and intersections to control precedence."

#### 🧠 Example:

```ts
type Complex = (A | B) & C; // A or B, and both must satisfy C
```

✅ Like math: parentheses help avoid ambiguity.

---
#  27. **What is the `in` operator in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "In TypeScript, the `in` operator is used in two main ways:
> 
> 1. For **type narrowing** — to check if a property exists on an object in union types.
>     
> 2. In **mapped types** — to iterate over keys and generate new types."
>     

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

---

### ✅ 1. **Type Guarding with `in`**

Use `in` to check which type an object is — **especially in a union of object types.**

```ts
type Dog = { bark: () => void };
type Cat = { meow: () => void };

function makeSound(animal: Dog | Cat) {
  if ("bark" in animal) {
    animal.bark(); // ✅ TypeScript now knows it's a Dog
  } else {
    animal.meow(); // ✅ Otherwise it's a Cat
  }
}
```

✅ This is called **type narrowing** — it helps TypeScript determine the correct type at runtime.

---

### ✅ 2. **Mapped Types with `in`**

```ts
type Keys = "name" | "email";

type User = {
  [K in Keys]: string;
};

// Becomes:
type User = {
  name: string;
  email: string;
}
```

✅ This lets you **dynamically generate object structures** — useful in libraries and form builders.

---

### 🔹 **🔸 Real-world analogy:**

- In type narrowing: `in` is like checking if a key exists on a door:
    
    > “If the key fits in the `bark` slot, it must be a Dog.”
    
- In mapped types: it’s like looping through a checklist and stamping “string” next to each item.
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How does `in` help with union types?**

#### ✅ What to say:

> "It acts as a type guard. When working with union types, `in` helps TypeScript decide which type you're dealing with by checking for unique properties."

#### 🧠 Example:

```ts
type Admin = { role: "admin"; accessLevel: number };
type User = { role: "user"; subscription: string };

function getRoleDetails(person: Admin | User) {
  if ("accessLevel" in person) {
    return person.accessLevel; // must be Admin
  }
}
```

---

### ❓ Q2: **What are mapped types and how does `in` work in them?**

#### ✅ What to say:

> "Mapped types use `in` to loop over a union of keys and create a new object type with those keys. This is useful for generic transformations."

#### 🧠 Example:

```ts
type MakeOptional<T> = {
  [K in keyof T]?: T[K];
};
```

✅ This turns any type into one where all properties are optional.

---

### ❓ Q3: **Is the `in` operator only for objects?**

#### ✅ What to say:

> "For type narrowing — yes, it checks if a key exists in an object.  
> But in mapped types, it's used over union types to generate keys dynamically — not just object literals."

---
#  28. **What is the `typeof` operator in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "`typeof` in TypeScript is used in two main contexts:
> 
> 1. At **runtime** (just like JavaScript) to check the type of a variable during execution.
>     
> 2. At **compile-time** (TypeScript-only) to extract the type of an existing variable or function to reuse its type elsewhere."
>     

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

There are **two versions** of `typeof`:

---

### ✅ 1. **Runtime `typeof` (JavaScript style)**

Used for **type narrowing** in conditional checks:

```ts
function logId(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // ✅ TypeScript knows it's a string
  } else {
    console.log(id.toFixed()); // ✅ It’s a number
  }
}
```

✅ This is used inside functions to help TypeScript figure out what you're dealing with.

---

### ✅ 2. **Compile-time `typeof` (TypeScript-only)**

Used to **extract a type** from an existing value or function:

```ts
const user = {
  name: "Shrey",
  age: 30,
};

type User = typeof user; // Same as: { name: string; age: number; }
```

✅ Super helpful for reusing types without duplicating structures.

---

### 🔹 **🔸 Real-world analogy:**

- Runtime `typeof` is like **checking a package label at delivery**: “Oh, this is fragile!”
    
- Compile-time `typeof` is like **copying the shape of a parcel** so you can reuse it to send something similar.
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **When should I use `typeof` at compile-time?**

#### ✅ What to say:

> "When I want to derive a type directly from a variable, function, or constant — especially useful when the object structure is large or dynamic."

#### 🧠 Example:

```ts
const config = {
  apiUrl: "https://...",
  retries: 3,
};

type Config = typeof config;
```

✅ Now you never have to duplicate or manually write the type.

---

### ❓ Q2: **Is `typeof` different in TypeScript and JavaScript?**

#### ✅ What to say:

> "Yes. At runtime, `typeof` behaves like in JavaScript — returning strings like `'number'`, `'string'`, etc.  
> At compile-time, TypeScript's `typeof` returns the actual **type** of the variable."

#### 🧠 Example:

```ts
// Runtime
typeof 123 // "number"

// Compile-time
type X = typeof 123; // X is inferred as: number
```

---

### ❓ Q3: **Can I use `typeof` to type a function’s return value?**

#### ✅ What to say:

> "Yes. You can use `typeof` in combination with `ReturnType` to extract the return type of a function."

#### 🧠 Example:

```ts
function getUser() {
  return { name: "Aman", age: 25 };
}

type User = ReturnType<typeof getUser>;
```

✅ Now you don’t have to repeat the return type manually — it's DRY and safe.

---
# ⭐ 29. **Do you have experience configuring a TypeScript project using `tsconfig.json`?**

---

### 🔹 **🔸 What to say in the interview:**

> "Yes, I’ve worked with `tsconfig.json` to configure TypeScript projects.  
> It’s the main configuration file that controls how TypeScript behaves during compilation — including file inclusion, module system, strictness settings, output location, and more.
> 
> I’ve used it to enable strict typing, define source/output folders, and adjust settings for React or Node environments."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

`tsconfig.json` = TypeScript's **settings control panel**

It tells the TypeScript compiler:

> “Here’s how to process my code.”

You define:

- Which files to include
    
- Where to output compiled JS
    
- Whether to enforce strict typing
    
- Module and target settings (ES6, CommonJS, etc.)
    

---

### ✅ Sample `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

✅ This setup:

- Converts `src` files to JS in `dist`
    
- Enables strict type checking
    
- Supports modern JS syntax
    

---

### 🔹 **🔸 Real-world analogy:**

Think of `tsconfig.json` as the **recipe book** for how TypeScript should cook your code.

- It sets the oven temp (ES6 vs ES5)
    
- Chooses ingredients (files/folders)
    
- Decides on plating (output folders)
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What does the `strict` flag do in `tsconfig.json`?**

#### ✅ What to say:

> "`strict` enables all strict type-checking features like `strictNullChecks`, `noImplicitAny`, and more.  
> It helps catch bugs earlier and enforces safe code practices."

#### 🧠 Example:

```ts
let msg; // ❌ In strict mode, this becomes type `any` unless defined
```

✅ Strict mode pushes you toward cleaner, more predictable code.

---

### ❓ Q2: **What’s the difference between `include` and `exclude`?**

#### ✅ What to say:

> "`include` tells TypeScript which files/folders to compile.  
> `exclude` tells it what to ignore — like `node_modules` or `dist`.  
> If not specified, TypeScript defaults to including everything under the root except `node_modules`."

#### 🧠 Example:

```json
"include": ["src/**/*"],
"exclude": ["tests", "build"]
```

✅ Keeps build time fast and output clean.

---

### ❓ Q3: **What happens if there’s no `tsconfig.json` file?**

#### ✅ What to say:

> "TypeScript falls back to its default settings.  
> You can still compile `.ts` files manually, but you won’t get customized compiler behavior."

#### 🧠 Analogy:

It's like driving a rental car without adjusting the mirrors — it'll work, but not tailored to your comfort.

---
#  30. **What is the use of `tsconfig.json`?**

---

### 🔹 **🔸 What to say in the interview:**

> "`tsconfig.json` is the configuration file for a TypeScript project.  
> It tells the TypeScript compiler how to compile the code — including which files to include, how strict the type checking should be, what output format to generate, and which ECMAScript version to target."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

It's like a **settings file** for your TypeScript project.

Without it, TypeScript has to **guess** what you want.  
With it, you **explicitly define** what your project expects.

---

### ✅ What you can control using `tsconfig.json`:

|Option|What it does|
|---|---|
|`compilerOptions`|How to compile the code (target version, module system, etc.)|
|`include`|Which files/folders to compile|
|`exclude`|Which files/folders to ignore|
|`strict`|Enforces strict typing rules|
|`outDir` / `rootDir`|Output and source folder locations|
|`esModuleInterop`|Enables compatibility with CommonJS/ES modules|

---

### 🔹 **🔸 Real-world analogy:**

`tsconfig.json` is like the **project’s rulebook or blueprint** —  
Without it, you might compile to the wrong JS version or include the wrong files.

✅ With it, everything stays consistent — especially in teams or CI/CD pipelines.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between `tsconfig.json` and `jsconfig.json`?**

#### ✅ What to say:

> "`tsconfig.json` is for TypeScript projects, and `jsconfig.json` is for JavaScript projects that want to use editor tooling like autocompletion and module resolution.
> 
> They’re similar in structure, but `tsconfig.json` triggers full TypeScript compilation."

---

### ❓ Q2: **Can you extend other `tsconfig.json` files?**

#### ✅ What to say:

> "Yes — using the `extends` field, you can base your config on another file. This is useful in monorepos or shared configurations."

#### 🧠 Example:

```json
{
  "extends": "../tsconfig.base.json",
  "compilerOptions": {
    "outDir": "dist"
  }
}
```

✅ Keeps things DRY across multiple projects/modules.

---

### ❓ Q3: **Where is `tsconfig.json` usually located?**

#### ✅ What to say:

> "It’s typically in the root folder of a TypeScript project. The compiler uses it to determine the context of what to compile."

---
#  31. **How do you compile TypeScript into JavaScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "To compile TypeScript into JavaScript, you use the `tsc` command — which stands for TypeScript Compiler.
> 
> Running `tsc` will look for the `tsconfig.json` file and compile all the `.ts` files based on its configuration. You can also compile a single file with `tsc filename.ts`."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

TypeScript doesn’t run directly in the browser — it needs to be **converted** to JavaScript first.

You do that using the command:

```bash
tsc
```

✅ This compiles **all** files defined in your `tsconfig.json`.

Or compile a single file manually:

```bash
tsc index.ts
```

You’ll get an `index.js` file as output.

---

### 🔹 **🔸 Real-world analogy:**

Think of `.ts` files as **raw ingredients**, and `tsc` as the **cooking process**.  
After running `tsc`, you get the final dish — the `.js` file — ready to be served in browsers.

---

### ✅ Typical Compile Setup

```json
// tsconfig.json
{
  "compilerOptions": {
    "outDir": "dist",
    "rootDir": "src"
  }
}
```

Then:

```bash
tsc
```

This takes files from `src/` and outputs JS into `dist/`.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What if I don't have a `tsconfig.json` — can I still compile?**

#### ✅ What to say:

> "Yes. You can compile a single file directly using `tsc filename.ts`.  
> But for larger projects, it’s best to use a `tsconfig.json` to manage settings and dependencies."

---

### ❓ Q2: **Can TypeScript watch files and recompile automatically?**

#### ✅ What to say:

> "Yes. You can use the `--watch` flag: `tsc --watch`.  
> It monitors changes and recompiles on the fly — perfect for development workflows."

---

### ❓ Q3: **How do you compile TS in a project with build tools like Webpack or Vite?**

#### ✅ What to say:

> "In real-world projects, we often use tools like Webpack, Vite, or Babel. These tools use loaders or plugins (like `ts-loader` or `esbuild`) to compile TypeScript as part of the bundling process."

✅ This is how most React/Vue/Node projects work in practice.

---
#  32. **Is TypeScript a strictly statically typed language?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript is a **gradually typed** language — not strictly typed like languages such as Java or Rust.  
> It provides **static typing** at compile time, but it's also flexible — allowing you to opt in or out of type safety using types like `any`, `unknown`, or implicit typing.
> 
> This makes it great for both small and large projects."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

- “Statically typed” means: **type errors are caught before you run the code.**
    
- “Gradual” means: **you can add as much or as little type safety as you want.**
    

You can do this:

```ts
let name: string = "Shrey";  // Strict, safe
```

Or this:

```ts
let name = "Shrey";          // Inferred, still safe
```

Or even this (less safe):

```ts
let name: any = "Shrey";     // Anything goes, TypeScript won’t warn you
```

✅ So TypeScript isn’t “strict-only” — it’s **flexible**.

---

### 🔹 **🔸 Real-world analogy:**

Think of TypeScript like **lane assist in a car**:

- You can **turn it on fully** (strict mode)
    
- Or keep it **partially on**
    
- Or **turn it off** (use `any` everywhere — not recommended 🚫)
    

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What does “gradually typed” mean exactly?**

#### ✅ What to say:

> "It means you can add types incrementally. You’re not forced to annotate everything.  
> This allows teams to migrate from JavaScript to TypeScript gradually, without rewriting the entire codebase."

#### 🧠 Example:

```ts
let id = 5;            // inferred
let name: string;      // explicit
let data: any = "abc"; // opt-out
```

✅ You can mix and match.

---

### ❓ Q2: **Can TypeScript be made stricter?**

#### ✅ What to say:

> "Yes — by enabling `"strict": true` in `tsconfig.json`, you activate all strict type rules like `noImplicitAny`, `strictNullChecks`, and more."

✅ This ensures the entire project follows stronger type safety.

---

### ❓ Q3: **How does TypeScript help compared to pure JavaScript if types are optional?**

#### ✅ What to say:

> "Even with partial types, TypeScript still provides better tooling — like autocomplete, refactoring support, and catching basic type mismatches.  
> And you can scale up the strictness as your project grows."

✅ It’s not all-or-nothing — **you scale TypeScript to your needs**.

---
#  33. **What are modules in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Modules in TypeScript are files that export and import values like variables, functions, classes, or types using `export` and `import` keywords.  
> They help organize code into reusable, maintainable parts — especially in large applications."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

A **module** in TypeScript = any file that uses `import` or `export`.

So if you have:

```ts
// math.ts
export function add(a: number, b: number) {
  return a + b;
}
```

And then in another file:

```ts
// app.ts
import { add } from './math';
console.log(add(2, 3)); // 5
```

✅ That’s a module system in action.

It allows you to split code into **logical chunks** and share only what’s needed.

---

### 🔹 **🔸 Real-world analogy:**

Modules are like **different departments in a company**:

- The HR department only shares what’s relevant (e.g. employee benefits)
    
- You don’t have access to _everything_ — just the things they explicitly `export`
    

✅ Keeps things private unless intentionally shared.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What’s the difference between CommonJS and ES Modules?**

#### ✅ What to say:

> "CommonJS is the module system used in Node.js (with `require`/`module.exports`), while ES Modules use `import`/`export`.  
> TypeScript supports both — you specify which one to use via `module` in `tsconfig.json`."

#### 🧠 Example:

```json
"module": "commonjs" // for Node
"module": "esnext"   // for modern JS/browser
```

---

### ❓ Q2: **Can you export multiple things from a module?**

#### ✅ What to say:

> "Yes. You can use named exports to export multiple items, or a default export for a single main value."

#### 🧠 Example:

```ts
// utils.ts
export const format = () => {};
export const log = () => {};

// OR
export default function mainUtil() {}
```

Then:

```ts
import { format, log } from './utils';
import mainUtil from './utils';
```

✅ You can mix both styles.

---

### ❓ Q3: **What happens if you import something that wasn't exported?**

#### ✅ What to say:

> "TypeScript will throw a compile-time error — it ensures you only use what was explicitly exported by the module."

---
#  34. **How does TypeScript support Object-Oriented Programming (OOP)?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript supports Object-Oriented Programming features like **classes**, **interfaces**, **inheritance**, **access modifiers**, **constructors**, and **polymorphism** — similar to languages like Java or C#.  
> This makes it easier to build scalable, maintainable, and structured codebases, especially for complex frontend apps or libraries."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

With TypeScript, you can:

- Create **classes**
    
- Define **constructors**
    
- Use **`public`, `private`, `protected`** for encapsulation
    
- Implement **interfaces**
    
- Extend **base classes** for inheritance
    

---

### ✅ Example: Basic OOP in TypeScript

```ts
class Animal {
  constructor(public name: string) {}

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks`);
  }
}

const dog = new Dog("Bruno");
dog.speak(); // Bruno barks
```

✅ You’re using:

- **Inheritance**
    
- **Method overriding (polymorphism)**
    
- **Public class fields**
    

---

### 🔹 **🔸 Real-world analogy:**

Think of a base class `Vehicle`, and subclasses like `Car`, `Bike`, and `Truck`.  
They all inherit core behavior (`start`, `stop`), but can override or extend it (`honk`, `cargo`).

✅ That’s classic OOP — and TypeScript fully supports it.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **What are access modifiers in TypeScript?**

#### ✅ What to say:

> "`public`, `private`, and `protected` are access modifiers that control where a class property or method can be accessed."

#### 🧠 Example:

```ts
class User {
  private password: string;

  constructor(public name: string, pwd: string) {
    this.password = pwd;
  }

  checkPassword(pwd: string) {
    return this.password === pwd;
  }
}
```

✅ `password` is only accessible inside the class.

---

### ❓ Q2: **How do `implements` and `extends` differ?**

#### ✅ What to say:

> "`implements` is used when a class wants to follow the structure of an interface.  
> `extends` is used when a class inherits from another class — including behavior."

#### 🧠 Example:

```ts
interface Printable {
  print(): void;
}

class Invoice implements Printable {
  print() {
    console.log("Invoice printed");
  }
}
```

✅ `implements` = structure  
✅ `extends` = structure + behaviour

---

### ❓ Q3: **Can TypeScript classes be abstract?**

#### ✅ What to say:

> "Yes. Abstract classes allow you to define base methods that must be implemented by subclasses. They cannot be instantiated directly."

#### 🧠 Example:

```ts
abstract class Shape {
  abstract getArea(): number;
}

class Circle extends Shape {
  constructor(public radius: number) {
    super();
  }

  getArea() {
    return Math.PI * this.radius ** 2;
  }
}
```

✅ This enforces a consistent interface across subclasses.

---
#  35. **What are decorators in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Decorators in TypeScript are special functions that can modify or annotate classes, methods, properties, or parameters.  
> They're part of a proposed ECMAScript feature and are enabled via the `experimentalDecorators` flag in `tsconfig.json`.
> 
> Decorators are commonly used in frameworks like Angular for dependency injection, metadata, and class enhancement."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

A **decorator** is like a **wrapper function** you attach to a class or method to **enhance or modify its behaviour**.

They start with `@`:

```ts
@sealed
class MyClass {}
```

The `@sealed` function runs and **modifies** the class during definition.

✅ They're like **middleware** for your classes/functions.

---

### 🔹 **🔸 Real-world analogy:**

Imagine putting a decorator on a cake 🍰:

- The cake is done, but now you're adding **frosting** or **labels**.
    
- You didn't change the cake's core, but you enhanced how it looks or behaves.
    

---

### ✅ Common Types of Decorators

|Decorator Type|Used On|Example Syntax|
|---|---|---|
|Class|Classes|`@Component()`|
|Property|Class fields|`@Input()`|
|Method|Class methods|`@Log()`|
|Parameter|Function args|`@Inject()`|

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Are decorators built into JavaScript?**

#### ✅ What to say:

> "No — decorators are still a stage 3 ECMAScript proposal.  
> TypeScript supports them via the `experimentalDecorators` flag in `tsconfig.json`, but they're not yet official in vanilla JS."

---

### ❓ Q2: **Where are decorators commonly used?**

#### ✅ What to say:

> "Decorators are heavily used in Angular to define components, services, and inject dependencies.  
> They’re also popular in NestJS, MobX, and other class-based libraries."

#### 🧠 Example (Angular):

```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent {}
```

✅ `@Component` is a **class decorator** that adds metadata to the class.

---

### ❓ Q3: **Can I write custom decorators?**

#### ✅ What to say:

> "Yes. You can create your own decorators by writing functions that take the target class or method as input and modify it."

#### 🧠 Example:

```ts
function Log(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const original = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${propertyKey} with`, args);
    return original.apply(this, args);
  };
}

class MyService {
  @Log
  greet(name: string) {
    return `Hello, ${name}`;
  }
}
```

✅ Adds logging without modifying the actual method.

---
#  36. **What are mixins in TypeScript?**

---

### 🔹 **🔸 What to say in the interview:**

> "Mixins in TypeScript are a way to combine properties and methods from multiple classes into a single class.  
> They let you reuse behaviour across classes without relying on traditional single inheritance."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

JavaScript & TypeScript only allow **single inheritance** (`extends` one class).  
Mixins let you **blend multiple classes** together so your new class gets features from all of them.

---

### ✅ Example:

```ts
type Constructor<T = {}> = new (...args: any[]) => T;

function Jumpable<TBase extends Constructor>(Base: TBase) {
  return class extends Base {
    jump() {
      console.log("Jumping...");
    }
  };
}

function Speakable<TBase extends Constructor>(Base: TBase) {
  return class extends Base {
    speak() {
      console.log("Speaking...");
    }
  };
}

class Person {}
class SuperPerson extends Jumpable(Speakable(Person)) {}

const hero = new SuperPerson();
hero.jump(); // Jumping...
hero.speak(); // Speaking...
```

✅ `SuperPerson` now has both `jump` and `speak` without needing a deep inheritance tree.

---

### 🔹 **🔸 Real-world analogy:**

If inheritance is **"You inherit your father’s surname"**,  
Mixins are **"You also inherit cooking skills from your mother and driving skills from your uncle"** — multiple traits combined into one.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How are mixins different from interfaces?**

#### ✅ What to say:

> "Interfaces only define structure — no actual implementation.  
> Mixins bring real methods and logic into the class, combining multiple implementations together."

---

### ❓ Q2: **When would you use mixins in frontend development?**

#### ✅ What to say:

> "Mixins are handy when you want to share behaviour across unrelated classes — for example, a logging feature that should be available in multiple services, or reusable animation behaviours for different UI components."

---

### ❓ Q3: **Are mixins common in modern TypeScript projects?**

#### ✅ What to say:

> "They’re less common than composition or inheritance, but are still useful in certain patterns, especially for framework or library development."

✅ In frameworks like **Vue**, older versions used mixins for reusing component logic (though now hooks/composition API are more common).

---
# ⭐ 37. **Have you used TypeScript with popular frontend frameworks like React?**

---

### 🔹 **🔸 What to say in the interview:**

> "Yes. While I started with JavaScript in React, I’ve explored and practiced integrating TypeScript for better type safety and maintainability.  
> Using TypeScript with React improves props validation, enforces correct state types, and provides better IntelliSense in editors.  
> It also makes refactoring safer in large codebases."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

When using React with TypeScript:

- You define **types for props** so components get the right data
    
- You define **types for state** to avoid mismatches
    
- You use **React types** like `FC`, `ChangeEvent`, `MouseEvent` for event handling
    

---

### ✅ Example: React + TypeScript

```tsx
type ButtonProps = {
  label: string;
  onClick: () => void;
};

const MyButton: React.FC<ButtonProps> = ({ label, onClick }) => {
  return <button onClick={onClick}>{label}</button>;
};

<MyButton label="Click Me" onClick={() => alert("Hello")} />; // ✅ Works
<MyButton label={123} onClick={() => {}} />; // ❌ TS Error
```

✅ Here, TypeScript ensures `label` must be a string and `onClick` must be a function.

---

### 🔹 **🔸 Real-world analogy:**

Think of TypeScript in React like **a strict restaurant order system** —  
You specify exactly what ingredients (props) a dish (component) needs, so no one sends a pizza with pineapple when you didn’t ask for it.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **How do you type component props in React with TypeScript?**

#### ✅ What to say:

> "You can use type aliases or interfaces to define the shape of props, and then apply them to a component using `React.FC` or directly in function parameters."

#### 🧠 Example:

```tsx
interface CardProps {
  title: string;
  children?: React.ReactNode;
}

const Card: React.FC<CardProps> = ({ title, children }) => (
  <div>
    <h1>{title}</h1>
    {children}
  </div>
);
```

---

### ❓ Q2: **How do you type state in React with TypeScript?**

#### ✅ What to say:

> "You provide the type as a generic parameter to `useState`."

#### 🧠 Example:

```tsx
const [count, setCount] = useState<number>(0);
```

✅ Ensures `count` will always be a number.

---

### ❓ Q3: **How does TypeScript help in large React projects?**

#### ✅ What to say:

> "It prevents runtime bugs by catching type mismatches early, provides better autocomplete, and makes refactoring safer by ensuring type changes propagate across the project."

---

Here’s the final one:

---

#  38. **What are the advantages and scenarios of using TypeScript in large projects?**

---

### 🔹 **🔸 What to say in the interview:**

> "TypeScript provides static type checking, which helps catch errors early and improves maintainability in large projects.  
> It enhances developer productivity through better IntelliSense, safer refactoring, and clear contracts between different parts of the codebase.  
> It’s especially useful in large teams where multiple developers work on shared modules, because types act as a form of documentation and prevent accidental misuse."

---

### 🔹 **🔸 Beginner-Friendly Explanation:**

In **small projects**, JavaScript’s flexibility is fine.  
In **large projects**, that flexibility can cause bugs when:

- A function gets the wrong kind of data
    
- Someone changes an object shape without telling others
    
- Refactoring silently breaks code in multiple files
    

✅ TypeScript **prevents these issues** by enforcing type rules at compile time.

---

### ✅ Key Advantages for Large Projects

1. **Early error detection** — Find bugs before running the code
    
2. **Self-documenting code** — Types act as built-in documentation
    
3. **Safe refactoring** — IDEs can update code confidently
    
4. **Improved collaboration** — Types clarify expectations between team members
    
5. **Better tooling** — Autocomplete and navigation in editors
    

---

### 🔹 **🔸 Real-world analogy:**

TypeScript in a large project is like **having architectural blueprints** when building a skyscraper:  
Everyone knows what each part should look like, and you catch mistakes before construction starts.

---

### 🔹 **🔸 Trailing Questions with Explanations**

---

### ❓ Q1: **Can TypeScript slow down development?**

#### ✅ What to say:

> "There’s a learning curve and some extra upfront work for type definitions.  
> But in large projects, it saves far more time during debugging and maintenance."

---

### ❓ Q2: **What kind of projects benefit the most from TypeScript?**

#### ✅ What to say:

> "Projects with large teams, long-term maintenance, complex data structures, or shared codebases benefit the most — for example, enterprise dashboards, design systems, or backend APIs."

---

### ❓ Q3: **Have you seen cases where TypeScript didn’t make sense?**

#### ✅ What to say:

> "For very small prototypes or quick proof-of-concepts, plain JavaScript might be faster since you avoid type setup.  
> But once a project starts growing, TypeScript quickly pays off."

---
