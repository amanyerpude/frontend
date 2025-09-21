
```markdown
# 🚀 Performance, Utilities, and Best Practices

1. What are the differences between `call()`, `apply()`, and `bind()`?  
2. What are interceptors in JavaScript (e.g., in APIs or libraries like Axios)?  
3. What is CORS?  
4. 🌟What is the difference between authentication and authorization?  
5. How do you optimize performance in JavaScript applications?  
6. 🌟What is the difference between debouncing and throttling? When would you use each?  
7. What are DRY, KISS, YAGNI, and SOLID principles?
```

### 📌 **Performance & Web Vitals**

- How to identify slowness in react applications
    
- Security vulnerabilities
    
- 🌟Able to run any performance tool (e.g. lighthouse, webpagetest, pagespeed, sitespeed.io, etc) on a website and gather report
    
- Able to explain different performance metrices e.g. (WebVitals, Critical Rendering Path)
    
- Able to tell performance improvement areas and their impact on performance metrices like:  
    Web Compression (gzip/brotli), Caching / CDN / Expirations, HTTP2, Service Workers
### 📌 **Security**

- Security vulnerabilities
    
- Able to explain security & compliance topics like: HIPPA, GDPR, PCI, Pll, XSS, CORS, MITM, CSP, CSRF, OWASP, SSL/TLS
    
- Able to explain mechanism to secure cookies

### 📌 **Frontend Architecture & Rendering**

- Can explain the frontend architecture of their existing project. And aware of architectural patterns like: MicroFrontends, SPA/MPA, Web Components, 12 Factor, MicroServices, ModuleFederation
    
- Is clear with reasons of tech stack decisions made
    
- Awareness of Rendering Techniques: SSR/CSR/SSG/ISR/ESR/PWA
    

---

### 📌 **Testing**

- Has experience of writing Unit Test cases in previous projects using Jest/Karma/Jasmine/Mocha/Enzyme/RTL
    
- Has experience in writing functional test cases (not snapshot testing)
    
- Able to tell test cases to be written for a given scenario
    
- Able to explain HTTP API mocking and browser API methods mocking (e.g. mocking localstorage)
    

---

### 📌 **Caching**

- Able to explain browser caching through http headers (cache-control, etag)
    
- Able to explain browser caching using service workers and benefits over http caching
    
- Able to tell different caching strategies for service workers
### 📌 **Accessibility**

- Web accessibility
    
- Understands accessibility guidelines like: A/AA/AAA/ADA/508
    
- Able to explain use of aria live regions for dynamic content announcement
    
- Able to use any screen reader to access a website
    
- Able to create accesible forms and write code adhering to accessibility
--------------------------------------------------------------------------
# **1️⃣ What are the differences between `call()`, `apply()`, and `bind()`?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **all three are used to set the `this` value for a function**.
    
- Explain **key differences:**
    
    - `call()` → calls immediately, arguments as comma-separated.
        
    - `apply()` → calls immediately, arguments as an array.
        
    - `bind()` → returns a new function with `this` fixed, does not execute immediately.
        
- Use a table for clarity.
    

---

## 💡 **Answer**

|Method|Calls Immediately?|Arguments Passed As|Returns?|
|---|---|---|---|
|`call()`|✅ Yes|Comma-separated values|Function's return value|
|`apply()`|✅ Yes|Array of values|Function's return value|
|`bind()`|❌ No|Comma-separated values|New function (bound)|

---

## 🧩 **Example**

```js
const person = { name: "Alice" };

function greet(msg) {
  console.log(`${msg}, I'm ${this.name}`);
}

greet.call(person, "Hi");         // Hi, I'm Alice
greet.apply(person, ["Hello"]);   // Hello, I'm Alice

const sayHey = greet.bind(person);
sayHey("Hey"); // Hey, I'm Alice
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use bind()?**

#### ✅ **How to Answer in an Interview**

- Use `bind()` when you **want to fix `this` but call the function later** (e.g., event handlers, callbacks).
    

---

### **2️⃣ How are call/apply used for function borrowing?**

#### ✅ **How to Answer in an Interview**

- You can **borrow methods from other objects by setting `this`**.
    

```js
const obj1 = { name: "Bob" };
const obj2 = { name: "Sam" };

function sayName() { console.log(this.name); }

sayName.call(obj1); // Bob
sayName.call(obj2); // Sam
```

---

## 🎯 **Interview Tips**

✅ Always **show all three with examples**.  
✅ Mention **call/apply execute immediately, bind does not**.  
✅ Be ready for follow-ups on **arrow functions ignoring `this` binding**.

# **2️⃣ What are interceptors in JavaScript (e.g., in APIs or libraries like Axios)?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **interceptors are functions that run before a request is sent or after a response is received in API libraries like Axios**.
    
- Mention they are used for **adding headers, logging, error handling, or modifying responses globally**.
    
- Show **a short Axios example**.
    

---

## 💡 **Answer**

**Interceptors** are functions that allow you to **intercept and modify HTTP requests or responses** before they are handled by `.then()` or `.catch()`.

✅ **Use Cases:**  
✔ Adding authentication tokens  
✔ Logging API calls  
✔ Handling global errors  
✔ Transforming request/response data

---

## 🧩 **Example (Axios Interceptors)**

```js
import axios from "axios";

// Request Interceptor
axios.interceptors.request.use((config) => {
  config.headers.Authorization = "Bearer my-token";
  return config;
});

// Response Interceptor
axios.interceptors.response.use(
  (response) => response,
  (error) => {
    console.error("API Error:", error);
    return Promise.reject(error);
  }
);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Can you have multiple interceptors?**

#### ✅ **How to Answer in an Interview**

- Yes, Axios allows **multiple interceptors**, and they **run in the order they were added**.
    

---

### **2️⃣ What are common real-world use cases for interceptors?**

#### ✅ **How to Answer in an Interview**

- Attaching tokens to every request
    
- Retrying failed requests
    
- Showing/hiding global loaders
    
- Handling 401 (unauthorized) errors globally
    

---

## 🎯 **Interview Tips**

✅ Always **give a code example with both request & response interceptors**.  
✅ Mention **real-world use cases (auth, logging, error handling)**.  
✅ Be ready for follow-ups on **fetch API equivalents (wrappers for fetch)**.

# **3️⃣ What is CORS?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **CORS (Cross-Origin Resource Sharing) is a security feature implemented by browsers**.
    
- Explain **it prevents unauthorized requests from one origin to another**.
    
- Mention **how servers handle CORS using headers like `Access-Control-Allow-Origin`**.
    

---

## 💡 **Answer**

**CORS (Cross-Origin Resource Sharing)** is a **browser security mechanism** that **restricts web pages from making requests to a different domain, protocol, or port** unless the server explicitly allows it.

---

### 🔹 **Why is it needed?**

✅ Prevents malicious sites from making unauthorized API calls on behalf of users.  
✅ The server must send specific **CORS headers** to allow the request.

---

### 🔹 **Example Header**

```http
Access-Control-Allow-Origin: https://example.com
Access-Control-Allow-Methods: GET, POST
Access-Control-Allow-Headers: Content-Type
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is a preflight request?**

#### ✅ **How to Answer in an Interview**

- A **preflight request (OPTIONS)** is sent by the browser **before certain requests (e.g., POST with custom headers)** to check if the server allows it.
    

---

### **2️⃣ How to fix CORS errors in development?**

#### ✅ **How to Answer in an Interview**

- Configure the server to send correct CORS headers.
    
- Use a proxy in development (`webpack-dev-server`, `vite proxy`).
    

---

## 🎯 **Interview Tips**

✅ Always mention **browser enforces CORS, not servers**.  
✅ Use **real-world example: calling an API from frontend at a different domain**.  
✅ Be ready for follow-ups on **preflight requests and CORS headers**.

# **4️⃣ What is the difference between authentication and authorization?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **authentication verifies identity, while authorization determines access rights**.
    
- Use a **real-world analogy (checking ID vs checking permissions)**.
    
- Show a **comparison table**.
    

---

## 💡 **Answer**

|Feature|**Authentication**|**Authorization**|
|---|---|---|
|**Definition**|Verifies **who the user is**|Determines **what the user can do**|
|**Example**|Login with username/password|Checking if user can access admin page|
|**Happens When?**|Always **before authorization**|After authentication|
|**Methods**|Passwords, OTP, biometrics, tokens|Role-based, permissions, ACLs|

---

### 🔹 **Analogy**

- **Authentication** = Showing your ID card at the entrance.
    
- **Authorization** = Security guard checking if you can enter VIP area.
    

---

## 🧩 **Example (Code)**

```js
// Authentication (login)
if (username === "admin" && password === "1234") {
  console.log("User authenticated");
}

// Authorization (check role)
if (user.role === "admin") {
  console.log("Access granted");
} else {
  console.log("Access denied");
}
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Can you have authorization without authentication?**

#### ✅ **How to Answer in an Interview**

- No. Authorization **always requires authentication first**.
    

---

### **2️⃣ What are common methods of authentication?**

#### ✅ **How to Answer in an Interview**

- Password-based login
    
- Multi-factor authentication (MFA)
    
- OAuth tokens (Google/Facebook login)
    
- JWT (JSON Web Tokens)
    

---

## 🎯 **Interview Tips**

✅ Always **differentiate identity (authentication) vs access rights (authorization)**.  
✅ Use a **real-world analogy (ID card + access control)**.  
✅ Be ready for follow-ups on **OAuth, JWT, role-based access control**.

# **5️⃣ How do you optimize performance in JavaScript applications?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **performance optimization improves load time, rendering speed, and runtime efficiency**.
    
- Break down **best practices into categories: network, rendering, and JS execution**.
    
- Give practical examples.
    

---

## 💡 **Answer**

### 🔹 **1. Reduce JavaScript Execution Time**

✅ Minify and bundle JS using Webpack/Vite/Rollup.  
✅ Use lazy loading and code splitting (`import()` for dynamic imports).  
✅ Avoid blocking the main thread with heavy loops.

---

### 🔹 **2. Optimize Rendering**

✅ Minimize **DOM manipulation** (batch updates, use Virtual DOM in React).  
✅ Use `requestAnimationFrame()` for animations.  
✅ Avoid layout thrashing (group DOM reads/writes).

---

### 🔹 **3. Reduce Network Load**

✅ Use caching (Service Workers, IndexedDB).  
✅ Compress assets (gzip/brotli).  
✅ Use CDN for static files.

---

### 🔹 **4. Improve Memory Management**

✅ Remove unused event listeners.  
✅ Use pagination/infinite scroll for large lists.  
✅ Free up references (`obj = null`) when not needed.

---

## 🧩 **Example**

```js
// Instead of updating DOM in a loop
for (let i = 0; i < 100; i++) {
  document.body.innerHTML += `<p>${i}</p>`; // ❌ Bad
}

// Use fragment (efficient)
const fragment = document.createDocumentFragment();
for (let i = 0; i < 100; i++) {
  const p = document.createElement("p");
  p.textContent = i;
  fragment.appendChild(p);
}
document.body.appendChild(fragment);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How do you optimize React app performance?**

#### ✅ **How to Answer in an Interview**

- Use React.memo, useCallback, useMemo
    
- Code splitting with React.lazy + Suspense
    
- Avoid unnecessary re-renders by proper key usage
    

---

### **2️⃣ How can you reduce JS bundle size?**

#### ✅ **How to Answer in an Interview**

- Remove unused dependencies
    
- Use tree-shaking
    
- Use dynamic imports and CDN for heavy libraries
    

---

## 🎯 **Interview Tips**

✅ Always **cover network, DOM, and JS execution optimizations**.  
✅ Give **practical examples** (bundle splitting, caching).  
✅ Be ready for **React-specific follow-ups** if interviewer is frontend-focused.

# **6️⃣ What is the difference between debouncing and throttling? When would you use each?**

---

## ✅ **How to Answer in an Interview**

- Start by defining **both techniques used to control how often a function is executed**.
    
- Explain **debounce delays execution until the user stops triggering the event**, while **throttle executes at fixed intervals**.
    
- Use a **table for clarity**.
    

---

## 💡 **Answer**

| Feature        | **Debouncing**                                                          | **Throttling**                                                                  |
| -------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Definition** | Executes the function **after a delay** once the event stops triggering | Executes the function **at fixed intervals** even if the event keeps triggering |
| **Use Case**   | Search input (wait until user stops typing)                             | Scroll event (run every 200ms while scrolling)                                  |
| **Example**    | Autocomplete input                                                      | Infinite scroll, resize handler                                                 |

---

## 🧩 **Example (Debounce)**

```js
function debounce(func, delay) {
  let timeout;
  return function (...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), delay);
  };
}

const search = debounce(() => console.log("API Call"), 500);
input.addEventListener("keyup", search);
```

---

## 🧩 **Example (Throttle)**

```js
function throttle(func, limit) {
  let lastCall = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func.apply(this, args);
    }
  };
}

const logScroll = throttle(() => console.log("Scrolling..."), 1000);
window.addEventListener("scroll", logScroll);
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use debounce vs throttle?**

#### ✅ **How to Answer in an Interview**

- **Debounce** → For events where you want **only one final action** (search bar, form validation).
    
- **Throttle** → For events that fire **continuously but should execute periodically** (scroll, resize).
    

---

### **2️⃣ Which technique improves performance more?**

#### ✅ **How to Answer in an Interview**

- Both help performance, but **debounce avoids unnecessary API calls**, while **throttle keeps UI responsive** for frequent events.
    

---

## 🎯 **Interview Tips**

✅ Always **use a table to differentiate**.  
✅ Show **both debounce and throttle code snippets**.  
✅ Be ready for **React-specific use cases (debouncing input state updates)**.

# **7️⃣ What are DRY, KISS, YAGNI, and SOLID principles?**

---

## ✅ **How to Answer in an Interview**

- Start by saying these are **software development principles** that make code **cleaner, maintainable, and scalable**.
    
- Define each principle briefly with examples.
    
- Use a **table for quick understanding**.
    

---

## 💡 **Answer**

|Principle|Meaning|Explanation|Example|
|---|---|---|---|
|**DRY**|_Don't Repeat Yourself_|Avoid duplicate logic; reuse code|Create reusable functions instead of copy-pasting code|
|**KISS**|_Keep It Simple, Stupid_|Write simple, readable code|Avoid over-engineering a solution|
|**YAGNI**|_You Aren’t Gonna Need It_|Don’t add features until needed|Don’t write extra unused functions|
|**SOLID**|5 OOP design principles|Helps in scalable, maintainable code|See below|

---

### 🔹 **SOLID Breakdown**

1️⃣ **S – Single Responsibility Principle (SRP)** → A class/module should have one responsibility.  
2️⃣ **O – Open/Closed Principle** → Open for extension, closed for modification.  
3️⃣ **L – Liskov Substitution Principle** → Subclasses should work without altering base class behavior.  
4️⃣ **I – Interface Segregation Principle** → Prefer small, specific interfaces.  
5️⃣ **D – Dependency Inversion Principle** → Depend on abstractions, not concrete implementations.

---

## 🧩 **Example (DRY & KISS)**

❌ **Bad**

```js
function calcCircleArea(r) { return 3.14 * r * r; }
function calcCircleCircumference(r) { return 2 * 3.14 * r; }
```

✅ **Good (DRY)**

```js
const PI = 3.14;
function circleArea(r) { return PI * r * r; }
function circleCircumference(r) { return 2 * PI * r; }
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why are these principles important?**

#### ✅ **How to Answer in an Interview**

- They **reduce bugs, improve code readability, and make scaling easier**.
    

---

### **2️⃣ Can you give a real-world example of YAGNI?**

#### ✅ **How to Answer in an Interview**

- Adding **unused config options or APIs "just in case"** wastes time.
    
- Instead, **build features only when needed**.
    

---

## 🎯 **Interview Tips**

✅ Always **expand SOLID** as interviewers expect it.  
✅ Give **real examples for DRY, KISS, and YAGNI**.  
✅ Be ready for follow-ups on **design patterns and clean code practices**.

--------------------------------------------------------------------------

# Performance, Utilities & Best Practices – JavaScript Interview Prep

Here you'll find beginner-friendly explanations, examples, practical interview talking points, and common trailing questions (with answers) for every question in this section.

## 1. What are the differences between call, apply, and bind?

**Explanation:**  
All three methods are used to control what `this` refers to inside a function.

- **call:** Invokes the function right away, with arguments passed one by one.
    
- **apply:** Invokes the function right away, but arguments are passed as an array.
    
- **bind:** Returns a new function with `this` fixed, but doesn't call it immediately.
    

**Example:**

javascript

``function sayHello(greeting) {   return `${greeting}, ${this.name}`; } const person = { name: "Pat" }; sayHello.call(person, "Hi");          // "Hi, Pat" sayHello.apply(person, ["Hello"]);    // "Hello, Pat" const sayHi = sayHello.bind(person); sayHi("Hey");                         // "Hey, Pat"``

**What to say in an interview:**  
"`call` and `apply` execute the function with a custom `this` immediately—`call` uses comma arguments, `apply` uses an array. `bind` saves the context for later, returning a new function."

## Trailing Question: Why would you use bind?

**Answer:**  
You use `bind` when passing a function as a callback and want it to always have the correct `this` value.

## 2. What are interceptors in JavaScript when working with APIs or libraries like Axios?

**Explanation:**  
**Interceptors** are functions you can define to process requests or responses before they're handled. In libraries like Axios, you can use interceptors to modify outgoing requests (e.g., add a token) or to process incoming responses (e.g., log out users on 401 errors).

**Example (Axios):**

javascript

`axios.interceptors.request.use(   config => {    config.headers.Authorization = "Bearer token";    return config;  } ); axios.interceptors.response.use(   response => response,  error => {    if (error.response.status === 401) {      // Handle unauthorized    }    return Promise.reject(error);  } );`

**What to say in an interview:**  
"In Axios, interceptors let me automatically handle or modify requests and responses—like adding auth tokens or handling errors globally."

## Trailing Question: When are interceptors especially useful?

**Answer:**  
Interceptors are useful for common tasks you want to apply to all API calls, like adding headers, error handling, or logging.

## 3. What is CORS?

**Explanation:**  
**CORS** (Cross-Origin Resource Sharing) is a browser security feature that restricts web pages from making requests to a domain different from the one that served the page. Servers must explicitly allow cross-origin requests using special headers.

**Example:**  
A web app at `example.com` trying to fetch data from `api.another.com` will only succeed if `api.another.com` sends back headers like:

text

`Access-Control-Allow-Origin: https://example.com`

**What to say in an interview:**  
"CORS is a browser security policy restricting cross-site HTTP requests. The server controls what origins are allowed using special HTTP headers."

## Trailing Question: What happens if CORS is not enabled?

**Answer:**  
The browser blocks the request and shows a CORS error. The server needs to allow the request's origin for it to succeed.

## 4. What is authentication vs authorization?

**Explanation:**

- **Authentication** is confirming who a user is (login, verifying identity).
    
- **Authorization** is determining what actions or resources a user is allowed to access.
    

**Example:**

- Signing into Gmail = authentication.
    
- Accessing your inbox but not someone else's = authorization.
    

**What to say in an interview:**  
"Authentication answers 'Who are you?' Authorization answers 'What can you do?' Both are needed for secure applications."

## Trailing Question: Can you have one without the other?

**Answer:**  
Yes. You might authenticate (log in) but have no authorization for certain resources.

## 5. How do you optimize performance in JavaScript applications?

**Explanation & Tips:**

- Minimize DOM manipulations.
    
- Use event delegation for large lists.
    
- Debounce or throttle frequent events (like scroll/resize).
    
- Avoid memory leaks by removing unused event listeners.
    
- Use code splitting and lazy loading.
    
- Cache expensive computations.
    
- Write efficient algorithms.
    

**Example:**

javascript

`// Debounce an input event let timeout; input.addEventListener('input', () => {   clearTimeout(timeout);  timeout = setTimeout(() => {    // Perform action  }, 300); });`

**What to say in an interview:**  
"I optimize JS apps by reducing DOM updates, handling heavy computations off the main thread, debouncing/throttling frequent events, and caching when possible."

## Trailing Question: What tools help measure JavaScript performance?

**Answer:**  
Browser DevTools (Performance tab), Lighthouse Audits, and library-specific tools help analyze bottlenecks.

## 6. What is meant by debouncing and throttling?

**Explanation:**

- **Debouncing:**  
    Ensures a function only runs after a certain pause in events (wait X ms after the last trigger). Useful for search bars or window resizing.
    
- **Throttling:**  
    Ensures a function runs at most once every X ms, no matter how many times it's triggered (limits frequency).
    

**Example:**

javascript

`// Simple debounce function debounce(fn, delay) {   let timer;  return (...args) => {    clearTimeout(timer);    timer = setTimeout(() => fn.apply(this, args), delay);  }; }`

**What to say in an interview:**  
"Debouncing delays a function's execution until a pause in activity—great for search inputs. Throttling limits a function so it runs at a set rate—good for scroll events."

## Trailing Question: When would you use throttling vs debouncing?

**Answer:**  
Use debouncing for actions that should only happen after the event stops (search, typing). Use throttling for periodic actions needing regular updates (scroll, resize).

## 7. What are DRY, KISS, YAGNI, and SOLID principles?

**Explanation:**

- **DRY:** Don't Repeat Yourself — avoid duplicating logic.
    
- **KISS:** Keep It Simple, Stupid — strive for simplicity.
    
- **YAGNI:** You Aren't Gonna Need It — don't add code for possible future needs.
    
- **SOLID:**
    
    - **S**: Single Responsibility
        
    - **O**: Open/Closed (open for extension, closed for modification)
        
    - **L**: Liskov Substitution (subtypes must be substitutable)
        
    - **I**: Interface Segregation
        
    - **D**: Dependency Inversion
        

**What to say in an interview:**  
"DRY means I avoid code duplication. KISS guides me to simple solutions. YAGNI cautions against coding features 'just in case.' SOLID stands for five principles supporting good object-oriented design, like single responsibility and open/closed."

## Trailing Question: Why do these principles matter?

**Answer:**  
They help produce code that is easier to maintain, test, and extend, while reducing bugs and complexity.

Let me know if you'd like to review more sections, need further examples, or want to practice delivering your answers!