
```markdown
# 🖼 DOM & Frontend Concepts

1. What is the Document Object Model (DOM), and how does JavaScript interact with it?  
2. How do you render HTML elements dynamically in JavaScript or React?  
3. How do you prevent default actions and stop event propagation in JavaScript?  
4. 🌟What is event bubbling and event capturing?  
5. Explain event bubbling and event capturing with a practical example.  
6. What is the difference between an event object and a custom event in JavaScript?  
7. 🌟What is event delegation in JavaScript?  
8. 🌟What is Shadow DOM?  
9. 🌟How do you detect browser or platform in JavaScript?  
10. What is layout thrashing?  
11. What are the stages of the render pipeline?  
12. What is script execution order in browsers?  
13. What is CSS containment and how does it affect painting?
14. 🌟DOM Manipulation (`querySelector`, `querySelectorAll`, `innerHTML`, DOM Fragments[optional])
```

### 📌 **DOM & Browser APIs**

- 🌟Event Listeners (Able to use following: addEventListener, event object, stopPropagation, preventDefault)
    
- DOM Manipulation (querySelector, querySelectorAll, innerHTML, DOM Fragments[optional])
    
- Fetch API
    
- Able to create modules, and use import and export statement
    
- Able to modify and transform objects
    
- Able to create Form in native HTML and submit without JS. Able to add validations to form. Knows how to use FormData API.
    
- 🌟Able to explain browser side storage (cookies / localstorage / sessionstorage / indexeddb)

--------------------------------------------------------------------------
# **1️⃣ What is the Document Object Model (DOM), and how does JavaScript interact with it?**

---

## ✅ **How to Answer in an Interview**

- Start by defining the DOM in **simple terms**: It’s a **tree-like representation of an HTML page**.
    
- Mention that **JavaScript can use the DOM to create, update, delete, or style elements dynamically**.
    
- Show that **DOM is not the same as HTML—it’s a runtime representation of the page in memory**.
    

---

## 💡 **Answer**

The **Document Object Model (DOM)** is a **programmatic representation of an HTML document as a tree structure**, where **each element is a node**.

- **HTML is just text**, but when loaded in the browser, it is converted into the DOM (a tree-like structure in memory).
    
- **JavaScript can interact with the DOM to:**
    
    - Read or change content (`textContent`, `innerHTML`)
        
    - Add or remove elements (`appendChild`, `remove()`)
        
    - Modify styles (`style.color = "red"`)
        
    - Listen to user actions (`addEventListener`)
        

---

## 🧩 **Example**

```html
<p id="demo">Hello!</p>
<button onclick="changeText()">Click Me</button>

<script>
function changeText() {
  document.getElementById("demo").textContent = "You clicked the button!";
}
</script>
```

✔ Here, **JavaScript modifies the DOM** by changing the text inside the `<p>` tag when the button is clicked.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Is the DOM part of JavaScript or the browser?**

#### ✅ **How to Answer in an Interview**

- Explain that the DOM is provided by **the browser**, not JavaScript itself.
    

#### 💡 **Answer**

The **DOM is a Web API provided by browsers**, not part of the JavaScript language.  
JavaScript **uses DOM APIs** (like `document.querySelector`) to interact with the page.

---

### **2️⃣ How is the DOM different from HTML?**

#### ✅ **How to Answer in an Interview**

- HTML is the **static source code**, while the DOM is the **live, in-memory representation**.
    

#### 💡 **Answer**

- **HTML** → The actual markup written in the file.
    
- **DOM** → A **tree-like structure created in memory** when the browser parses HTML.
    
- The DOM **can change dynamically**, even after the page loads.
    

---

## 🎯 **Interview Tips**

✅ Beginners often confuse **HTML with DOM**—always clarify that **DOM is dynamic and manipulable via JS**.  
✅ Mention **common DOM methods** (`getElementById`, `querySelector`, `createElement`).  
✅ Interviewers may ask **how React manipulates the DOM differently (Virtual DOM)**—be prepared for follow-ups.

# **2️⃣ How do you render HTML elements dynamically in JavaScript or React?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **dynamic rendering means creating or updating UI elements based on user actions, API data, or logic at runtime**.
    
- Explain **how it is done in vanilla JS (DOM APIs)** and **how React handles it with JSX and re-rendering**.
    
- Give **examples for both JS and React** to make it clear for beginners.
    

---

## 💡 **Answer**

Dynamic rendering means **adding, removing, or updating HTML elements while the page is running (without reloading)**.

### 🔹 **In Vanilla JavaScript**

- Use **DOM methods** to create and insert elements:
    
    - `createElement()`
        
    - `appendChild()`
        
    - `innerHTML`
        

```html
<div id="container"></div>
<script>
const div = document.createElement("p");
div.textContent = "Hello, I was created dynamically!";
document.getElementById("container").appendChild(div);
</script>
```

---

### 🔹 **In React**

- React uses **JSX** (a syntax similar to HTML) and **state changes** to re-render UI automatically.
    

```jsx
import { useState } from "react";

function App() {
  const [items, setItems] = useState(["Apple", "Banana"]);

  return (
    <div>
      {items.map((item, i) => <p key={i}>{item}</p>)}
      <button onClick={() => setItems([...items, "Mango"])}>Add Item</button>
    </div>
  );
}
```

✔ In React, **changing state (`setItems`) triggers a re-render**, so new elements appear automatically.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between innerHTML and createElement()?**

#### ✅ **How to Answer in an Interview**

- `innerHTML` is simpler but **less safe (can lead to XSS attacks)**, while `createElement()` is **safer and more structured**.
    

#### 💡 **Answer**

```js
// Using innerHTML (less safe)
container.innerHTML += "<p>Hello</p>";

// Using createElement (better)
const p = document.createElement("p");
p.textContent = "Hello";
container.appendChild(p);
```

---

### **2️⃣ How does React rendering differ from DOM manipulation?**

#### ✅ **How to Answer in an Interview**

- React uses a **Virtual DOM** to efficiently update only the changed parts of the UI.
    

#### 💡 **Answer**

Instead of directly manipulating the DOM, React:  
1️⃣ Creates a **Virtual DOM copy** of the UI.  
2️⃣ Compares it with the previous version (**diffing**).  
3️⃣ Updates only the parts that changed (**reconciliation**).

---

## 🎯 **Interview Tips**

✅ Show **both Vanilla JS and React approaches**—interviewers like comparisons.  
✅ Mention **React’s Virtual DOM advantage** over manual DOM manipulation.  
✅ Be ready for follow-ups on **React’s key prop & re-rendering behavior**.

---

# **3️⃣ How do you prevent default actions and stop event propagation in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **browsers have default behaviours for certain events (like links navigating, form submissions)**.
    
- Explain **`event.preventDefault()` stops the default action**, and **`event.stopPropagation()` stops the event from bubbling up**.
    
- Show examples for both cases.
    

---

## 💡 **Answer**

### 🔹 **Prevent Default Action**

- Some elements (like `<a>` and `<form>`) have built-in behaviours.
    
- Use **`event.preventDefault()`** to stop that behaviour.
    

```html
<a href="https://google.com" id="link">Click Me</a>

<script>
document.getElementById("link").addEventListener("click", (e) => {
  e.preventDefault(); // Prevents navigation
  console.log("Link clicked but not redirected!");
});
</script>
```

---

### 🔹 **Stop Event Propagation**

- Events **bubble up** the DOM tree by default.
    
- Use **`event.stopPropagation()`** to prevent parent handlers from firing.
    

```html
<div id="parent">
  <button id="child">Click</button>
</div>

<script>
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked!");
});

document.getElementById("child").addEventListener("click", (e) => {
  e.stopPropagation(); // Stops bubbling
  console.log("Button clicked!");
});
</script>
```

✔ Clicking the button logs **"Button clicked!"** but **not "Parent clicked!"**.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What is the difference between preventDefault() and stopPropagation()?**

#### ✅ **How to Answer in an Interview**

- **preventDefault()** → Stops browser’s default behaviour.
    
- **stopPropagation()** → Stops the event from bubbling to parent elements.
    

#### 💡 **Answer**

```js
e.preventDefault();   // Prevents default (e.g., form submit)
e.stopPropagation();  // Stops event from reaching parents
```

---

### **2️⃣ Can we stop capturing as well as bubbling?**

#### ✅ **How to Answer in an Interview**

- Yes, use **`stopPropagation()`** for both phases, or **`stopImmediatePropagation()`** to also stop other listeners on the same element.
    

#### 💡 **Answer**

```js
element.addEventListener("click", (e) => {
  e.stopImmediatePropagation(); // Stops everything
});
```

---

## 🎯 **Interview Tips**

✅ Always **give examples for both methods**, as beginners confuse them.  
✅ Mention **stopImmediatePropagation()** for advanced follow-ups.  
✅ Be ready for **questions about event bubbling & capturing (next topic)**.

Alright ✅ Moving to **Q4: What is event bubbling and event capturing?**

---

# **4️⃣ What is event bubbling and event capturing?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **events travel through the DOM in two phases – capturing (downwards) and bubbling (upwards)**.
    
- Make it clear **bubbling is the default phase**.
    
- Use **a simple parent-child example**.
    

---

## 💡 **Answer**

When an event occurs on a DOM element, it travels in two phases:

### 🔹 **Capturing Phase (Trickle Down)**

Event goes **from the root (document) → target element**.

### 🔹 **Bubbling Phase (Bubble Up)**

Event goes **from the target element → back to the root**.

By default, **event listeners work in the bubbling phase**, but you can listen in capturing phase by passing `true` as the third argument.

---

## 🧩 **Example**

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
document.getElementById("parent").addEventListener(
  "click",
  () => console.log("Parent"),
  true // capturing
);

document.getElementById("child").addEventListener(
  "click",
  () => console.log("Child")
);
</script>
```

✔ Output (on clicking button):

```
Parent  (capturing phase)
Child
Parent  (bubbling phase)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How do you listen to events in the capturing phase?**

#### ✅ **How to Answer in an Interview**

- Pass `true` as the third parameter in `addEventListener`.
    

#### 💡 **Answer**

```js
element.addEventListener("click", handler, true); // Capturing phase
element.addEventListener("click", handler, false); // Bubbling phase
```

---

### **2️⃣ Which phase is better for event delegation?**

#### ✅ **How to Answer in an Interview**

- Event delegation usually **works in the bubbling phase** because most listeners default to it.
    

#### 💡 **Answer**

Bubbling phase is better for delegation because **events bubble up naturally to parent elements**.

---

## 🎯 **Interview Tips**

✅ Always **differentiate capturing vs bubbling clearly**.  
✅ Show **a code example where both phases fire**.  
✅ Be ready for follow-ups on **stopPropagation() and delegation**.

# **5️⃣ Explain event bubbling and event capturing with a practical example**

---

## ✅ **How to Answer in an Interview**

- First **briefly define bubbling and capturing**.
    
- Then **give a simple real-world example (nested elements)**.
    
- Show **how changing the third argument in `addEventListener` changes behaviour**.
    

---

## 💡 **Answer**

When a user clicks on a nested element, **the event first travels down (capturing phase)**, reaches the target, and then **bubbles up (bubbling phase)**.

### 🔹 **Capturing Phase** → Top → Target

### 🔹 **Bubbling Phase** → Target → Top

---

## 🧩 **Example**

```html
<div id="grandparent" style="padding:20px; background:#f99;">
  Grandparent
  <div id="parent" style="padding:20px; background:#9f9;">
    Parent
    <button id="child">Child</button>
  </div>
</div>

<script>
document.getElementById("grandparent").addEventListener(
  "click", () => console.log("Grandparent"), true // capturing
);
document.getElementById("parent").addEventListener(
  "click", () => console.log("Parent"), true
);
document.getElementById("child").addEventListener(
  "click", () => console.log("Child")
);
</script>
```

✔ If you click on **Child**, Output will be:

```
Grandparent  (capturing)
Parent       (capturing)
Child
Parent       (bubbling)
Grandparent  (bubbling)
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How can you stop event propagation in this example?**

#### ✅ **How to Answer in an Interview**

- Use `event.stopPropagation()` inside the child click handler.
    

#### 💡 **Answer**

```js
child.addEventListener("click", (e) => {
  e.stopPropagation();
  console.log("Child clicked");
});
```

✔ Now clicking **Child** will only log **"Child clicked"**.

---

### **2️⃣ Why does event delegation rely on bubbling?**

#### ✅ **How to Answer in an Interview**

- Because bubbling ensures that events **propagate to parent elements**, so a single parent listener can handle many child elements.
    

#### 💡 **Answer**

Instead of adding separate listeners to each button, **one parent listener can capture all clicks using bubbling**.

---

## 🎯 **Interview Tips**

✅ Always **show an example with nested elements**.  
✅ Show **actual console output order** for better understanding.  
✅ Be ready for **follow-ups on stopPropagation() and delegation**.

# **6️⃣ What is the difference between an event object and a custom event in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **an event object is automatically created when an event occurs**, while **a custom event is manually created using the `CustomEvent` constructor**.
    
- Clarify that **custom events are useful for component communication and custom logic**.
    
- Show examples for both.
    

---

## 💡 **Answer**

### 🔹 **Event Object**

- Created **automatically by the browser** when an event (click, keypress, etc.) occurs.
    
- Passed as a parameter to the event handler.
    

```js
button.addEventListener("click", (event) => {
  console.log(event.type); // "click"
});
```

---

### 🔹 **Custom Event**

- **Manually created and dispatched** using `new CustomEvent()` and `dispatchEvent()`.
    
- Used for **triggering custom logic** or **communication between components**.
    

```js
const customEvent = new CustomEvent("myEvent", { detail: { msg: "Hello" } });
document.addEventListener("myEvent", (e) => console.log(e.detail.msg));
document.dispatchEvent(customEvent); // "Hello"
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use a custom event?**

#### ✅ **How to Answer in an Interview**

- When you need **component-to-component communication**, or **trigger an event manually without a real user action**.
    

#### 💡 **Answer**

Custom events are useful for:  
✔ Component communication in vanilla JS apps  
✔ Triggering logic after API responses  
✔ Building event-driven systems

---

### **2️⃣ What is the difference between `dispatchEvent` and `triggering DOM events` like `click()`?**

#### ✅ **How to Answer in an Interview**

- `element.click()` triggers the default behaviour of a click.
    
- `dispatchEvent()` can **dispatch any event (custom or built-in)**.
    

#### 💡 **Answer**

```js
button.click(); // Triggers click handler + default action
button.dispatchEvent(new Event("click")); // Only triggers event listener
```

---

## 🎯 **Interview Tips**

✅ Always **explain that event object = automatic, custom event = manual**.  
✅ Show **a short code example for both**.  
✅ Be ready for follow-ups on **CustomEvent options (`detail`, `bubbles`, `cancelable`)**.

# **7️⃣ What is event delegation in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **event delegation is attaching a single event listener to a parent element to manage events on multiple child elements using event bubbling**.
    
- Explain **why it's efficient** (better performance, works for dynamically added elements).
    
- Give a **real-world example like handling clicks on a list of items**.
    

---

## 💡 **Answer**

**Event delegation** is a technique where **a single event listener is attached to a parent element**, and **events on its child elements are handled by checking `event.target`**.

### 🔹 **Why use it?**

✔ Reduces the number of event listeners (better memory usage).  
✔ Works for **elements added dynamically** after page load.

---

## 🧩 **Example**

```html
<ul id="menu">
  <li>Home</li>
  <li>About</li>
  <li>Contact</li>
</ul>

<script>
document.getElementById("menu").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Clicked:", e.target.textContent);
  }
});
</script>
```

✔ Instead of adding `click` to every `<li>`, we add **one listener to `<ul>`**.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is event delegation better than individual listeners?**

#### ✅ **How to Answer in an Interview**

- It **reduces memory usage** and **handles future dynamic elements** automatically.
    

#### 💡 **Answer**

- If we have 1000 `<li>` items, attaching 1000 listeners is inefficient.
    
- With delegation, **only 1 listener is needed**, saving memory and improving performance.
    

---

### **2️⃣ Does event delegation work with capturing phase?**

#### ✅ **How to Answer in an Interview**

- Yes, but **it's commonly used with bubbling**, because bubbling is default.
    

#### 💡 **Answer**

```js
parent.addEventListener("click", handler, true); // Capturing phase
parent.addEventListener("click", handler, false); // Bubbling phase
```

---

## 🎯 **Interview Tips**

✅ Always explain **benefits + real-world example (list items)**.  
✅ Mention that **event delegation relies on bubbling by default**.  
✅ Be ready for follow-ups on **dynamic DOM elements**.

# **8️⃣ What is Shadow DOM?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **Shadow DOM is a way to encapsulate a component’s DOM and CSS so they do not affect the rest of the page**.
    
- Mention that **it is commonly used in Web Components to create isolated, reusable elements**.
    
- Show **a small example of creating and attaching a Shadow DOM**.
    

---

## 💡 **Answer**

The **Shadow DOM** is a **separate, hidden DOM tree** attached to an element.  
It allows **encapsulation**, meaning the component’s HTML and CSS **do not leak out** or get affected by external styles.

✅ Used in **Web Components, custom elements, and frameworks like Angular/React internally**.

---

## 🧩 **Example**

```html
<div id="host"></div>

<script>
const host = document.getElementById("host");
const shadow = host.attachShadow({ mode: "open" }); // Create Shadow DOM
shadow.innerHTML = `<style>p { color: red; }</style><p>Hello Shadow DOM!</p>`;
</script>
```

✔ The `<p>` inside the shadow DOM will **always be red**, even if external CSS tries to change it.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ What are the benefits of Shadow DOM?**

#### ✅ **How to Answer in an Interview**

- Encapsulation – HTML & CSS are **isolated**.
    
- Reusability – Components **behave the same anywhere**.
    
- Avoids **style conflicts** with global CSS.
    

---

### **2️⃣ What are `open` and `closed` shadow roots?**

#### ✅ **How to Answer in an Interview**

- **open** → You can access the shadow DOM with `element.shadowRoot`.
    
- **closed** → `element.shadowRoot` returns `null`.
    

```js
host.attachShadow({ mode: "open" });   // Can access shadowRoot
host.attachShadow({ mode: "closed" }); // Can't access shadowRoot
```

---

## 🎯 **Interview Tips**

✅ Always mention **encapsulation of DOM & CSS**.  
✅ Give **real-world examples – Web Components, browser `<video>` controls use Shadow DOM**.  
✅ Be ready for **questions on open vs closed shadow roots**.

# **9️⃣ How do you detect browser or platform in JavaScript?**

---

## ✅ **How to Answer in an Interview**

- Start by saying that **browser detection is often done using `navigator.userAgent`, but feature detection is preferred over browser detection**.
    
- Mention **platform detection can also be done using `navigator.platform` or feature-based checks**.
    
- Show **examples for both browser and platform detection**.
    

---

## 💡 **Answer**

### 🔹 **Browser Detection (using userAgent)**

```js
const ua = navigator.userAgent;

if (ua.includes("Chrome")) console.log("Browser: Chrome");
else if (ua.includes("Firefox")) console.log("Browser: Firefox");
else console.log("Other Browser");
```

---

### 🔹 **Platform Detection**

```js
console.log("Platform:", navigator.platform); 
// e.g. "Win32", "MacIntel", "Linux x86_64"
```

---

### 🔹 **Preferred Method → Feature Detection**

✅ Instead of detecting the browser, check **if a feature is supported**:

```js
if ("geolocation" in navigator) {
  console.log("Geolocation supported");
}
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Why is feature detection better than browser detection?**

#### ✅ **How to Answer in an Interview**

- Because browser detection is **unreliable** (userAgent can be spoofed).
    
- Feature detection **works regardless of browser**.
    

---

### **2️⃣ How to detect if the user is on mobile or desktop?**

#### ✅ **How to Answer in an Interview**

- Use **userAgent matching** or **screen size detection**.
    

```js
if (/Mobi|Android/i.test(navigator.userAgent)) {
  console.log("Mobile device");
} else {
  console.log("Desktop");
}
```

---

## 🎯 **Interview Tips**

✅ Always mention that **feature detection is better** than browser detection.  
✅ Be ready for **follow-ups on responsive design techniques (CSS media queries)**.  
✅ Mention **`navigator` object properties (platform, userAgent)**.

# **🔟 What is layout thrashing?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining **layout thrashing happens when layout and style calculations are triggered repeatedly, causing performance issues**.
    
- Mention **it occurs when reading and writing DOM properties alternately**.
    
- Give **an example of bad code and how to optimize it**.
    

---

## 💡 **Answer**

**Layout thrashing** happens when **JavaScript forces the browser to recalculate styles and re-render the page repeatedly in a short time**.

- Occurs when **DOM reads and writes are mixed** (e.g., reading `offsetHeight` right after changing `style`).
    
- This causes **multiple reflows and repaints**, slowing down rendering.
    

---

## 🧩 **Example**

❌ **Bad (Causes Thrashing)**

```js
for (let i = 0; i < 100; i++) {
  box.style.width = i + "px";          // Write
  console.log(box.offsetHeight);       // Read → Forces layout recalculation
}
```

✔ **Good (Optimized)**

```js
const height = box.offsetHeight; // Read once
for (let i = 0; i < 100; i++) {
  box.style.width = i + "px"; // Write after reading
}
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ How can you avoid layout thrashing?**

#### ✅ **How to Answer in an Interview**

- Batch DOM reads together and writes together.
    
- Use `requestAnimationFrame()` for animations.
    
- Use CSS transitions instead of frequent JS updates.
    

---

### **2️⃣ What are reflow and repaint?**

#### ✅ **How to Answer in an Interview**

- **Reflow (layout)** – When the browser recalculates element positions/sizes.
    
- **Repaint** – When visual parts (like colors) change but layout stays the same.
    

---

## 🎯 **Interview Tips**

✅ Always **show a bad vs good code example**.  
✅ Mention that **DOM reads after writes cause forced reflow**.  
✅ Be ready for follow-ups on **reflow vs repaint vs composite**.

# **1️⃣1️⃣ What are the stages of the render pipeline?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **the render pipeline is the process the browser follows to display a page after changes to HTML/CSS/JS**.
    
- Explain **each stage (style, layout, paint, composite)** in simple terms.
    
- Show **a small diagram-like breakdown** for beginners.
    

---

## 💡 **Answer**

When the browser renders a page, it goes through these stages:

1️⃣ **Style (Recalculate Styles)** – Determine computed styles from CSS rules.  
2️⃣ **Layout (Reflow)** – Calculate element positions and sizes.  
3️⃣ **Paint** – Fill pixels (colors, borders, text) on layers.  
4️⃣ **Composite** – Combine layers into the final screen image.

---

## 🧩 **Example Flow**

```plaintext
HTML/CSS Change
   ↓
Recalculate Style → Layout → Paint → Composite → Screen
```

✅ Not every change goes through all steps:

- Changing **color** → Paint + Composite only
    
- Changing **width/height** → Layout + Paint + Composite
    

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Which stage is most expensive?**

#### ✅ **How to Answer in an Interview**

- **Layout (Reflow)** is usually the most expensive because it recalculates element positions and sizes.
    

---

### **2️⃣ How can you improve performance?**

#### ✅ **How to Answer in an Interview**

- Minimize layout changes (batch DOM updates).
    
- Use CSS transforms instead of changing layout properties like `top`, `left`.
    
- Avoid layout thrashing (read/write in correct order).
    

---

## 🎯 **Interview Tips**

✅ Always **list all four stages in order**.  
✅ Mention that **not all changes go through all stages**.  
✅ Be ready for follow-ups on **layout thrashing & expensive operations**.

# **1️⃣2️⃣ What is script execution order in browsers?**

---

## ✅ **How to Answer in an Interview**

- Start by explaining that **browsers execute scripts in the order they appear in HTML unless attributes like `async` or `defer` are used**.
    
- Clarify the difference between **normal scripts, async scripts, and defer scripts**.
    
- Use a table for better understanding.
    

---

## 💡 **Answer**

By default, **scripts are executed in the order they appear in HTML**, and **HTML parsing is blocked until the script finishes**.

|Attribute|Loading|Execution|Blocks HTML Parsing?|
|---|---|---|---|
|**Normal**|Immediately|As soon as downloaded|✅ Yes|
|**async**|Parallel|Immediately after download|❌ No|
|**defer**|Parallel|After HTML is parsed|❌ No|

---

## 🧩 **Example**

```html
<!-- Normal script: blocks HTML parsing -->
<script src="script1.js"></script>

<!-- async: loads parallel, executes immediately -->
<script src="script2.js" async></script>

<!-- defer: loads parallel, executes after parsing -->
<script src="script3.js" defer></script>
```

---

# 🔄 **Trailing Questions**

---

### **1️⃣ Which attribute should you use for scripts that depend on DOM?**

#### ✅ **How to Answer in an Interview**

- Use **`defer`** so the script runs **after HTML parsing**.
    

---

### **2️⃣ Which attribute is best for analytics or ads?**

#### ✅ **How to Answer in an Interview**

- Use **`async`** because such scripts are **independent and don’t need to wait for HTML parsing**.
    

---

## 🎯 **Interview Tips**

✅ Always **compare normal, async, defer in a table**.  
✅ Mention **defer preserves execution order, async does not**.  
✅ Be ready for follow-ups on **performance best practices for loading scripts**.

# **1️⃣3️⃣ What is CSS containment and how does it affect painting?**

---

## ✅ **How to Answer in an Interview**

- Start by saying **CSS containment is a feature that allows developers to limit a DOM element’s scope of layout, style, and paint calculations**.
    
- Explain that **using containment helps browsers optimize rendering performance**.
    
- Show how it **reduces unnecessary reflows and repaints**.
    

---

## 💡 **Answer**

**CSS Containment (`contain` property)** tells the browser that an element is **independent of the rest of the page**, so changes inside it **won’t affect outside elements**.

### 🔹 **Benefits**

✅ Prevents unnecessary layout recalculations for unrelated elements.  
✅ Improves rendering performance in large web apps.

---

### 🔹 **Types of Containment**

|Value|Effect|
|---|---|
|`contain: layout`|Prevents element from affecting page layout outside|
|`contain: paint`|Restricts painting to within the element|
|`contain: size`|Forces fixed size (doesn't depend on children)|
|`contain: content`|Combines layout, style, and paint isolation|

---

## 🧩 **Example**

```css
.card {
  contain: layout paint; 
  width: 200px;
  height: 150px;
  overflow: auto;
}
```

✔ Now, changes inside `.card` (like adding elements) **won’t trigger re-layout for the entire page**.

---

# 🔄 **Trailing Questions**

---

### **1️⃣ When should you use CSS containment?**

#### ✅ **How to Answer in an Interview**

- When working with **complex components**, like infinite scroll lists, dashboards, or reusable widgets.
    

---

### **2️⃣ How does containment improve performance?**

#### ✅ **How to Answer in an Interview**

- It **reduces reflow and repaint scope**, so the browser **only recalculates the contained element instead of the whole page**.
    

---

## 🎯 **Interview Tips**

✅ Always **mention performance benefits**.  
✅ Give **a practical example (cards, widgets)**.  
✅ Be ready for follow-ups on **relation to layout thrashing and render pipeline**.

--------------------------------------------------------------------------

# DOM & Frontend Concepts – JavaScript Interview Prep

Below are detailed explanations for each question from the "DOM & Frontend Concepts" section. Each question includes practical code examples, “what to say” in an interview, and multiple trailing questions—with their answers—following the same beginner-friendly approach.

## 1. What is the Document Object Model (DOM), and how does JavaScript interact with it?

**Explanation:**  
The DOM is a tree-like structure representing every element on a web page as objects, so that JavaScript and other languages can read and change the structure, style, or content of the page.

JavaScript interacts with the DOM to dynamically update content, style, structure, or respond to user actions.

**Example:**

javascript

`document.getElementById("main-title").textContent = "Hello, JavaScript!";`

This code finds an HTML element with the id "main-title" and changes its text content.

**What to say in an interview:**  
"The DOM is a programming interface for web pages, letting me use JavaScript to read, update, or modify elements and their content on the fly."

## Trailing Question: How can you select elements in the DOM using JavaScript?

**Answer:**  
You can use:

- `getElementById("id")` – selects one element by ID.
    
- `getElementsByClassName("className")` – selects all elements with a given class.
    
- `getElementsByTagName("tagname")` – selects all elements with the tag.
    
- `querySelector("selector")` – selects the first matching element (supports CSS selectors).
    
- `querySelectorAll("selector")` – selects all elements matching the CSS selector.
    

**Example:**

javascript

`let firstButton = document.querySelector('button'); let allParagraphs = document.querySelectorAll('p');`

**What to say:**  
"I use methods like `getElementById`, `querySelector`, or `querySelectorAll` to select elements from the DOM for manipulation."

## Trailing Question: What happens if you try to select an element that doesn't exist?

**Answer:**  
Selecting a non-existent element returns `null` (for single selectors) or an empty collection (for multiple selectors). Trying to access properties on `null` will trigger an error.

**Example:**

javascript

`let el = document.getElementById('does-not-exist'); // null`

**What to say:**  
"If I try to select an element not on the page, I get `null`. It’s good practice to check for null before using the element in code."

## 2. How do you render HTML elements dynamically in JavaScript or React?

**Explanation:**  
Rendering elements dynamically means creating, modifying, or removing elements in the DOM using JavaScript (vanilla JS or libraries like React).

**In plain JavaScript:**

javascript

`let newItem = document.createElement('li'); newItem.textContent = "Learn DOM!"; document.getElementById('todo-list').appendChild(newItem);`

**In React (JSX syntax):**

jsx

`function MyComponent() {   return <div>{Math.random()}</div>; }`

**What to say in an interview:**  
"In JavaScript, I can create and add elements using DOM methods like `createElement` and `appendChild`. In React, I return elements from functions via JSX, and the virtual DOM handles the updates efficiently."

## Trailing Question: Why might you prefer React or other libraries for dynamic rendering versus vanilla JavaScript?

**Answer:**  
Libraries like React provide a virtual DOM, making updates more efficient and predictable, support reusable components, and improve code maintainability, especially in large-scale applications.

**What to say:**  
"React makes dynamic rendering more maintainable at scale by using components and automatic interface updates, so I write less code and handle complex UIs more easily."

## Trailing Question: What is the virtual DOM?

**Answer:**  
The virtual DOM is an in-memory representation of the actual DOM. Changes are computed efficiently, and only the differences are updated in the real DOM. This speeds up user interfaces and minimizes unnecessary changes.

**What to say:**  
"The virtual DOM lets React figure out what’s changed before touching the actual DOM, which makes updates faster and more efficient."

## 3. How do you prevent default actions and stop event propagation in JavaScript?

**Explanation:**

- To stop an event’s default action (like a link navigating away or a form submitting), use `event.preventDefault()`.
    
- To stop an event from bubbling up the DOM tree (affecting parent elements), use `event.stopPropagation()`.
    

**Example:**

javascript

`document.querySelector('a').addEventListener('click', function(event) {   event.preventDefault();      // Prevents the link's default behavior  event.stopPropagation();     // Stops the event from bubbling up  alert('Clicked, but not redirecting!'); });`

**What to say in an interview:**  
"I use `preventDefault()` to stop actions like form submits, and `stopPropagation()` to prevent the event from reaching parent elements."

## Trailing Question: When would you want to use stopPropagation?

**Answer:**  
Use `stopPropagation()` when you have nested event listeners and want to ensure only the innermost listener handles the event, not its parents.

**Example:**

javascript

`parentDiv.addEventListener('click', () => alert('parent!')); childDiv.addEventListener('click', (event) => {   event.stopPropagation();  alert('child!'); });`

**What to say:**  
"I use `stopPropagation()` if both a child and its parent element have click handlers, but I only want the child’s handler to run when it’s clicked."

## 4. What is event bubbling and event capturing?

**Explanation:**

- **Event bubbling:** Events start at the innermost element you clicked and bubble up to the root (`document`), triggering any listeners along the way.
    
- **Event capturing:** The event starts from the outermost element and goes down to the innermost target before bubbling back up.
    

**Example:**

javascript

`// Bubbling document.body.addEventListener('click', () => alert('body!')); document.getElementById('btn').addEventListener('click', () => alert('button!'));`

Click the button, and both alerts fire—first button (target), then body (bubble).

**What to say in an interview:**  
"In event bubbling, events go from the target element up to the root. In capturing, they go from the root down to the target. By default, most browsers use bubbling."

## Trailing Question: How do you listen to events in the capturing phase?

**Answer:**  
You can add a third parameter to `addEventListener` and set it to `true` to listen during the capturing phase.

javascript

`element.addEventListener('click', handler, true);`

**What to say:**  
"I set the third argument of `addEventListener` to `true` to catch events during the capturing phase instead of bubbling."

## 5. What is event delegation in JavaScript?

**Explanation:**  
Event delegation is attaching a single event listener to a parent element, rather than many listeners to individual child elements, and using `event.target` to determine which child triggered the event.

**Example:**

javascript

`document.getElementById('list').addEventListener('click', function(event) {   if (event.target.tagName === 'LI') {    alert('List item clicked: ' + event.target.textContent);  } });`

**What to say in an interview:**  
"Event delegation saves memory and makes it easier to handle events on elements created in the future by attaching a handler to a common parent."

## Trailing Question: Why is event delegation useful?

**Answer:**  
You avoid attaching listeners to each child; new child elements added later also work automatically. This improves performance and code simplicity.

**What to say:**  
"It's useful for handling events efficiently, especially with lots of similar items or when elements are dynamically added or removed."

## 6. What is the difference between an event object and a custom event in JavaScript?

**Explanation:**

- An **event object** is automatically passed to event handlers and describes the event (e.g., type, target).
    
- A **custom event** is one you define yourself (using `CustomEvent`) to signal that something special happened in your code.
    

**Examples:**

javascript

`// Native event object button.addEventListener('click', function(event) {   console.log(event.type); // 'click' }); // Custom event let custom = new CustomEvent('hello', { detail: { name: "Alice" } }); element.dispatchEvent(custom); element.addEventListener('hello', function(e) {   alert(e.detail.name); // "Alice" });`

**What to say in an interview:**  
"The event object tells me about the event, like what was clicked. A custom event lets me define my own application-specific triggers for communication between code modules."

## Trailing Question: When should you use custom events?

**Answer:**  
Use custom events to communicate between components, or broadcast state changes, especially in large or modular applications.

**What to say:**  
"I use custom events to help different parts of my app communicate without being tightly coupled, making the code more modular and maintainable."

If you'd like to continue through further sections or go deeper on any topic, let me know!