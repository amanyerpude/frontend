
- what are key-events how to create a custom event 
- difference between options api and composition api
- ref, reactive, watcher, computed
- life cycle hooks
- directives
- events modifiers
- key-events
- what is v-model what all modifiers we use with it
- what are components 
- how do we communicate with components.
- what are vue.js features

### **1️⃣ Vue.js Basics**

- What is vue.js?
    
- What is a progressive framework?
    
- What is a component-based architecture?
    
- What are single-file components?
    
- What is `.vue` file?
    
- What is ‘new vue’?
    
- What is Single Page Application? Does vue.js belong to single page applications?
    

---

### **2️⃣ Vue.js Components & Templates**

- What are components?
    
- What are dynamic components?
    
- What is a template?
    
- What are vue.js forms? What are form input bindings?
    
- Explain templates?
    
- What is vue.js component? Write an example for the same.
    

---

### **3️⃣ Vue.js Data Binding & Reactivity**

- What is binding? How do you bind HTML classes and inline styles?
    
- What is v-bind and v-model?
    
- What is one-way and two-way data binding? Give examples.
    
- What is interpolation and binding expression?
    
- What is a reactive interface?
    

---

### **4️⃣ Vue.js Events & Lifecycle**

- Explain vue.js events. What is a click event?
    
- What are event modifiers? What are event-key modifiers?
    
- What are the lifecycle hooks of vue.js?
    
- Explain the component life cycle hooks.
    
- What is watch property?
    

---

### **5️⃣ Vue.js Routing & State Management**

- What is routing? How to use routing? How routing works in vue.js?
    
- How routers work? Write code snippet for 5 modules.
    
- What is vuex and mixins?
    
- How to share data between components?
    

---

### **6️⃣ Vue.js Performance & Deployment**

- How can you improve performance in vue.js?
    
- How to deploy vue.js applications?
    

---

### **7️⃣ Vue.js API Handling (Axios / Fetch / REST)**

- What is axios.js?
    
- Explain axios. How axios gives better support for vue?
    
- How to handle REST API calls in vue.js? Write an example.
    
- How to fetch data from API using vue.js?
    
- Create a CRUD application in vue.js (GET, POST, PUT, DELETE).
    
- Can you write a sample code snippet to access all REST operations?
    
- How to handle a CORS policy issue? Write code.
    
- http vs https? How do you handle REST API calls?
    
- Write code: Axios vs Fetch – which one is faster/safe/efficient?
    

---

### **8️⃣ Vue.js Project & Debugging**

- Explain your current project.
    
- Explain all the modules of the project you contributed to.
    
- How many components you created for the project?
    
- How vue.js components are changed to HTML file and viewed in browser?
    
- Can we debug vue.js apps in VS Code or any other IDE?
    
- What are the positives of debugging vue.js code in browser vs IDE?
    
- Building vue.js projects vs plain JavaScript/jQuery – which is easier? Why?

### **Vue.js Concepts & Features**

15. How do you communicate between Vue components?  
    Write a suitable example.
    
16. How do routers work? Write a code snippet for 5 modules.
    
17. What is a filter? What filters are available in Vue?
    
18. How to handle decimal points in Vue?
    
19. You are given a project on handling videos using Vue.js.  
    How would you handle it? Write code.
    
20. How are Vue.js components converted to HTML files and viewed in the browser?
    
21. I want to write a code for a button callback in a Vue project, but the code should be in JavaScript.  
    How would you handle it?

--------------------------------------------------------------------------


# **1. What is Vue.js?**

## How to Answer in an Interview

Start by mentioning that Vue.js is a **progressive JavaScript framework** used to build user interfaces, particularly **Single Page Applications (SPAs)**. Highlight that it is **easy to learn**, **component-based**, and **flexible**, making it popular for small to large-scale projects.

---

## Answer

Vue.js is a **progressive, open-source JavaScript framework** for building **user interfaces and single-page applications**. It focuses on the **view layer (the “V” in MVC)** but can be extended with official libraries for routing (`vue-router`) and state management (`vuex`) to build complex applications.

It is designed to be **incrementally adoptable**, meaning developers can start with just a script tag for small projects or use a full build setup (via Vue CLI or Vite) for enterprise apps.

### **Key Features**

- ✅ **Reactive Data Binding** – Automatically updates the DOM when data changes.
    
- ✅ **Component-Based Architecture** – UI is divided into small, reusable components.
    
- ✅ **Declarative Rendering** – Uses templates with directives (`v-bind`, `v-if`, etc.).
    
- ✅ **Progressive Nature** – You can start small and scale up as needed.
    

---

## Example

```html
<div id="app">
  <p>{{ message }}</p>
  <button @click="message = 'Hello from Vue.js!'">Click Me</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      message: 'Welcome to Vue.js!'
    }
  });
</script>
```

---

# **Trailing Questions**

---

## **1️⃣ Why is Vue called a “progressive framework”?**

### How to Answer in an Interview

Explain that Vue is designed for **incremental adoption**, meaning developers can use it as a small library or scale it to a full-fledged framework with routing, state management, and build tools.

---

### Answer

Vue is called a **progressive framework** because it allows developers to **start small and gradually add features as needed**. For example, you can begin by simply including Vue via a `<script>` tag to enhance parts of a webpage. Later, you can add **Vue Router** for navigation, **Vuex/Pinia** for state management, and a build setup like **Vite or Vue CLI** for larger applications.

This approach makes Vue highly flexible and beginner-friendly, unlike frameworks that require full setup from the start.

---

### Example

```html
<!-- Start small -->
<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>

<!-- Scale up later with a CLI-based project -->
vue create my-project
```

---

### Interview Tips

- Use the keywords **“incremental adoption”** and **“flexible scaling”**.
    
- Contrast it briefly with Angular/React setups that often require more boilerplate.
    

---

## **2️⃣ Is Vue.js an MVC framework?**

### How to Answer in an Interview

Clarify that Vue is **not a full MVC framework**, but it can integrate with tools to achieve similar architecture.

---

### Answer

Vue.js is **not a full MVC framework**. It focuses on the **View layer** and provides a way to build UI declaratively with components and reactive data binding. However, Vue can be combined with **Vuex/Pinia** for state (Model) and **Vue Router** for navigation (Controller-like role).

This modular approach gives developers flexibility without enforcing a rigid structure like MVC frameworks.

---

### Example

- **Model (State)** → Managed using `data`, `ref`, or Vuex/Pinia.
    
- **View (Template)** → Defined in `.vue` files using HTML-based templates.
    
- **Controller (Logic)** → Written as methods and lifecycle hooks.
    

---

### Interview Tips

- Emphasize that Vue is **View-focused**, not opinionated like Angular.
    
- Show that you understand **how Vue can mimic MVC when needed**.
    

---

## **3️⃣ What companies use Vue.js?**

### How to Answer in an Interview

Highlight **industry adoption** to show that Vue is used in production by well-known companies.

---

### Answer

Vue.js is used by many **large-scale companies and startups** because of its lightweight nature and fast learning curve. Some well-known companies using Vue include:

- ✅ **Alibaba** – E-commerce platform.
    
- ✅ **Xiaomi** – Smart devices and web apps.
    
- ✅ **GitLab** – Entire UI is built with Vue.
    
- ✅ **Grammarly** – Uses Vue for parts of its web interface.
    
- ✅ **Behance (Adobe)** – Creative portfolio platform.
    

This shows that Vue is **production-ready and scalable** for enterprise applications.

---

### Interview Tips

- Mention at least 2–3 companies.
    
- If you’ve personally used Vue in projects, briefly highlight that experience.
    

---
# **2. What is a Progressive Framework?**

## How to Answer in an Interview

Explain that a progressive framework is **designed to be adopted gradually**—developers can start small with basic features and scale up to advanced capabilities as the project grows. Relate it specifically to **Vue.js**, since this term is central to its philosophy.

---

## Answer

A **progressive framework** is a framework that can be **incrementally adopted**, meaning you can start with just its core features and later add more advanced capabilities like routing, state management, and build tooling as your project grows.

In the context of Vue.js:

- You can use Vue as a **simple library** by adding a `<script>` tag to enhance a webpage.
    
- For bigger applications, you can **add Vue Router, Vuex/Pinia, and build tools** to create a complete Single Page Application (SPA).
    

This approach makes Vue flexible and beginner-friendly compared to more opinionated frameworks that require a full setup from the beginning (like Angular).

---

## Example

```html
<!-- Step 1: Start small by including Vue via CDN -->
<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>

<!-- Step 2: Scale up with CLI-based project -->
npm install -g @vue/cli
vue create my-project
```

This example shows how you can **start small** and **progressively adopt advanced features** like routing or state management as the application grows.

---

# **Trailing Questions**

---

## **1️⃣ Why is incremental adoption important for Vue.js?**

### How to Answer in an Interview

Explain that incremental adoption lowers the learning curve and makes Vue suitable for both small and large projects.

---

### Answer

Incremental adoption is crucial because it **lowers the barrier to entry**. Developers can quickly add Vue to existing pages without changing the entire codebase. As project requirements grow, they can gradually add features like routing and state management.

This flexibility makes Vue suitable for:

- ✅ **Small-scale widgets** embedded in existing apps.
    
- ✅ **Large enterprise SPAs** with complex state and navigation.
    

---

### Example

- A company might first use Vue to add a small interactive form to an existing site.
    
- Later, as requirements grow, the same app can evolve into a full SPA with Vue Router and Vuex.
    

---

### Interview Tips

- Use **real-world scenarios** to show you understand incremental adoption.
    
- Emphasize how this is different from frameworks that require full setup upfront.
    

---

## **2️⃣ How is Vue different from Angular in terms of progressiveness?**

### How to Answer in an Interview

Compare Vue's flexibility with Angular's all-in-one structure.

---

### Answer

Vue is **progressive** because it lets developers adopt it **step by step**, while Angular is **opinionated** and expects developers to follow its complete framework structure from the start.

- **Vue** → Start with a script tag, then scale up with Vue Router and Vuex as needed.
    
- **Angular** → Requires TypeScript, CLI setup, and a predefined architecture from day one.
    

This makes Vue **lighter, easier to learn**, and more adaptable to existing projects.

---

### Interview Tips

- Always use keywords like **“flexible”, “incremental adoption”, “scalable”**.
    
- Show that you understand **the practical advantages of Vue over Angular**.
    

---

## **3️⃣ Can React also be called a progressive framework?**

### How to Answer in an Interview

Point out similarities and differences between React and Vue in this regard.

---

### Answer

React is **not officially called a progressive framework**, but it also offers incremental adoption. Like Vue, React can be added to existing apps via a `<script>` tag or built with tools like Create React App.

However, Vue places more emphasis on **being beginner-friendly out of the box**, with a template-based approach and a complete ecosystem (Router, Vuex/Pinia). React relies on third-party libraries for many features.

---

### Interview Tips

- Keep the comparison neutral; **don’t bash React**.
    
- Focus on **Vue’s simplicity and flexibility** as its biggest advantage.
    

---

# **3. What is a Component-Based Architecture?**

## How to Answer in an Interview

Explain that in component-based architecture, the UI is **broken into reusable, self-contained components**, each managing its own logic, template, and styling. Show how this approach improves **modularity, reusability, and maintainability**, which is a core principle of Vue.js.

---

## Answer

A **component-based architecture** is a design pattern where the application UI is divided into **independent, reusable pieces called components**. Each component:

- Encapsulates its **own logic, template (HTML), and style (CSS)**.
    
- Can be **reused across multiple parts of the application**.
    
- Communicates with other components via **props (input) and events (output)**.
    

Vue.js uses component-based architecture to create **modular, maintainable, and scalable applications**. It also supports **Single File Components (SFCs)** (`.vue` files) that combine template, script, and style in a single file.

---

### **Benefits of Component-Based Architecture**

✅ **Reusability** – Write once, use anywhere.  
✅ **Maintainability** – Each component is small and easier to debug.  
✅ **Scalability** – Ideal for large apps by breaking UI into manageable units.  
✅ **Consistency** – Promotes a standard structure for the app UI.

---

## Example

### **Parent Component (App.vue)**

```vue
<template>
  <div>
    <h1>My Vue App</h1>
    <HelloWorld msg="Welcome to Component-Based Architecture!" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  components: { HelloWorld }
}
</script>
```

### **Child Component (HelloWorld.vue)**

```vue
<template>
  <p>{{ msg }}</p>
</template>

<script>
export default {
  props: ['msg']
}
</script>
```

✅ Here, `HelloWorld` is a **reusable component** that takes `msg` as a prop.

---

# **Trailing Questions**

---

## **1️⃣ Why is component-based architecture better than traditional MVC templates?**

### How to Answer in an Interview

Focus on **reusability, scalability, and maintainability** as the key benefits.

---

### Answer

Component-based architecture is better than traditional MVC templates because it **encourages reusability and modularity**. Instead of having all logic and UI in large monolithic files, components separate concerns into smaller, self-contained units.

This results in:

- **Cleaner code** → Easier to debug and maintain.
    
- **Reusability** → The same component can be used in multiple places.
    
- **Scalability** → Large apps can be built as collections of smaller parts.
    

In contrast, traditional MVC templates often lead to **tightly coupled code**, making changes harder as the app grows.

---

### Example

- A **button component** (`BaseButton.vue`) can be reused across forms, modals, and dialogs by simply changing its props.
    
- In MVC templates, you’d likely duplicate button HTML and event handling logic in multiple files.
    

---

### Interview Tips

- Always mention **separation of concerns and reusability**.
    
- Relate the concept directly to Vue Single File Components.
    

---

## **2️⃣ How do components communicate in Vue.js?**

### How to Answer in an Interview

Explain the **parent-to-child (props)** and **child-to-parent (events)** communication pattern.

---

### Answer

Components in Vue communicate mainly in two ways:

1. **Parent → Child (Props)** – Data is passed down as properties.
    
2. **Child → Parent (Events)** – The child emits events that the parent listens for.
    

For complex apps, **state management tools like Vuex or Pinia** are used to share data between multiple components.

---

### Example

```vue
<!-- Parent.vue -->
<ChildComponent :message="parentMessage" @update="handleUpdate" />
```

```vue
<!-- ChildComponent.vue -->
<template>
  <button @click="$emit('update', 'New Value')">{{ message }}</button>
</template>
<script>
export default { props: ['message'] }
</script>
```

---

### Interview Tips

- Mention **props and events** as the primary mechanism.
    
- Add that Vue 3 Composition API also allows **provide/inject** for deeper hierarchies.
    

---

## **3️⃣ What are Single File Components (SFCs) and how do they relate to this architecture?**

### How to Answer in an Interview

Show that SFCs are the **best way to implement component-based architecture in Vue**.

---

### Answer

Single File Components (`.vue` files) are the **building blocks of component-based architecture in Vue.js**. They allow developers to **write template, script, and style in a single file**, keeping everything related to a component in one place.

This structure makes components **modular, reusable, and easy to maintain**.

---

### Example

```vue
<template>
  <button @click="count++">Clicked {{ count }} times</button>
</template>

<script>
export default {
  data() {
    return { count: 0 }
  }
}
</script>

<style>
button { background-color: blue; color: white; }
</style>
```

---

### Interview Tips

- Mention that **SFCs are compiled into JavaScript at build time**.
    
- Emphasize **how SFCs enforce component encapsulation**.
    

---
# **5. What is a `.vue` File?**

## How to Answer in an Interview

Explain that a `.vue` file is a **Single-File Component (SFC)** that contains **template, logic, and style** in a single file. Clarify that it is compiled at build time into JavaScript and plays a central role in Vue's component-based architecture.

---

## Answer

A `.vue` file is the **default file format for Vue Single-File Components (SFCs)**. It allows developers to **define the component’s HTML template, JavaScript logic, and CSS styles** in one file.

When a `.vue` file is compiled (using Vue CLI or Vite), it is **transformed into a JavaScript render function** that Vue can efficiently render in the browser.

### **Structure of a `.vue` File:**

1️⃣ **`<template>`** – Defines the HTML structure of the component.  
2️⃣ **`<script>`** – Contains the component logic (data, props, methods, lifecycle hooks).  
3️⃣ **`<style>`** – Contains CSS (can be global or scoped).

---

### **Benefits of `.vue` Files**

✅ Encapsulation → Everything for a component is in one place.  
✅ Scoped CSS → Prevents style conflicts.  
✅ Build Tooling Support → Works with Vite, Vue CLI, TypeScript, SCSS, etc.  
✅ Better IDE Support → Syntax highlighting, auto-completion, and linting.

---

## Example

### **ButtonComponent.vue**

```vue
<template>
  <button @click="count++">Clicked {{ count }} times</button>
</template>

<script>
export default {
  data() {
    return { count: 0 }
  }
}
</script>

<style scoped>
button {
  background-color: #42b983;
  color: white;
  padding: 10px;
  border-radius: 5px;
}
</style>
```

✅ Here, **HTML (template)**, **JS logic (script)**, and **CSS (style)** are all inside a single `.vue` file.

---

# **Trailing Questions**

---

## **1️⃣ How is a `.vue` file processed during build?**

### How to Answer in an Interview

Show that you understand the **compilation process**.

---

### Answer

A `.vue` file is **compiled by build tools (Vue Loader with Webpack or Vite)** into a JavaScript render function.

- The **`<template>`** is compiled into efficient **virtual DOM render functions**.
    
- The **`<script>`** is converted into a standard JS module.
    
- The **`<style>`** is extracted and scoped (if `scoped` is used).
    

This process ensures Vue apps are **optimized for performance and browser compatibility**.

---

### Example

When using Vue CLI or Vite:

```
npm run build
```

The `.vue` files are converted into **JavaScript bundles** that the browser can execute.

---

### Interview Tips

- Use terms like **"compiled into render functions"** and **"virtual DOM"**.
    
- Highlight that Vue **does not run `.vue` files directly in the browser**—they must be built first.
    

---

## **2️⃣ What is the difference between a `.vue` file and a normal `.js` file?**

### How to Answer in an Interview

Clarify that `.vue` is a **component file**, while `.js` files are logic modules.

---

### Answer

- A `.vue` file defines **a single UI component**, containing its template, logic, and style.
    
- A `.js` file contains **only logic (functions, classes, exports)** and does not define a template or styles.
    

In larger projects, `.vue` files are **imported into a root component or router**, while `.js` files are used for utilities, store modules, or composables.

---

### Example

```js
// helper.js
export function add(a, b) {
  return a + b
}
```

```vue
<!-- MyComponent.vue -->
<template><p>{{ add(2,3) }}</p></template>
<script>
import { add } from './helper.js'
export default { methods: { add } }
</script>
```

---

### Interview Tips

- Stress that `.vue` is **specific to Vue components**, whereas `.js` is for general logic.
    

---

## **3️⃣ Can we use TypeScript or SCSS in a `.vue` file?**

### How to Answer in an Interview

Show that `.vue` supports advanced features with build tools.

---

### Answer

Yes. By adding the `lang` attribute to `<script>` or `<style>`, we can use **TypeScript, SCSS, LESS, or other preprocessors** inside `.vue` files.

---

### Example

```vue
<script lang="ts">
export default {
  data(): { count: number } {
    return { count: 0 }
  }
}
</script>

<style lang="scss" scoped>
button { background: blue; }
</style>
```

✅ This gives **type safety and powerful CSS features** while keeping everything inside one file.

---

# **6. What is `new Vue`?**

## How to Answer in an Interview

Explain that `new Vue()` was the way to **create a root Vue instance in Vue 2**, which controls a specific part of the DOM. In Vue 3, this approach was replaced with `createApp()`. Mention its role in **initializing the Vue application**.

---

## Answer

In **Vue 2**, `new Vue()` is used to **create a root Vue instance** that connects Vue to the DOM and manages the application’s data, methods, and template.

This instance acts as the **entry point of the application** and controls everything inside the element specified by `el` or `mount()`.

In **Vue 3**, the `new Vue()` syntax was replaced by the **Composition API’s `createApp()` method**, which is more flexible and modular.

---

### **Key Responsibilities of `new Vue()` (Vue 2)**

✅ Initializes the Vue instance.  
✅ Connects Vue to a DOM element via the `el` option.  
✅ Manages data, methods, lifecycle hooks, and template rendering.

---

## Example (Vue 2)

```html
<div id="app">
  <p>{{ message }}</p>
  <button @click="changeMessage">Click Me</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
<script>
new Vue({
  el: "#app",
  data: {
    message: "Hello Vue!"
  },
  methods: {
    changeMessage() {
      this.message = "You clicked the button!";
    }
  }
});
</script>
```

✅ The `new Vue()` instance **controls everything inside `#app`**.

---

## Example (Vue 3 Equivalent)

```javascript
import { createApp } from "vue";
import App from "./App.vue";

createApp(App).mount("#app");
```

✅ In Vue 3, we use `createApp()` instead of `new Vue()`.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between `new Vue()` and `createApp()`?**

### How to Answer in an Interview

Show that you understand **Vue 2 vs Vue 3 changes**.

---

### Answer

|Feature|Vue 2 (`new Vue()`)|Vue 3 (`createApp()`)|
|---|---|---|
|App Initialization|Uses `new Vue()`|Uses `createApp()`|
|Multiple App Instances|Harder to manage|Easier to create multiple apps|
|Plugins & Config|Global configuration|App-level configuration|

In Vue 3, `createApp()` provides **better modularity and multiple app instance support**, whereas `new Vue()` is tied to a single root instance.

---

### Example

```javascript
// Vue 2
new Vue({ el: '#app', data: { msg: 'Hello' } });

// Vue 3
const app = createApp(App);
app.mount('#app');
```

---

### Interview Tips

- Always mention **Vue 3 uses `createApp()`**.
    
- If asked about migration, note that Vue 3 modularizes app-level configs.
    

---

## **2️⃣ Can you have multiple Vue instances on the same page?**

### How to Answer in an Interview

Explain that **both Vue 2 and Vue 3 support multiple instances**, but Vue 3 handles it better.

---

### Answer

Yes, you can create multiple Vue instances on the same page:

- In Vue 2, you can call `new Vue()` multiple times, each with a different `el`.
    
- In Vue 3, `createApp()` makes it **easier and more modular** to have multiple apps.
    

---

### Example

```html
<div id="app1">{{ msg }}</div>
<div id="app2">{{ msg }}</div>

<script>
new Vue({ el: '#app1', data: { msg: 'App 1' } });
new Vue({ el: '#app2', data: { msg: 'App 2' } });
</script>
```

✅ Vue 3 can do the same with `createApp(App).mount('#app1')`.

---

### Interview Tips

- Highlight that **multiple instances are useful for micro-frontends** or embedding Vue in legacy apps.
    

---

## **3️⃣ Is `new Vue()` used in Vue 3?**

### How to Answer in an Interview

Clarify that `new Vue()` is **not used in Vue 3**.

---

### Answer

No. `new Vue()` is deprecated in Vue 3. Instead, Vue 3 uses:

```javascript
import { createApp } from "vue";
const app = createApp(App);
app.mount("#app");
```

This change provides **better flexibility**, **multiple app instance support**, and **clearer plugin management**.

---

# **7. What is a Single Page Application (SPA)? Does Vue.js belong to SPAs?**

## How to Answer in an Interview

Explain that an SPA is a **web application that loads a single HTML page and dynamically updates content** without full page reloads. Highlight that Vue.js is **commonly used to build SPAs** using `vue-router` for navigation and dynamic component rendering.

---

## Answer

A **Single Page Application (SPA)** is a web application that:

- Loads **a single HTML page initially**.
    
- Dynamically updates the page content **using JavaScript** as the user interacts.
    
- Uses **client-side routing** (via libraries like `vue-router`) to mimic navigation **without reloading the page**.
    

Yes, **Vue.js is widely used to build SPAs**. Using Vue Router, Vue apps can have multiple views (pages) while still being a **single-page application**.

### **Key Benefits of SPAs:**

✅ Faster navigation (no full page reloads).  
✅ Better user experience (app-like feel).  
✅ Efficient use of client-side rendering.

---

## Example

### **Vue Router Setup (SPA Example)**

```javascript
import { createApp } from "vue";
import { createRouter, createWebHistory } from "vue-router";
import Home from "./Home.vue";
import About from "./About.vue";

const routes = [
  { path: "/", component: Home },
  { path: "/about", component: About }
];

const router = createRouter({
  history: createWebHistory(),
  routes
});

createApp(App).use(router).mount("#app");
```

✅ The app **switches between Home and About components** without reloading the page.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between SPA and MPA (Multi-Page Application)?**

### How to Answer in an Interview

Compare **page load behavior, routing, and performance trade-offs**.

---

### Answer

|Feature|SPA (Single Page App)|MPA (Multi-Page App)|
|---|---|---|
|Page Loading|Loads once, updates dynamically|Reloads full HTML on navigation|
|Speed|Faster after initial load|Slower due to full page reload|
|SEO|Harder (requires SSR/Prerender)|Easier (traditional HTML pages)|
|Examples|Gmail, Trello, GitLab|Amazon product pages, Blogs|

---

### Interview Tips

- Mention that **SPAs give an app-like feel**, while MPAs are better for **SEO-heavy static sites**.
    
- Highlight that Vue can be used for both SPAs and MPAs (using server-side rendering with Nuxt.js).
    

---

## **2️⃣ How does Vue Router enable SPA behavior?**

### How to Answer in an Interview

Show that Vue Router **handles navigation on the client-side** without reloading the page.

---

### Answer

Vue Router enables SPA behavior by:

- Using the **History API** (`pushState`, `popState`) to change URLs without reloading.
    
- Dynamically rendering components based on the current route.
    

This creates the illusion of navigating multiple pages while actually staying on the same HTML file.

---

### Example

```javascript
const router = createRouter({
  history: createWebHistory(),
  routes: [
    { path: "/", component: Home },
    { path: "/about", component: About }
  ]
});
```

✅ When the URL changes, Vue **swaps components dynamically**, avoiding a full reload.

---

### Interview Tips

- Use keywords like **"client-side routing"**, **"History API"**, and **"dynamic component rendering"**.
    
- Mention that Vue Router **improves SPA navigation** but can also support **hash-based routing**.
    

---

## **3️⃣ Are SPAs bad for SEO? How can Vue handle SEO issues?**

### How to Answer in an Interview

Explain that SPAs rely on **client-side rendering**, which search engines may struggle with.

---

### Answer

SPAs can be bad for SEO because:

- Content is rendered dynamically using JavaScript.
    
- Search engine crawlers may not fully index pages without prerendered HTML.
    

**Solutions in Vue.js:**  
✅ **Server-Side Rendering (SSR)** with **Nuxt.js**.  
✅ **Prerendering** static pages at build time.  
✅ Using **meta tags and dynamic routing** for better SEO handling.

---

### Interview Tips

- Mention **Nuxt.js** as the go-to framework for SSR in Vue.
    
- Use terms like **"prerendering"** and **"hydration"** to show depth of knowledge.
    

---

# **8. What are Components in Vue.js?**

## How to Answer in an Interview

Explain that components are **reusable, self-contained building blocks** in Vue.js that encapsulate template, logic, and style. Emphasize that components promote **modularity, reusability, and maintainability** in large applications.

---

## Answer

Components in Vue.js are **reusable and independent UI elements** that manage their own:

- **Template (HTML)** – Defines the structure.
    
- **Logic (JavaScript)** – Contains data, props, methods, and lifecycle hooks.
    
- **Style (CSS)** – Defines the component’s styling.
    

Vue components follow a **component-based architecture**, meaning a UI is built by combining multiple small components. Components can be:

- **Root Components** – The main entry point of the app.
    
- **Child Components** – Nested inside other components.
    

---

### **Benefits of Components**

✅ **Reusability** – Write once, use anywhere.  
✅ **Maintainability** – Small, independent pieces of code.  
✅ **Separation of Concerns** – Logic, UI, and styling live together in one unit.  
✅ **Scalability** – Ideal for large applications.

---

## Example

### **App.vue (Parent Component)**

```vue
<template>
  <div>
    <h1>Welcome to My App</h1>
    <UserCard name="John Doe" age="25" />
  </div>
</template>

<script>
import UserCard from "./components/UserCard.vue";

export default {
  components: { UserCard }
};
</script>
```

### **UserCard.vue (Child Component)**

```vue
<template>
  <div class="card">
    <h2>{{ name }}</h2>
    <p>Age: {{ age }}</p>
  </div>
</template>

<script>
export default {
  props: ["name", "age"]
};
</script>

<style scoped>
.card { border: 1px solid #ccc; padding: 10px; }
</style>
```

✅ The `UserCard` component is reusable and accepts **props** for dynamic content.

---

# **Trailing Questions**

---

## **1️⃣ What are the types of components in Vue.js?**

### How to Answer in an Interview

Show that you know **how Vue organizes components**.

---

### Answer

There are mainly **two types of components in Vue.js**:

1️⃣ **Global Components** – Registered using `Vue.component()` (Vue 2) or `app.component()` (Vue 3) and can be used anywhere.  
2️⃣ **Local Components** – Imported and registered inside a specific component's `components` option.

---

### Example

```javascript
// Global Component (Vue 3)
app.component("ButtonCounter", ButtonCounter);

// Local Component
export default {
  components: { ButtonCounter }
};
```

✅ **Best Practice:** Use **local registration** for better maintainability.

---

### Interview Tips

- Mention that Vue also supports **dynamic components** via `<component :is="">`.
    

---

## **2️⃣ How do components communicate with each other?**

### How to Answer in an Interview

Cover **parent-to-child (props)** and **child-to-parent (events)** communication patterns.

---

### Answer

Components in Vue communicate mainly through:  
✅ **Props (Parent → Child)** – Passing data down.  
✅ **Events (Child → Parent)** – Emitting events to send data up.  
✅ **Provide/Inject (Vue 3)** – Sharing data between deeply nested components.  
✅ **Vuex/Pinia** – For global state management.

---

### Example

```vue
<!-- Parent.vue -->
<Child :message="parentMessage" @sendData="handleData" />
```

```vue
<!-- Child.vue -->
<button @click="$emit('sendData', 'Hello Parent!')">Send</button>
```

✅ Parent receives `"Hello Parent!"` when the child button is clicked.

---

### Interview Tips

- Always **mention props, events, and Vuex/Pinia** for state management.
    
- Highlight that Vue 3 also provides **Composition API patterns (reactive state sharing)**.
    

---

## **3️⃣ What is the difference between a component and a directive?**

### How to Answer in an Interview

Explain **role differences** clearly.

---

### Answer

|Feature|Component|Directive|
|---|---|---|
|Purpose|Defines **UI + Logic + Style**|Adds **behaviour to DOM elements**|
|Example|`<UserCard />`|`v-if`, `v-model`, `v-bind`|
|Reusability|Can be reused as building blocks|Used inside components to control DOM|

✅ **Components = Building Blocks**  
✅ **Directives = Instructions for DOM manipulation**

---

# **9. What are Dynamic Components in Vue.js?**

## How to Answer in an Interview

Explain that dynamic components allow you to **switch between multiple components at runtime** using the `<component :is="">` element. Emphasize that they are useful for **tab systems, wizards, or conditional rendering of components**.

---

## Answer

Dynamic components in Vue.js are components that **change based on runtime conditions**. Instead of hardcoding which component to display, Vue dynamically renders a component using the `<component>` element and the `:is` attribute.

This feature is especially useful for:  
✅ **Tab systems** (switching between tabs).  
✅ **Step-by-step wizards**.  
✅ **Conditional UI rendering without long `v-if` chains**.

---

### **Key Benefits**

- **Reusability** – Same placeholder, multiple components.
    
- **Cleaner Code** – Avoids multiple `v-if` conditions.
    
- **Supports `<keep-alive>`** – Preserves state when switching components.
    

---

## Example

```vue
<template>
  <div>
    <button @click="currentView = 'Home'">Home</button>
    <button @click="currentView = 'About'">About</button>

    <component :is="currentView" />
  </div>
</template>

<script>
import Home from "./Home.vue";
import About from "./About.vue";

export default {
  data() {
    return { currentView: "Home" };
  },
  components: { Home, About }
};
</script>
```

✅ The component rendered inside `<component :is="">` changes dynamically based on `currentView`.

---

# **Trailing Questions**

---

## **1️⃣ What is the benefit of using `<keep-alive>` with dynamic components?**

### How to Answer in an Interview

Show that you understand **performance optimization and state preservation**.

---

### Answer

The `<keep-alive>` wrapper **caches inactive components**, so when you switch back to a component, its state is preserved instead of being destroyed and recreated.

This improves **performance** and **user experience**, especially in **tabs or forms** where users don’t want to lose input data when switching views.

---

### Example

```vue
<keep-alive>
  <component :is="currentView" />
</keep-alive>
```

✅ The inactive components remain in memory, retaining their state.

---

### Interview Tips

- Mention **performance boost + better UX**.
    
- Show you know `<keep-alive>` works **only for stateful components**.
    

---

## **2️⃣ How is a dynamic component different from `v-if`/`v-show`?**

### How to Answer in an Interview

Explain the **key difference in how components are handled in the DOM**.

---

### Answer

|Feature|Dynamic Component `<component :is="">`|`v-if` / `v-show`|
|---|---|---|
|Use Case|Switches **between multiple components**|Show/hide parts of the DOM|
|Rendering|Completely **replaces the component**|Keeps/Removes DOM elements|
|State Handling|Can use `<keep-alive>` to preserve state|State may reset when destroyed|

✅ **Dynamic components are better when you need to load different components in one placeholder.**

---

### Example

- Use `v-if` for conditional HTML blocks.
    
- Use `<component :is="">` for **reusable placeholders that load different components**.
    

---

### Interview Tips

- Highlight **reusability and cleaner architecture** as the main benefit.
    

---

## **3️⃣ Can we pass props to dynamic components?**

### How to Answer in an Interview

Show that dynamic components **still support props and events**.

---

### Answer

Yes, you can pass props to dynamic components just like normal components.

---

### Example

```vue
<component :is="currentView" :title="'Dynamic Title'" />
```

✅ If the component has a `title` prop, it will receive `"Dynamic Title"` even when switched dynamically.

---

# **10. What is a Template in Vue.js?**

## How to Answer in an Interview

Explain that a template in Vue.js is **the declarative HTML structure** of a component. It uses **Vue directives** (`v-bind`, `v-if`, `v-for`, etc.) and **interpolation (`{{ }}`)** to bind data dynamically. Highlight that templates are compiled into **render functions** by Vue at build time.

---

## Answer

A **template in Vue.js** is an **HTML-based syntax** that defines how the UI should look based on the component’s data and logic.

Vue templates support:  
✅ **Interpolation (`{{ }}`)** – For binding dynamic values.  
✅ **Directives (`v-if`, `v-for`, `v-bind`, etc.)** – For conditional rendering, loops, and attribute binding.  
✅ **Event Handling (`@click`, `@input`)** – For user interactions.

Vue **compiles templates into Virtual DOM render functions**, which makes them fast and efficient.

---

### **Benefits of Using Templates**

- **Declarative Syntax** – Easier to read and understand.
    
- **Reactive Updates** – Automatically updates the DOM when data changes.
    
- **Integration with Directives** – Provides powerful dynamic behavior.
    

---

## Example

```vue
<template>
  <div>
    <h1>{{ title }}</h1>
    <input v-model="name" placeholder="Enter name" />
    <p v-if="name">Hello, {{ name }}!</p>
    <button @click="resetName">Reset</button>
  </div>
</template>

<script>
export default {
  data() {
    return { title: "Vue Template Example", name: "" };
  },
  methods: {
    resetName() {
      this.name = "";
    }
  }
};
</script>
```

✅ Here, the template dynamically binds data (`title`, `name`) and handles events (`@click`).

---

# **Trailing Questions**

---

## **1️⃣ How are templates converted to render functions?**

### How to Answer in an Interview

Show that you understand the **compilation process behind templates**.

---

### Answer

Vue **compiles templates into JavaScript render functions** at build time (or runtime for CDN usage). These render functions return **Virtual DOM nodes**, which Vue uses to efficiently update the UI.

This means templates are **just syntactic sugar** for writing `render()` functions manually.

---

### Example

```javascript
// Template
<template><p>{{ msg }}</p></template>

// Compiled Render Function
render() {
  return h('p', this.msg)
}
```

✅ Vue internally uses these render functions for **faster DOM updates**.

---

### Interview Tips

- Use terms like **“Virtual DOM”, “render functions”, and “compilation”**.
    
- Mention that Vue **also allows JSX or manual render functions**.
    

---

## **2️⃣ What is the difference between template syntax and JSX in Vue?**

### How to Answer in an Interview

Highlight **use cases for each**.

---

### Answer

|Feature|Vue Template Syntax|JSX in Vue|
|---|---|---|
|Readability|Easier for designers/developers|Closer to JavaScript logic|
|Flexibility|Limited dynamic logic|Full JS expressions inside markup|
|Compilation|Compiled to render functions|Directly written as render functions|

✅ Vue templates are **beginner-friendly**, while JSX is useful for **complex conditional rendering or logic-heavy components**.

---

### Example

```jsx
// JSX Example
render() {
  return <p>{ this.msg }</p>;
}
```

---

### Interview Tips

- Say that **most Vue projects use templates**, but JSX is available for advanced use cases.
    

---

## **3️⃣ Can templates have multiple root elements?**

### How to Answer in an Interview

Explain Vue 2 vs Vue 3 behavior.

---

### Answer

- **Vue 2:** Templates **must have a single root element** (wrap everything in `<div>`).
    
- **Vue 3:** Supports **fragments**, so templates can have **multiple root elements**.
    

---

### Example (Vue 3)

```vue
<template>
  <h1>Hello</h1>
  <p>Welcome to Vue 3</p>
</template>
```

✅ Works fine in Vue 3, but would throw an error in Vue 2.

---
# **11. What are Vue.js Forms? What are Form Input Bindings?**

## How to Answer in an Interview

Explain that Vue.js makes form handling simple with **two-way data binding (`v-model`)**. Forms in Vue can bind inputs (text, checkbox, radio, select) to data properties, automatically syncing changes between the UI and component state.

---

## Answer

Forms in Vue.js are **interactive UI elements (input fields, checkboxes, selects, etc.)** that can be bound to the component’s data using `v-model`.

### **Key Features of Vue.js Form Handling**

✅ **Two-Way Binding (`v-model`)** – Automatically syncs data between the UI and component.  
✅ Supports **all input types** – text, checkbox, radio, select, textarea, etc.  
✅ Works with **modifiers** like `.lazy`, `.number`, `.trim` for better control.

---

### **Benefits of Form Bindings**

- Less boilerplate code compared to manual event listeners.
    
- Data updates **immediately reflect in the DOM**.
    
- Works seamlessly with validation libraries.
    

---

## Example

```vue
<template>
  <div>
    <h2>Vue Form Example</h2>
    <input v-model="name" placeholder="Enter name" />
    <p>Hello, {{ name }}</p>

    <input type="checkbox" v-model="isSubscribed" /> Subscribe
    <p>Subscribed: {{ isSubscribed }}</p>

    <select v-model="selectedCountry">
      <option value="India">India</option>
      <option value="USA">USA</option>
    </select>
    <p>Country: {{ selectedCountry }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      isSubscribed: false,
      selectedCountry: "India"
    };
  }
};
</script>
```

✅ The `v-model` directive automatically updates the `data` properties as the user interacts with the form.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between `v-model` and `v-bind` for forms?**

### How to Answer in an Interview

Clarify that `v-bind` is **one-way binding**, while `v-model` is **two-way binding**.

---

### Answer

|Feature|`v-bind`|`v-model`|
|---|---|---|
|Binding Type|One-way (data → UI only)|Two-way (data ↔ UI sync)|
|Usage|Setting attributes like `value`|Handling input updates automatically|
|Event Needed?|Requires `@input` manually|Handles events internally|

✅ Use `v-bind:value` when you **only display data**.  
✅ Use `v-model` when you **need two-way interaction**.

---

### Example

```vue
<!-- Using v-bind -->
<input :value="name" @input="name = $event.target.value" />

<!-- Using v-model -->
<input v-model="name" />
```

✅ Both do the same thing, but `v-model` is **shorter and cleaner**.

---

### Interview Tips

- Use keywords **“one-way binding”** vs **“two-way binding”**.
    
- Mention that `v-model` is a **syntactic sugar** for `:value` + `@input`.
    

---

## **2️⃣ What are modifiers in `v-model`?**

### How to Answer in an Interview

Show that you understand **how modifiers control binding behavior**.

---

### Answer

Vue provides modifiers for `v-model` to fine-tune form bindings:

✅ `.lazy` → Updates data **only on `change` event**, not `input`.  
✅ `.number` → Automatically converts input values to numbers.  
✅ `.trim` → Removes leading and trailing spaces.

---

### Example

```vue
<input v-model.lazy="msg" />   <!-- Updates only on blur/change -->
<input v-model.number="age" /> <!-- Converts to number -->
<input v-model.trim="name" />  <!-- Trims spaces -->
```

✅ Modifiers make form handling **more predictable and cleaner**.

---

### Interview Tips

- Always mention **`.lazy`, `.number`, `.trim`**.
    
- If asked for validation, mention integration with libraries like VeeValidate or custom watchers.
    

---

## **3️⃣ How do you handle multiple checkboxes or radio buttons in Vue.js?**

### How to Answer in an Interview

Explain that Vue automatically binds arrays for checkboxes and single values for radios.

---

### Answer

- For **checkboxes**, `v-model` binds selected values into an **array**.
    
- For **radio buttons**, `v-model` binds the **selected value** as a string or number.
    

---

### Example

```vue
<!-- Multiple Checkboxes -->
<input type="checkbox" v-model="hobbies" value="Cricket" />
<input type="checkbox" v-model="hobbies" value="Football" />

<!-- Radio Buttons -->
<input type="radio" v-model="gender" value="Male" />
<input type="radio" v-model="gender" value="Female" />
```

✅ For checkboxes → `hobbies = ['Cricket', 'Football']`  
✅ For radio → `gender = 'Male'`

---

# **13. What is a Vue.js Component? Write an Example for the Same.**

## How to Answer in an Interview

Explain that a Vue.js component is a **reusable and self-contained building block** that encapsulates its own **template, logic, and style**. Mention that components can be **local or global**, and they are the foundation of Vue's **component-based architecture**.

---

## Answer

A **Vue.js component** is a **reusable UI element** that manages its own **data, logic, and styles**. Components help create **modular, maintainable, and scalable** applications.

Components can be:  
✅ **Global** → Registered once and used anywhere.  
✅ **Local** → Registered inside a parent component’s `components` option.

---

### **Key Features of Components:**

- Encapsulation → Template, logic, and style in one file (`.vue`).
    
- Reusability → Can be used multiple times with different props.
    
- Communication → Components communicate via **props, events, or state management tools**.
    

---

## Example

### **Parent Component (App.vue)**

```vue
<template>
  <div>
    <h1>Welcome to My Vue App</h1>
    <UserCard name="John Doe" age="28" />
    <UserCard name="Jane Smith" age="25" />
  </div>
</template>

<script>
import UserCard from "./components/UserCard.vue";

export default {
  components: { UserCard }
};
</script>
```

---

### **Child Component (UserCard.vue)**

```vue
<template>
  <div class="card">
    <h2>{{ name }}</h2>
    <p>Age: {{ age }}</p>
  </div>
</template>

<script>
export default {
  props: ["name", "age"]
};
</script>

<style scoped>
.card {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 5px;
}
</style>
```

✅ Here, `UserCard` is a **reusable component** that takes props (`name`, `age`) and displays them dynamically.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between global and local components?**

### How to Answer in an Interview

Show that you understand **registration scope and usage differences**.

---

### Answer

|Feature|Global Component|Local Component|
|---|---|---|
|Registration|`app.component("Name", Comp)`|Registered inside `components: {}`|
|Usage Scope|Can be used in any component|Can be used only inside the parent|
|Best Practice|Not recommended for large projects|Preferred for better maintainability|

✅ **Local components** are better for large apps to avoid naming conflicts.

---

### Example

```javascript
// Global Component (Vue 3)
app.component("ButtonCounter", ButtonCounter);

// Local Component
export default {
  components: { ButtonCounter }
};
```

---

### Interview Tips

- Best practice → **Register components locally unless truly global.**
    

---

## **2️⃣ How do components communicate in Vue.js?**

### How to Answer in an Interview

Cover **props, events, and state management tools**.

---

### Answer

Components communicate in Vue using:  
✅ **Props (Parent → Child)** → Pass data down.  
✅ **Events (`$emit`) (Child → Parent)** → Send data up.  
✅ **Provide/Inject (Vue 3)** → Share data across deeply nested components.  
✅ **State Management (Vuex/Pinia)** → Share global state across multiple components.

---

### Example

```vue
<!-- Parent.vue -->
<Child :message="parentMessage" @update="handleUpdate" />

<!-- Child.vue -->
<button @click="$emit('update', 'New Value')">{{ message }}</button>
```

✅ The parent listens to `update` event emitted by the child.

---

### Interview Tips

- Always mention **props, events, provide/inject, Vuex/Pinia**.
    

---

## **3️⃣ Can we pass functions as props to components?**

### How to Answer in an Interview

Show that Vue supports function props like React.

---

### Answer

Yes, you can pass functions as props to components in Vue. The child component can call the function just like any other prop value.

---

### Example

```vue
<!-- Parent.vue -->
<UserCard :onDelete="deleteUser" />

<!-- Child.vue -->
<button @click="onDelete()">Delete</button>

<script>
export default { props: ["onDelete"] };
</script>
```

✅ This is useful for **callback-based communication**.

---

# **14. What is Binding? How Do You Bind HTML Classes and Inline Styles in Vue.js?**

## How to Answer in an Interview

Explain that **binding** in Vue.js refers to connecting data from the component to the DOM using directives like `v-bind`. Mention that binding can be **one-way (`v-bind`)** or **two-way (`v-model`)**. Specifically highlight how **classes and styles can be dynamically bound using objects or arrays**.

---

## Answer

**Binding** in Vue.js is the process of **dynamically connecting data from the component’s state to attributes or properties of DOM elements**.

- **One-way binding (`v-bind`)** – Passes data from component to the DOM.
    
- **Two-way binding (`v-model`)** – Syncs data both ways (used in forms).
    

For **classes and styles**, Vue allows **dynamic binding** using `v-bind:class` and `v-bind:style` (or shorthand `:class` and `:style`).

---

### **Binding HTML Classes**

✅ **Object Syntax** → Toggle classes based on conditions.  
✅ **Array Syntax** → Apply multiple classes dynamically.

```vue
<div :class="{ active: isActive, error: hasError }"></div>
<div :class="[primaryClass, secondaryClass]"></div>
```

---

### **Binding Inline Styles**

✅ **Object Syntax** → Key-value pairs for styles.  
✅ **Array Syntax** → Merge multiple style objects.

```vue
<div :style="{ color: activeColor, fontSize: size + 'px' }"></div>
<div :style="[baseStyle, extraStyle]"></div>
```

---

### **Benefits**

- Cleaner and more dynamic styling.
    
- Automatically updates when data changes.
    

---

## Example

```vue
<template>
  <div>
    <p :class="{ highlighted: isHighlighted }" :style="{ color: textColor }">
      Bound Class and Style Example
    </p>
    <button @click="toggleHighlight">Toggle Highlight</button>
  </div>
</template>

<script>
export default {
  data() {
    return { isHighlighted: false, textColor: "blue" };
  },
  methods: {
    toggleHighlight() {
      this.isHighlighted = !this.isHighlighted;
      this.textColor = this.isHighlighted ? "red" : "blue";
    }
  }
};
</script>

<style>
.highlighted {
  background-color: yellow;
  font-weight: bold;
}
</style>
```

✅ The class and style update dynamically when the button is clicked.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between static and dynamic class binding?**

### How to Answer in an Interview

Highlight that **static classes never change**, while **dynamic classes depend on data**.

---

### Answer

|Feature|Static Class|Dynamic Class (`v-bind:class`)|
|---|---|---|
|Changeable?|No|Yes (updates when data changes)|
|Syntax|`<div class="red"></div>`|`<div :class="{ red: isRed }"></div>`|
|Use Case|Fixed styling|Conditional or multiple classes|

✅ Dynamic classes **reactively update** when the component state changes.

---

### Example

```vue
<!-- Static -->
<p class="red">Always red</p>

<!-- Dynamic -->
<p :class="{ red: isRed }">Changes when isRed is true</p>
```

---

### Interview Tips

- Mention **object syntax vs array syntax** for class binding.
    

---

## **2️⃣ Can we bind multiple styles or classes dynamically?**

### How to Answer in an Interview

Show object and array syntax for binding **multiple values**.

---

### Answer

Yes, Vue supports **multiple dynamic styles and classes** using arrays or objects.

```vue
<div :class="[classA, classB]"></div>
<div :style="[styleObjectA, styleObjectB]"></div>
```

✅ Vue merges all classes/styles dynamically.

---

### Example

```vue
data() {
  return {
    classA: "big",
    classB: "bold",
    styleObjectA: { color: "blue" },
    styleObjectB: { fontSize: "20px" }
  };
}
```

✅ Result: `<div class="big bold" style="color:blue; font-size:20px"></div>`

---

## **3️⃣ What is the shorthand for `v-bind`?**

### How to Answer in an Interview

Clarify that `v-bind` has a shorthand **colon (:)**.

---

### Answer

Instead of writing `v-bind:class`, you can write simply `:class`.

```vue
<div v-bind:class="myClass"></div>
<div :class="myClass"></div> <!-- shorthand -->
```

✅ The same applies to `:style`, `:id`, `:disabled`, etc.

---

# **15. What is `v-bind` and `v-model` in Vue.js?**

## How to Answer in an Interview

Explain that `v-bind` is used for **one-way binding** (from data → UI), while `v-model` is used for **two-way binding** (data ↔ UI). Highlight their use cases with examples, especially in forms.

---

## Answer

### **`v-bind`**

- Provides **one-way binding** between the component’s data and the DOM.
    
- Dynamically binds HTML attributes (like `src`, `class`, `id`, `disabled`, etc.).
    
- Shorthand syntax: `:` (colon).
    

### **`v-model`**

- Provides **two-way binding** between the component’s data and form elements.
    
- Automatically updates data when the user changes input values.
    
- Works with `<input>`, `<textarea>`, `<select>`, checkboxes, and radio buttons.
    

---

### **Key Differences**

|Feature|`v-bind`|`v-model`|
|---|---|---|
|Binding Type|One-way (data → UI)|Two-way (data ↔ UI)|
|Use Case|Bind attributes/props|Form handling/input fields|
|Syntax|`v-bind:value="msg"`|`v-model="msg"`|

---

## Example

```vue
<template>
  <div>
    <!-- Using v-bind -->
    <img :src="imageUrl" :alt="altText" />

    <!-- Using v-model -->
    <input v-model="name" placeholder="Enter name" />
    <p>Hello, {{ name }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return { imageUrl: "logo.png", altText: "Logo", name: "" };
  }
};
</script>
```

✅ Here, `v-bind` binds `src` and `alt` attributes, while `v-model` syncs `name` in both directions.

---

# **Trailing Questions**

---

## **1️⃣ What is the shorthand for `v-bind`?**

### How to Answer in an Interview

Mention that `:` (colon) is shorthand for `v-bind`.

---

### Answer

Instead of writing `v-bind:src`, you can write `:src`.

```vue
<img v-bind:src="imageUrl" />
<img :src="imageUrl" /> <!-- shorthand -->
```

✅ Works for all attributes like `:class`, `:style`, `:id`, etc.

---

### Interview Tips

- Use the term **“shorthand colon syntax”**.
    

---

## **2️⃣ How is `v-model` internally implemented?**

### How to Answer in an Interview

Explain that `v-model` is a **syntactic sugar** for `v-bind:value` + `@input`.

---

### Answer

`v-model="dataProperty"` is equivalent to:

```vue
<input :value="dataProperty" @input="dataProperty = $event.target.value" />
```

✅ Vue internally handles value updates and event binding, making form handling concise.

---

---

## **3️⃣ Can `v-model` be used with custom components?**

### How to Answer in an Interview

Show that `v-model` can bind to a prop called `modelValue` and emit `update:modelValue`.

---

### Answer

Yes, in Vue 3, `v-model` works with custom components by using:

- A **prop named `modelValue`**.
    
- An **event named `update:modelValue`**.
    

---

### Example

```vue
<!-- Parent.vue -->
<CustomInput v-model="username" />

<!-- CustomInput.vue -->
<template>
  <input :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
</template>

<script>
export default { props: ["modelValue"] };
</script>
```

✅ The parent can use `v-model` just like with a normal input.

---

# **16. What is One-Way and Two-Way Data Binding? Give Examples.**

## How to Answer in an Interview

Explain the difference between **one-way** and **two-way binding** in Vue.js. Mention that **one-way binding (`v-bind`) updates only from data → UI**, while **two-way binding (`v-model`) keeps data and UI in sync**. Provide clear examples for both.

---

## Answer

### **One-Way Data Binding**

- Data flows **only from component → UI**.
    
- Achieved using `v-bind` (or shorthand `:`).
    
- UI changes **do not affect data**.
    

---

### **Two-Way Data Binding**

- Data flows **both ways (component ↔ UI)**.
    
- Achieved using `v-model`.
    
- UI changes **automatically update data**, and vice versa.
    

---

### **Key Differences**

|Feature|One-Way Binding (`v-bind`)|Two-Way Binding (`v-model`)|
|---|---|---|
|Data Flow|Component → UI|Component ↔ UI|
|Use Case|Dynamic attributes|Forms, input fields|
|Syntax|`:value="name"`|`v-model="name"`|

---

## Example

```vue
<template>
  <div>
    <!-- One-Way Binding -->
    <input :value="name" /> <!-- Updates only when data changes -->

    <!-- Two-Way Binding -->
    <input v-model="name" /> <!-- Updates data and UI simultaneously -->

    <p>Hello, {{ name }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return { name: "John" };
  }
};
</script>
```

✅ With `v-model`, typing in the input box **updates `name` immediately**, while `:value` does not.

---

# **Trailing Questions**

---

## **1️⃣ Why is two-way binding useful in forms?**

### How to Answer in an Interview

Explain how `v-model` reduces boilerplate code.

---

### Answer

Two-way binding simplifies form handling because it **automatically keeps data and input values in sync**, eliminating the need for manual `@input` event handling.

Instead of writing:

```vue
<input :value="name" @input="name = $event.target.value" />
```

You can just write:

```vue
<input v-model="name" />
```

✅ This makes **forms concise and easier to manage**.

---

---

## **2️⃣ Can you achieve two-way binding without `v-model`?**

### How to Answer in an Interview

Show that `v-model` is just syntactic sugar.

---

### Answer

Yes. Two-way binding can be implemented manually using `v-bind:value` + `@input`.

```vue
<input :value="name" @input="name = $event.target.value" />
```

✅ `v-model` internally does exactly this.

---

---

## **3️⃣ Is two-way binding always recommended?**

### How to Answer in an Interview

Discuss when **one-way binding is better**.

---

### Answer

No, two-way binding should be used **only when user input needs to update data**.

- Use **one-way binding** (`v-bind`) for static or read-only UI.
    
- Use **two-way binding** (`v-model`) only for form elements or interactive fields.
    

Too much two-way binding can make **data flow harder to debug** in large apps.

---

# **17. What is Interpolation and Binding Expression in Vue.js?**

## How to Answer in an Interview

Explain that **interpolation** is the use of `{{ }}` (mustache syntax) to insert dynamic values into the DOM, while **binding expressions** allow JavaScript expressions inside those curly braces. Highlight that interpolation is for text content, while `v-bind` is used for attributes.

---

## Answer

### **Interpolation (`{{ }}`)**

- Uses **mustache syntax** to insert dynamic values into the DOM.
    
- Can also include **simple JavaScript expressions**.
    
- Works **only for text content**, not HTML attributes.
    

---

### **Binding Expressions**

- Allow using **JavaScript expressions inside interpolation**.
    
- Can perform operations like arithmetic, string concatenation, or function calls.
    
- For attributes, use `v-bind` (or shorthand `:`).
    

---

### **Key Points**

✅ Interpolation automatically updates when data changes (reactivity).  
✅ Only simple expressions are allowed—no conditionals or loops.

---

## Example

```vue
<template>
  <div>
    <!-- Interpolation -->
    <p>Hello, {{ name }}</p>

    <!-- Binding Expression -->
    <p>Next Year Age: {{ age + 1 }}</p>
    <p>Uppercase Name: {{ name.toUpperCase() }}</p>

    <!-- Attribute Binding (Needs v-bind) -->
    <img :src="imageUrl" :alt="`Photo of ${name}`" />
  </div>
</template>

<script>
export default {
  data() {
    return { name: "John", age: 25, imageUrl: "profile.jpg" };
  }
};
</script>
```

✅ Vue **reactively updates these values** when `name` or `age` changes.

---

# **Trailing Questions**

---

## **1️⃣ Can we use conditionals inside interpolation?**

### How to Answer in an Interview

Explain that **ternary operators are allowed, but statements are not.**

---

### Answer

Yes, we can use **ternary operators**, but we **cannot use full `if` statements** inside interpolation.

```vue
<p>{{ isAdmin ? 'Welcome Admin' : 'Welcome User' }}</p> <!-- ✅ Works -->
<p>{{ if(isAdmin){ 'Welcome' } }}</p> <!-- ❌ Invalid -->
```

✅ Interpolation only allows **single expressions, not statements**.

---

---

## **2️⃣ What is the difference between interpolation and `v-bind`?**

### How to Answer in an Interview

Compare their usage.

---

### Answer

|Feature|Interpolation (`{{ }}`)|`v-bind` / `:`|
|---|---|---|
|Use Case|For text content|For HTML attributes/props|
|Example|`<p>{{ name }}</p>`|`<input :value="name" />`|
|Works With|Text nodes|Attributes, props, DOM properties|

✅ Interpolation cannot be used for attributes—`v-bind` is required.

---

---

## **3️⃣ Can interpolation be used inside attributes?**

### How to Answer in an Interview

Clarify the correct syntax.

---

### Answer

No, interpolation (`{{ }}`) **does not work in attributes**. For attributes, you must use `v-bind`.

❌ **Wrong:**

```html
<img src="{{ imageUrl }}" />
```

✅ **Correct:**

```html
<img :src="imageUrl" />
```

---

# **18. What is a Reactive Interface in Vue.js?**

## How to Answer in an Interview

Explain that a reactive interface is **an interface that updates automatically when the underlying data changes**. Mention that Vue achieves reactivity through **reactive data binding** using `ref`, `reactive`, and Vue’s reactivity system (Proxy-based in Vue 3).

---

## Answer

A **reactive interface** in Vue.js is a UI that **automatically updates whenever the data changes**—without manually manipulating the DOM.

Vue achieves this using its **reactivity system**, which tracks dependencies and updates the Virtual DOM efficiently.

---

### **How Vue's Reactivity Works:**

✅ In **Vue 2**, reactivity was based on `Object.defineProperty()`.  
✅ In **Vue 3**, it uses **ES6 Proxy**, which is more powerful and can track new properties dynamically.

---

### **Reactive Data in Vue 3:**

- `ref()` → Creates a reactive primitive value.
    
- `reactive()` → Creates a reactive object.
    

---

## Example

```vue
<template>
  <div>
    <p>Counter: {{ count }}</p>
    <button @click="count++">Increment</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const count = ref(0);
    return { count };
  }
};
</script>
```

✅ When `count` changes, the UI **automatically re-renders** without manual DOM updates.

---

# **Trailing Questions**

---

## **1️⃣ How does Vue track dependencies for reactivity?**

### How to Answer in an Interview

Show understanding of Vue's **reactive system and dependency tracking**.

---

### Answer

Vue uses a **dependency tracking system**:  
1️⃣ Each reactive property is wrapped by a **getter and setter**.  
2️⃣ When a component accesses the property, Vue **tracks the dependency**.  
3️⃣ When the property changes, Vue **triggers a re-render** of only the affected parts of the DOM.

In Vue 3, this is implemented using **Proxy-based reactivity**, which can track even new properties added to objects.

---

### Example

```javascript
import { reactive, watchEffect } from "vue";

const state = reactive({ count: 0 });

watchEffect(() => {
  console.log(`Count changed to: ${state.count}`);
});

state.count++; // Trigger effect automatically
```

✅ Vue automatically detects and reacts to `state.count` changes.

---

---

## **2️⃣ What is the difference between `ref` and `reactive`?**

### How to Answer in an Interview

Explain their specific use cases.

---

### Answer

|Feature|`ref()`|`reactive()`|
|---|---|---|
|Data Type|For **primitive values**|For **objects and arrays**|
|Access|Requires `.value`|Direct property access|
|Example|`const count = ref(0)`|`const user = reactive({name:"A"})`|

✅ Best Practice → Use `ref` for single values and `reactive` for complex objects.

---

---

## **3️⃣ Why is Vue's reactivity better in Vue 3 compared to Vue 2?**

### How to Answer in an Interview

Highlight **Proxy advantages over `Object.defineProperty()`**.

---

### Answer

- Vue 2 used `Object.defineProperty()`, which **couldn’t detect new properties or array index changes**.
    
- Vue 3 uses **Proxy**, which can:  
    ✅ Detect new properties added to objects.  
    ✅ Detect array index changes.  
    ✅ Provide better performance and flexibility.
    

---
# **19. Explain Vue.js Events. What is a Click Event?**

## How to Answer in an Interview

Explain that Vue.js uses the `v-on` directive (or shorthand `@`) to listen for DOM events and execute methods when those events occur. A **click event** is one of the most common events that triggers when a user clicks an element.

---

## Answer

Vue.js provides the **`v-on` directive (or shorthand `@`)** to **listen for DOM events** and execute component methods.

A **click event** is triggered whenever the user clicks on an element (like a button or div). By binding `v-on:click` or `@click`, we can call a method or inline expression when the element is clicked.

---

### **Key Points:**

✅ Uses `v-on:eventName` or shorthand `@eventName`.  
✅ Can call methods or inline expressions.  
✅ Supports **event modifiers** like `.prevent`, `.stop`, `.once`.

---

## Example

```vue
<template>
  <div>
    <button @click="increment">Click Me</button>
    <p>Clicked {{ count }} times</p>
  </div>
</template>

<script>
export default {
  data() {
    return { count: 0 };
  },
  methods: {
    increment() {
      this.count++;
    }
  }
};
</script>
```

✅ Each click **calls `increment()`** and updates the count reactively.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between inline event handling and method handling?**

### How to Answer in an Interview

Show that inline handlers are shorter, but method handling is cleaner for complex logic.

---

### Answer

|Feature|Inline Handler|Method Handler|
|---|---|---|
|Syntax|`@click="count++"`|`@click="increment"`|
|Use Case|Simple one-liners|Complex logic / multiple lines|
|Readability|Less clean for big logic|Easier to maintain|

✅ Best Practice → Use **methods** for better readability.

---

### Example

```vue
<!-- Inline -->
<button @click="count++">Click</button>

<!-- Method -->
<button @click="increment">Click</button>
```

---

---

## **2️⃣ Can we pass parameters to event methods?**

### How to Answer in an Interview

Show that Vue supports passing arguments, but `$event` must be used for event objects.

---

### Answer

Yes, you can pass parameters to event methods:

```vue
<button @click="sayHello('John')">Greet</button>
```

If you also need the event object:

```vue
<button @click="sayHello('John', $event)">Greet</button>
```

✅ `$event` is a special variable that gives access to the native event object.

---

---

## **3️⃣ What is the difference between `v-on` and `@`?**

### How to Answer in an Interview

Explain that `@` is just shorthand.

---

### Answer

`v-on:event` and `@event` are **exactly the same**.

```vue
<!-- Both are same -->
<button v-on:click="increment">Click</button>
<button @click="increment">Click</button>
```

✅ Use `@` for cleaner syntax.

---

# **20. What are Event Modifiers? What are Event-Key Modifiers in Vue.js?**

## How to Answer in an Interview

Explain that event modifiers **modify the behavior of DOM events** (e.g., preventing default, stopping propagation), while key modifiers **listen for specific keyboard keys** in events like `keyup` or `keydown`.

---

## Answer

### **Event Modifiers**

Event modifiers in Vue **alter the behavior of events** directly in the template without manually calling `event.preventDefault()` or `event.stopPropagation()`.

Common event modifiers:  
✅ `.stop` → Stops event propagation.  
✅ `.prevent` → Prevents default action.  
✅ `.capture` → Adds event listener in capture mode.  
✅ `.once` → Event will fire only once.  
✅ `.self` → Triggers only if the event target is the bound element itself.

---

### **Event-Key Modifiers**

Key modifiers **listen for specific keys** in keyboard events.

Examples:  
✅ `.enter` → Trigger when Enter key is pressed.  
✅ `.tab`, `.delete`, `.esc`, `.space` → Common key shortcuts.  
✅ You can also use **custom key codes**.

---

## Example

```vue
<template>
  <div>
    <!-- Event Modifiers -->
    <form @submit.prevent="submitForm">
      <button type="submit">Submit</button>
    </form>

    <!-- Key Modifiers -->
    <input @keyup.enter="saveData" placeholder="Press Enter to Save" />

    <!-- Multiple Modifiers -->
    <button @click.stop.once="handleClick">Click Once (Stops Propagation)</button>
  </div>
</template>

<script>
export default {
  methods: {
    submitForm() {
      alert("Form submitted!");
    },
    saveData() {
      alert("Data saved!");
    },
    handleClick() {
      alert("Button clicked only once!");
    }
  }
};
</script>
```

✅ This example uses **`.prevent`, `.enter`, `.stop`, and `.once`**.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between `.stop` and `.prevent`?**

### How to Answer in an Interview

Explain that `.stop` stops propagation, while `.prevent` prevents default action.

---

### Answer

|Modifier|Purpose|
|---|---|
|`.stop`|Stops event from propagating to parent|
|`.prevent`|Prevents the default browser action|

Example:

```vue
<button @click.stop="doSomething">Stop Propagation</button>
<form @submit.prevent="submitForm">Prevent Default</form>
```

✅ `.stop` affects event bubbling, `.prevent` affects browser default behavior.

---

---

## **2️⃣ Can we chain multiple event modifiers?**

### How to Answer in an Interview

Yes, modifiers can be chained together.

---

### Answer

Yes, Vue allows chaining event modifiers:

```vue
<button @click.stop.once="handleClick">Click Me</button>
```

✅ This stops propagation and ensures the event triggers only once.

---

---

## **3️⃣ How do key modifiers improve keyboard event handling?**

### How to Answer in an Interview

Explain that they make code **cleaner and easier to read**.

---

### Answer

Instead of writing manual `if` conditions in methods:

```vue
<input @keyup="onKeyUp" />

methods: {
  onKeyUp(event) {
    if (event.key === 'Enter') { ... }
  }
}
```

You can simply write:

```vue
<input @keyup.enter="submitData" />
```

✅ Cleaner syntax and **built-in support for common keys**.

---

# **21. What are the Lifecycle Hooks of Vue.js?**

## How to Answer in an Interview

Explain that lifecycle hooks are **special functions provided by Vue** that allow developers to run code at specific stages of a component’s lifecycle—from creation to destruction. Mention the difference between **Vue 2 (Options API)** and **Vue 3 (Composition API)** syntax.

---

## Answer

Lifecycle hooks in Vue.js are **functions that get called automatically at specific stages of a component’s existence**—such as when it is created, mounted, updated, or unmounted.

They allow developers to **perform side effects**, like fetching data, adding event listeners, or cleaning up resources at the right time.

---

### **Lifecycle Phases**

|Phase|Hooks (Options API)|Hooks (Composition API)|
|---|---|---|
|Creation|`beforeCreate`, `created`|`setup()`|
|Mounting|`beforeMount`, `mounted`|`onBeforeMount`, `onMounted`|
|Updating|`beforeUpdate`, `updated`|`onBeforeUpdate`, `onUpdated`|
|Unmounting|`beforeDestroy`, `destroyed`|`onBeforeUnmount`, `onUnmounted`|

---

### **Key Hooks and Usage:**

✅ `mounted` → Called after component is mounted (fetch data here).  
✅ `beforeUnmount` → Cleanup tasks before destroying the component.  
✅ `updated` → Runs after reactive data updates and DOM re-renders.

---

## Example

### **Vue 2 (Options API)**

```vue
<script>
export default {
  data() {
    return { message: "Hello" };
  },
  mounted() {
    console.log("Component mounted!");
  },
  beforeDestroy() {
    console.log("Component is about to be destroyed!");
  }
};
</script>
```

---

### **Vue 3 (Composition API)**

```vue
<script setup>
import { onMounted, onUnmounted } from "vue";

onMounted(() => console.log("Component mounted!"));
onUnmounted(() => console.log("Component unmounted!"));
</script>
```

✅ Lifecycle hooks help manage **setup, side effects, and cleanup** properly.

---

# **Trailing Questions**

---

## **1️⃣ Which lifecycle hook is best for API calls?**

### How to Answer in an Interview

Explain that `mounted()` (Vue 2) or `onMounted()` (Vue 3) is ideal.

---

### Answer

API calls should be made in **`mounted()` or `onMounted()`** because the component is fully created and the DOM is available.

✅ Avoid API calls in `created()` because the DOM is not yet mounted.

---

### Example

```vue
mounted() {
  fetch("/api/data").then(res => console.log(res));
}
```

---

---

## **2️⃣ What is the difference between `created()` and `mounted()`?**

### How to Answer in an Interview

Highlight DOM availability.

---

### Answer

|Hook|When It Runs|DOM Available?|
|---|---|---|
|`created()`|After data and methods are set up|❌ No|
|`mounted()`|After component is inserted in DOM|✅ Yes|

✅ Use `created()` for initial data setup, `mounted()` for DOM-related tasks.

---

---

## **3️⃣ How do lifecycle hooks differ in Vue 3 vs Vue 2?**

### How to Answer in an Interview

Explain that Vue 3 uses **Composition API functions**.

---

### Answer

- Vue 2 → Lifecycle hooks are defined as **component options** (`mounted`, `updated`, etc.).
    
- Vue 3 → Hooks are **imported functions** inside `setup()` (`onMounted`, `onUpdated`, etc.).
    

✅ Vue 3 provides better **logic grouping** and **code reusability**.

---

# **22. Explain the Component Lifecycle Hooks in Vue.js**

## How to Answer in an Interview

Explain that each Vue component goes through a **lifecycle** from creation to destruction. Vue provides **lifecycle hooks** that allow developers to execute code at specific stages. Mention **key phases (Creation, Mounting, Updating, Unmounting)** and how they differ in Vue 2 and Vue 3.

---

## Answer

The **component lifecycle** in Vue.js describes how a component is **created, rendered, updated, and destroyed**.

Vue provides **lifecycle hooks** that allow developers to **run code at specific stages**. These hooks are available in **Options API (Vue 2)** and as **Composition API functions (Vue 3)**.

---

### **Lifecycle Phases and Hooks**

|Phase|Vue 2 (Options API)|Vue 3 (Composition API)|Usage Example|
|---|---|---|---|
|Creation|`beforeCreate`, `created`|`setup()`|Initialize data, fetch initial state|
|Mounting|`beforeMount`, `mounted`|`onBeforeMount`, `onMounted`|Perform DOM actions, API calls after DOM renders|
|Updating|`beforeUpdate`, `updated`|`onBeforeUpdate`, `onUpdated`|Run code after reactive data changes|
|Unmounting|`beforeDestroy`, `destroyed`|`onBeforeUnmount`, `onUnmounted`|Cleanup listeners, timers, subscriptions|

---

### **Key Points**

✅ **`mounted()` / `onMounted()`** → Best for API calls after DOM is ready.  
✅ **`beforeUnmount()` / `onBeforeUnmount()`** → Best for cleanup tasks.  
✅ **`updated()` / `onUpdated()`** → Runs after reactive data changes cause re-render.

---

## Example

### **Vue 2 (Options API)**

```vue
<script>
export default {
  data() {
    return { count: 0 };
  },
  created() {
    console.log("Component Created");
  },
  mounted() {
    console.log("Component Mounted");
  },
  updated() {
    console.log("Component Updated");
  },
  beforeDestroy() {
    console.log("Component is about to be destroyed");
  }
};
</script>
```

---

### **Vue 3 (Composition API)**

```vue
<script setup>
import { ref, onMounted, onUpdated, onUnmounted } from "vue";

const count = ref(0);

onMounted(() => console.log("Mounted"));
onUpdated(() => console.log("Updated"));
onUnmounted(() => console.log("Unmounted"));
</script>
```

✅ Lifecycle hooks **help manage side effects and resource cleanup efficiently.**

---

# **Trailing Questions**

---

## **1️⃣ What are the main differences between Vue 2 and Vue 3 lifecycle hooks?**

### How to Answer in an Interview

Focus on **syntax change** and **Composition API advantages**.

---

### Answer

- Vue 2 uses **Options API** (`mounted`, `updated`, etc.) defined as component properties.
    
- Vue 3 uses **Composition API functions** (`onMounted`, `onUpdated`, etc.) inside `setup()`.
    

✅ Vue 3 allows **logic grouping and better reusability of code**.

---

---

## **2️⃣ Which lifecycle hook is best for cleaning up timers or event listeners?**

### How to Answer in an Interview

Answer with **beforeUnmount/onUnmounted**.

---

### Answer

The **best hook for cleanup** is:

- Vue 2 → `beforeDestroy()`
    
- Vue 3 → `onBeforeUnmount()` or `onUnmounted()`
    

✅ This ensures that timers, intervals, or event listeners **don’t create memory leaks** after the component is removed.

---

---

## **3️⃣ Can we use multiple lifecycle hooks in the same component?**

### How to Answer in an Interview

Explain that **multiple hooks can exist and run independently.**

---

### Answer

Yes, a component can have **multiple lifecycle hooks**, and they run in order. In Vue 3, you can even **call `onMounted()` multiple times**, and all registered callbacks will execute.

---

# **23. What is the Watch Property in Vue.js?**

## How to Answer in an Interview

Explain that the `watch` property is used to **observe reactive data or computed properties** and execute custom logic whenever they change. Emphasize that watchers are ideal for **side effects like API calls, logging, or complex data transformations.**

---

## Answer

The **`watch` property** in Vue.js allows developers to **monitor changes in data or computed properties** and execute a callback function whenever the value changes.

Watchers are useful when:  
✅ You need to **run side effects** based on data changes.  
✅ The logic is **too complex to handle inside computed properties**.  
✅ You want to **react to asynchronous changes**, like API calls.

---

### **Key Features**

- Can watch **data, props, and computed values**.
    
- Supports **deep watching** for nested objects/arrays.
    
- Can be set as **immediate** to run once when the component loads.
    

---

## Example

### **Using `watch` in Options API (Vue 2 / Vue 3)**

```vue
<script>
export default {
  data() {
    return { count: 0 };
  },
  watch: {
    count(newValue, oldValue) {
      console.log(`Count changed from ${oldValue} to ${newValue}`);
    }
  }
};
</script>
```

---

### **Using `watch` in Composition API (Vue 3)**

```vue
<script setup>
import { ref, watch } from "vue";

const count = ref(0);

watch(count, (newVal, oldVal) => {
  console.log(`Count changed from ${oldVal} to ${newVal}`);
});
</script>
```

✅ Whenever `count` changes, the watcher runs automatically.

---

# **Trailing Questions**

---

## **1️⃣ When should you use `watch` instead of `computed`?**

### How to Answer in an Interview

Explain the **key difference** in use cases.

---

### Answer

|Feature|`computed`|`watch`|
|---|---|---|
|Purpose|For **deriving new reactive values**|For **running side effects**|
|Execution|Caches result until dependency changes|Runs function every time value changes|
|Example|`fullName = firstName + lastName`|API call when `searchQuery` changes|

✅ Use `computed` for **reactive values**, use `watch` for **side effects** like API calls or logging.

---

---

## **2️⃣ How can you watch multiple values in Vue 3?**

### How to Answer in an Interview

Mention that Vue 3 `watch` can take multiple sources as an array.

---

### Answer

Vue 3 allows watching **multiple reactive sources**:

```vue
watch([firstName, lastName], ([newF, newL], [oldF, oldL]) => {
  console.log(`Name changed: ${oldF} ${oldL} → ${newF} ${newL}`);
});
```

✅ This is useful for tracking **changes in multiple properties at once**.

---

---

## **3️⃣ What is deep and immediate watching?**

### How to Answer in an Interview

Explain both options.

---

### Answer

✅ **Deep Watching (`deep: true`)** – Tracks changes inside nested objects or arrays.  
✅ **Immediate Watching (`immediate: true`)** – Executes the watcher **immediately on component load**.

---

### Example

```vue
watch(user, (newVal) => console.log(newVal), { deep: true, immediate: true });
```

✅ Useful for **complex objects** or when an initial action is needed.

---

# **24. What is Routing? How to Use Routing? How Does Routing Work in Vue.js?**

## How to Answer in an Interview

Explain that routing allows users to **navigate between different views or pages without reloading the entire application**. Vue uses **Vue Router**, which enables client-side routing for Single Page Applications (SPAs). Mention the steps to set up routing and how it works under the hood.

---

## Answer

### **What is Routing?**

Routing is the process of **navigating between different pages or views** in a web application.

In SPAs like Vue.js apps, **routing is handled on the client side**, meaning the page is not reloaded. Instead, Vue dynamically loads different components based on the URL.

---

### **How Does Routing Work in Vue.js?**

Vue.js uses the **Vue Router** library, which:  
✅ Maps URLs (paths) to components.  
✅ Uses the **HTML5 History API (`pushState`)** or **hash mode (`#`)**.  
✅ Dynamically updates the view without reloading the page.

---

### **Steps to Use Routing in Vue.js (Vue 3)**

1️⃣ Install Vue Router

```bash
npm install vue-router
```

2️⃣ Create a `router.js` file

```javascript
import { createRouter, createWebHistory } from "vue-router";
import Home from "./pages/Home.vue";
import About from "./pages/About.vue";

const routes = [
  { path: "/", component: Home },
  { path: "/about", component: About }
];

const router = createRouter({
  history: createWebHistory(),
  routes
});

export default router;
```

3️⃣ Use Router in `main.js`

```javascript
import { createApp } from "vue";
import App from "./App.vue";
import router from "./router";

createApp(App).use(router).mount("#app");
```

4️⃣ Add Navigation

```vue
<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
  </nav>
  <router-view></router-view>
</template>
```

✅ Clicking links updates the URL and loads the respective component **without a page reload**.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between history mode and hash mode in Vue Router?**

### How to Answer in an Interview

Explain the **URL difference and SEO benefits**.

---

### Answer

|Mode|URL Example|Description|
|---|---|---|
|**Hash Mode**|`/#/about`|Uses `#` fragment; does not require server config|
|**History Mode**|`/about`|Uses HTML5 History API; needs server setup to handle routes|

✅ **History mode is better for SEO-friendly URLs**, but requires server configuration.

---

---

## **2️⃣ How can you pass parameters in Vue Router?**

### How to Answer in an Interview

Explain both **dynamic routes** and **query parameters**.

---

### Answer

### **Dynamic Route Params**

```javascript
{ path: "/user/:id", component: User }
```

```vue
<router-link :to="`/user/${userId}`">Profile</router-link>
```

✅ Access in component → `this.$route.params.id`

---

### **Query Params**

```vue
<router-link :to="{ path: '/search', query: { q: 'vue' } }">Search</router-link>
```

✅ Access in component → `this.$route.query.q`

---

---

## **3️⃣ Can you have nested routes in Vue.js?**

### How to Answer in an Interview

Explain that Vue Router supports child routes.

---

### Answer

Yes, Vue Router supports **nested routes (child routes)**.

```javascript
const routes = [
  {
    path: "/user",
    component: UserLayout,
    children: [
      { path: "profile", component: UserProfile },
      { path: "settings", component: UserSettings }
    ]
  }
];
```

✅ `<router-view />` inside `UserLayout` renders child components dynamically.

---

# **25. How Do Routers Work in Vue.js? Write a Code Snippet for 5 Modules.**

## How to Answer in an Interview

Explain that Vue Router maps **URLs to components** using a configuration array. When the URL changes, Vue dynamically loads the corresponding component inside `<router-view>` without reloading the page. Then, provide a **code snippet for a router setup with 5 modules.**

---

## Answer

Routers in Vue.js work by:  
✅ Defining **routes** that map paths to components.  
✅ Using the **HTML5 History API** (or hash mode) to handle navigation.  
✅ Rendering the correct component inside `<router-view>` based on the current URL.

Vue Router is **essential for SPAs** because it enables navigation without full page reloads.

---

### **Code Snippet: Router with 5 Modules**

```javascript
// router.js
import { createRouter, createWebHistory } from "vue-router";

// Import components (modules)
import Home from "./pages/Home.vue";
import About from "./pages/About.vue";
import Services from "./pages/Services.vue";
import Contact from "./pages/Contact.vue";
import Profile from "./pages/Profile.vue";

// Define routes
const routes = [
  { path: "/", component: Home },
  { path: "/about", component: About },
  { path: "/services", component: Services },
  { path: "/contact", component: Contact },
  { path: "/profile/:id", component: Profile } // Dynamic route
];

// Create router
const router = createRouter({
  history: createWebHistory(),
  routes
});

export default router;
```

---

### **Usage in App.vue**

```vue
<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/services">Services</router-link>
    <router-link to="/contact">Contact</router-link>
    <router-link :to="`/profile/101`">My Profile</router-link>
  </nav>

  <router-view></router-view>
</template>
```

✅ Vue dynamically loads the respective component based on the URL.

---

# **Trailing Questions**

---

## **1️⃣ How do you create dynamic routes with parameters?**

### How to Answer in an Interview

Explain **`:param` syntax** and how to access it.

---

### Answer

Dynamic routes use `:` followed by a parameter name:

```javascript
{ path: "/profile/:id", component: Profile }
```

✅ Access inside component → `this.$route.params.id` (Options API)  
✅ Vue 3 Composition API → `import { useRoute } from 'vue-router'` → `const route = useRoute(); route.params.id`

---

---

## **2️⃣ How can you add route guards in Vue Router?**

### How to Answer in an Interview

Explain **`beforeEach` guard** for authentication checks.

---

### Answer

Route guards let you run checks before entering a route.

```javascript
router.beforeEach((to, from, next) => {
  if (to.path === "/profile" && !isLoggedIn()) {
    next("/login");
  } else {
    next();
  }
});
```

✅ Useful for **auth checks, permissions, or redirects.**

---

---

## **3️⃣ How can you lazy-load routes in Vue.js?**

### How to Answer in an Interview

Show dynamic import usage.

---

### Answer

Vue Router supports **lazy loading** to improve performance:

```javascript
const About = () => import("./pages/About.vue");

const routes = [
  { path: "/about", component: About }
];
```

✅ The component loads **only when the route is visited.**

---

# **26. What is Vuex and Mixins in Vue.js?**

## How to Answer in an Interview

Explain that **Vuex** is Vue's state management library for managing centralized data across components, while **Mixins** are reusable pieces of logic that can be shared across multiple components. Provide examples for both.

---

## Answer

### **What is Vuex?**

Vuex is a **state management pattern + library** for Vue.js applications. It provides a **centralized store** that holds all application state and ensures predictable state mutations.

Key Concepts in Vuex:  
✅ **State** → Centralized data.  
✅ **Mutations** → Synchronous methods to change state.  
✅ **Actions** → Asynchronous operations (API calls) that commit mutations.  
✅ **Getters** → Computed-like properties for store state.

---

### **What are Mixins?**

Mixins are **reusable blocks of logic** (data, methods, lifecycle hooks) that can be shared across multiple components.

When a component uses a mixin, Vue **merges the mixin’s properties** into the component.

---

## Example

### **Vuex Store Example**

```javascript
// store.js
import { createStore } from "vuex";

export default createStore({
  state: { count: 0 },
  mutations: {
    increment(state) { state.count++; }
  },
  actions: {
    incrementAsync({ commit }) {
      setTimeout(() => commit("increment"), 1000);
    }
  },
  getters: {
    doubleCount: (state) => state.count * 2
  }
});
```

---

### **Mixin Example**

```javascript
// mixins/loggerMixin.js
export default {
  created() {
    console.log("Component Created!");
  },
  methods: {
    greet() { alert("Hello from Mixin!"); }
  }
};
```

```vue
<script>
import loggerMixin from "./mixins/loggerMixin.js";

export default {
  mixins: [loggerMixin]
};
</script>
```

✅ The `loggerMixin` automatically logs a message when the component is created.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between Vuex and Props/Events?**

### How to Answer in an Interview

Explain that Vuex is for **global state**, while props/events are for **parent-child communication.**

---

### Answer

|Feature|Props & Events|Vuex|
|---|---|---|
|Scope|Only parent ↔ child communication|Global state for entire app|
|Use Case|Small apps|Large apps with shared state|
|Data Flow|Manual|Centralized & predictable|

✅ Vuex is best for **state shared by multiple unrelated components**.

---

---

## **2️⃣ Are Mixins still recommended in Vue 3?**

### How to Answer in an Interview

Mention that Vue 3 **prefers Composition API over Mixins.**

---

### Answer

Mixins still work in Vue 3, but **Composition API is preferred** because:  
✅ It avoids name conflicts.  
✅ Groups related logic together inside `setup()`.

✅ Mixins are useful for legacy code or when Composition API isn't possible.

---

---

## **3️⃣ Can Vuex be replaced by Pinia?**

### How to Answer in an Interview

Show awareness of **modern state management trends.**

---

### Answer

Yes. **Pinia** is the recommended state management library for Vue 3.  
✅ Simpler API than Vuex.  
✅ Supports TypeScript better.  
✅ Works with Composition API easily.

---
# **27. How to Share Data Between Components in Vue.js?**

## How to Answer in an Interview

Explain that Vue provides multiple ways to share data between components, depending on their relationship. Cover **props, events, provide/inject, state management (Vuex/Pinia), and custom event buses.**

---

## Answer

Data can be shared between Vue components using **different methods depending on the component hierarchy**:

### ✅ **1. Props (Parent → Child)**

Pass data from parent to child using props.

```vue
<Child :message="parentMsg" />
```

---

### ✅ **2. Events (Child → Parent)**

Emit events from child to parent.

```vue
<!-- Child.vue -->
<button @click="$emit('sendData', 'Hello Parent!')">Send</button>
```

---

### ✅ **3. Provide/Inject (Deep Hierarchies)**

Provide data at a high level and inject it in deeply nested components.

```vue
// Parent.vue
provide() { return { theme: 'dark' } }

// Child.vue
inject: ['theme']
```

---

### ✅ **4. Vuex/Pinia (Global State Management)**

Use Vuex or Pinia for shared state across unrelated components.

---

### ✅ **5. Event Bus (Vue 2)**

A global event bus can emit and listen for events (less common in Vue 3).

---

## Example

```vue
<!-- Parent.vue -->
<Child :count="count" @increment="count++" />

<!-- Child.vue -->
<button @click="$emit('increment')">Increment</button>
```

✅ The parent passes `count` as a prop and listens for the `increment` event.

---

# **Trailing Questions**

---

## **1️⃣ Which method is best for large applications?**

### How to Answer in an Interview

Mention **state management** as the scalable solution.

---

### Answer

- **Props/Events** → Best for small apps with clear parent-child hierarchy.
    
- **Provide/Inject** → Great for deeply nested components.
    
- **Vuex/Pinia** → Best for large apps with **global state shared across multiple components**.
    

✅ **Pinia is the recommended state management library for Vue 3.**

---

---

## **2️⃣ How do you pass data between sibling components?**

### How to Answer in an Interview

Explain that **siblings cannot directly communicate**.

---

### Answer

Sibling components can share data by:  
✅ **Using a common parent (props/events)**  
✅ **Using Vuex/Pinia (global state)**  
✅ **Using an event bus (Vue 2)**

---

### Example Using Parent

```vue
<!-- Parent.vue -->
<ChildA @sendMsg="msg = $event" />
<ChildB :message="msg" />
```

✅ ChildA emits data, Parent stores it, ChildB receives via props.

---

---

## **3️⃣ When should you use `provide/inject` over Vuex?**

### How to Answer in an Interview

Explain **scoping differences.**

---

### Answer

- Use **provide/inject** for **context-specific data**, like a theme or form state in a group of related components.
    
- Use **Vuex/Pinia** for **global state** shared across the entire app.
    

---

# **28. How Can You Improve Performance in Vue.js?**

## How to Answer in an Interview

Explain that Vue.js performance can be improved using **optimization techniques** like lazy loading, code splitting, caching, computed properties, and keeping components small. Mention both **build-time optimizations** and **runtime optimizations**.

---

## Answer

### ✅ **Ways to Improve Performance in Vue.js**

1️⃣ **Use `v-once` for Static Content**  
Prevents re-rendering of elements that never change.

```vue
<p v-once>This will never re-render</p>
```

---

2️⃣ **Use Computed Properties Instead of Methods in Templates**  
Computed properties are cached, reducing unnecessary calculations.

---

3️⃣ **Lazy Loading & Code Splitting**  
Load components only when needed.

```javascript
const About = () => import("./About.vue");
```

---

4️⃣ **Use `<keep-alive>` for Dynamic Components**  
Preserves component state and avoids re-rendering.

```vue
<keep-alive>
  <component :is="currentView" />
</keep-alive>
```

---

5️⃣ **Avoid Unnecessary Reactive Data**  
Store only necessary data in `data()`, avoid making large objects reactive.

---

6️⃣ **Use Key with `v-for`**  
Improves Virtual DOM diffing performance.

```vue
<li v-for="item in items" :key="item.id">{{ item.name }}</li>
```

---

7️⃣ **Use Vue DevTools and Performance Profiling**  
Identify unnecessary re-renders and optimize accordingly.

---

## Example

```vue
<template>
  <div>
    <p v-once>Static Text</p>
    <p>Computed Total: {{ total }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return { price: 100, quantity: 2 };
  },
  computed: {
    total() {
      return this.price * this.quantity;
    }
  }
};
</script>
```

✅ The total **recalculates only when dependencies change**, improving performance.

---

# **Trailing Questions**

---

## **1️⃣ How does `v-once` improve performance?**

### How to Answer in an Interview

Explain that `v-once` **renders an element only once**.

---

### Answer

`v-once` renders an element/component only **once** and skips updates in future re-renders.

```vue
<p v-once>Static Content</p>
```

✅ This avoids unnecessary updates for **static content**, improving performance.

---

---

## **2️⃣ What is the benefit of using computed properties over methods?**

### How to Answer in an Interview

Show that computed properties **cache results**.

---

### Answer

- **Methods** → Run **every time the template re-renders**.
    
- **Computed Properties** → Cached and re-evaluated **only when dependencies change**.
    

✅ This **reduces unnecessary recalculations** and improves efficiency.

---

---

## **3️⃣ How does code-splitting help performance?**

### How to Answer in an Interview

Explain lazy loading.

---

### Answer

Code-splitting (dynamic imports) loads components **only when needed**, reducing initial bundle size and improving page load time.

```javascript
const Dashboard = () => import("./Dashboard.vue");
```

✅ This improves performance **for large applications** by reducing initial load time.

---

# **30. What is Axios.js?**

## How to Answer in an Interview

Explain that Axios is a **promise-based HTTP client** for making API requests from the browser or Node.js. Mention that it simplifies **GET, POST, PUT, DELETE requests**, supports interceptors, and handles JSON data automatically.

---

## Answer

**Axios.js** is a **promise-based HTTP client** that allows developers to make **API requests (RESTful calls)** in both **browser and Node.js** environments.

### **Key Features of Axios:**

✅ Supports **GET, POST, PUT, DELETE** requests.  
✅ Automatically **transforms JSON data**.  
✅ Works with **interceptors** for modifying requests/responses.  
✅ Provides built-in **error handling**.  
✅ Supports **request cancellation and timeout**.

---

### **Why Use Axios in Vue.js?**

- Easier syntax than `fetch()`.
    
- Interceptors for authentication (JWT tokens).
    
- Better error handling.
    
- Automatic JSON conversion.
    

---

## Example

```javascript
import axios from "axios";

axios.get("https://jsonplaceholder.typicode.com/posts")
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```

✅ Axios returns a **promise**, making it easy to use with `.then()` or `async/await`.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between Axios and Fetch API?**

### How to Answer in an Interview

Provide a **comparison table**.

---

### Answer

|Feature|Axios|Fetch API|
|---|---|---|
|JSON Handling|Auto-parses JSON|Must use `res.json()` manually|
|Interceptors|✅ Supported|❌ Not built-in|
|Timeout|✅ Supported|❌ Manual setup needed|
|Error Handling|Throws error for bad status|Must manually check `res.ok`|

✅ Axios is **more developer-friendly**, while Fetch API is **built-in** but less feature-rich.

---

---

## **2️⃣ How do you use Axios with async/await?**

### How to Answer in an Interview

Show a clean `async` function example.

---

### Answer

```javascript
import axios from "axios";

async function fetchData() {
  try {
    const response = await axios.get("https://jsonplaceholder.typicode.com/posts");
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}

fetchData();
```

✅ Using `async/await` makes the code **cleaner and easier to read**.

---

---

## **3️⃣ How can you set a global base URL in Axios?**

### How to Answer in an Interview

Show how to configure Axios defaults.

---

### Answer

```javascript
import axios from "axios";

axios.defaults.baseURL = "https://api.example.com";
axios.defaults.headers.common["Authorization"] = "Bearer token";
```

✅ This avoids repeating the base URL and headers in every request.

---

# **31. Explain Axios. How Does Axios Give Better Support for Vue.js?**

## How to Answer in an Interview

Explain Axios as a **promise-based HTTP client** and highlight why it is preferred in Vue.js applications. Mention features like **automatic JSON parsing, interceptors, and ease of integration with Vue plugins or Vuex for API calls.**

---

## Answer

**Axios** is a **promise-based HTTP client** that makes API calls easier in both browser and Node.js environments. It is widely used in Vue.js because:

✅ It simplifies **GET, POST, PUT, DELETE** requests.  
✅ It automatically **parses JSON responses**.  
✅ It supports **interceptors**, which are useful for authentication tokens.  
✅ It integrates easily with **Vuex/Pinia** for managing API data.  
✅ It allows **global configuration** for base URLs and headers.

---

### **Why Axios is Preferred Over Fetch in Vue.js**

- **Cleaner syntax** with automatic JSON conversion.
    
- **Built-in error handling** for HTTP status codes.
    
- **Interceptors** for handling authentication (JWT tokens).
    
- **Easier cancellation of requests** (useful in Vue components that unmount).
    

---

## Example: Using Axios in Vue 3

```vue
<template>
  <div>
    <button @click="fetchPosts">Load Posts</button>
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return { posts: [] };
  },
  methods: {
    async fetchPosts() {
      try {
        const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
        this.posts = res.data;
      } catch (err) {
        console.error(err);
      }
    }
  }
};
</script>
```

✅ Axios **fetches data, parses it automatically, and updates Vue’s reactive state.**

---

# **Trailing Questions**

---

## **1️⃣ How do you use Axios with Vuex for API calls?**

### How to Answer in an Interview

Show API integration inside Vuex `actions`.

---

### Answer

```javascript
// store.js
import axios from "axios";

export default {
  state: { posts: [] },
  mutations: {
    setPosts(state, posts) { state.posts = posts; }
  },
  actions: {
    async fetchPosts({ commit }) {
      const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
      commit("setPosts", res.data);
    }
  }
};
```

✅ Components just **dispatch the action** → `this.$store.dispatch("fetchPosts")`.

---

---

## **2️⃣ How do Axios interceptors help in Vue apps?**

### How to Answer in an Interview

Show token injection and error handling.

---

### Answer

```javascript
axios.interceptors.request.use((config) => {
  config.headers.Authorization = `Bearer ${localStorage.getItem("token")}`;
  return config;
});
```

✅ This automatically **adds JWT tokens to all API calls.**

---

---

## **3️⃣ How do you cancel Axios requests in Vue?**

### How to Answer in an Interview

Show `AbortController` or Axios cancel token.

---

### Answer

```javascript
const controller = new AbortController();

axios.get("/data", { signal: controller.signal });
controller.abort(); // Cancels the request
```

✅ Useful for avoiding memory leaks when a **component unmounts before the request completes**.

---

# **32. How to Handle REST API Calls in Vue.js? Write an Example.**

## How to Answer in an Interview

Explain that REST API calls in Vue.js can be made using **Axios** or **Fetch API**. Highlight that Axios is commonly used because of its **automatic JSON handling, interceptors, and cleaner syntax**. Then, provide an example of making GET/POST requests in a Vue component.

---

## Answer

Vue.js handles REST API calls using **Axios** (most common) or the native `fetch()` API. Axios is preferred because:

✅ It has a **simpler syntax** than Fetch.  
✅ It **automatically parses JSON responses**.  
✅ It supports **interceptors, request cancellation, and global configuration**.

---

## Example: GET and POST Requests using Axios

```vue
<template>
  <div>
    <button @click="fetchPosts">Load Posts</button>
    <button @click="createPost">Create Post</button>

    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return { posts: [] };
  },
  methods: {
    async fetchPosts() {
      try {
        const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
        this.posts = res.data;
      } catch (err) {
        console.error(err);
      }
    },
    async createPost() {
      try {
        const res = await axios.post("https://jsonplaceholder.typicode.com/posts", {
          title: "New Post",
          body: "This is a new post",
          userId: 1
        });
        console.log("Created:", res.data);
      } catch (err) {
        console.error(err);
      }
    }
  }
};
</script>
```

✅ `fetchPosts()` **retrieves posts**, and `createPost()` **sends a POST request** to create a new post.

---

# **Trailing Questions**

---

## **1️⃣ How can you handle errors in API calls?**

### How to Answer in an Interview

Show try/catch with Axios or `.catch()` method.

---

### Answer

```javascript
try {
  const res = await axios.get("/api/data");
} catch (error) {
  if (error.response) {
    console.log("Server Error:", error.response.data);
  } else {
    console.log("Network Error:", error.message);
  }
}
```

✅ Axios provides detailed error objects (`error.response`, `error.request`, `error.message`).

---

---

## **2️⃣ How do you handle API loading states in Vue?**

### How to Answer in an Interview

Show `loading` state management.

---

### Answer

```vue
<template>
  <div>
    <p v-if="loading">Loading...</p>
    <ul v-else>
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return { posts: [], loading: false };
  },
  methods: {
    async fetchPosts() {
      this.loading = true;
      try {
        const res = await axios.get("/api/posts");
        this.posts = res.data;
      } finally {
        this.loading = false;
      }
    }
  }
};
</script>
```

✅ Always manage **loading state** for better UX.

---

---

## **3️⃣ How do you make multiple API calls in parallel?**

### How to Answer in an Interview

Show `Promise.all()` usage.

---

### Answer

```javascript
const [users, posts] = await Promise.all([
  axios.get("/api/users"),
  axios.get("/api/posts")
]);
```

✅ This **runs both requests in parallel** and waits for both to finish.

---

# **33. How to Fetch Data from API using Vue.js?**

## How to Answer in an Interview

Explain that fetching data in Vue.js is typically done using **Axios** or the **Fetch API**. Highlight the best practice: making API calls inside the **`mounted()` hook (Vue 2)** or **`onMounted()` (Vue 3)** so that the DOM is ready when data loads.

---

## Answer

Vue.js can fetch API data using **Axios** (preferred) or `fetch()`. Axios is easier because it **automatically parses JSON** and provides **better error handling and interceptors**.

---

### **Steps to Fetch API Data in Vue.js**

✅ Install Axios → `npm install axios`  
✅ Import Axios in the component  
✅ Make API call in `mounted()` (Vue 2) or `onMounted()` (Vue 3)  
✅ Store the response in a reactive property

---

## Example (Vue 3 with Axios)

```vue
<template>
  <div>
    <h2>Posts</h2>
    <p v-if="loading">Loading...</p>
    <ul v-else>
      <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import axios from "axios";

export default {
  setup() {
    const posts = ref([]);
    const loading = ref(true);

    onMounted(async () => {
      try {
        const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
        posts.value = res.data;
      } catch (err) {
        console.error(err);
      } finally {
        loading.value = false;
      }
    });

    return { posts, loading };
  }
};
</script>
```

✅ API data is fetched **after the component mounts**, ensuring that the DOM is ready.

---

# **Trailing Questions**

---

## **1️⃣ Why is `mounted()` preferred for API calls instead of `created()`?**

### How to Answer in an Interview

Focus on **DOM availability**.

---

### Answer

- `created()` → Runs **before the DOM is mounted**, good for initial logic but not for DOM-dependent code.
    
- `mounted()` → Runs **after the component is rendered**, so data changes can directly update the DOM.
    

✅ API calls are **best placed in `mounted()` or `onMounted()`**.

---

---

## **2️⃣ How to handle API errors gracefully?**

### How to Answer in an Interview

Show **try/catch with error messages.**

---

### Answer

```javascript
try {
  const res = await axios.get("/api/posts");
} catch (error) {
  alert("Failed to fetch data!");
  console.error(error);
}
```

✅ Always **handle network or server errors properly** for good UX.

---

---

## **3️⃣ Can we cancel API requests when navigating away from a page?**

### How to Answer in an Interview

Show Axios `AbortController` usage.

---

### Answer

```javascript
const controller = new AbortController();

axios.get("/api/data", { signal: controller.signal });
controller.abort(); // Cancels request
```

✅ Prevents memory leaks when **users navigate away before the request finishes**.

---

# **34. Create a CRUD Application in Vue.js (GET, POST, PUT, DELETE)**

## How to Answer in an Interview

Explain that a CRUD app allows users to **Create, Read, Update, and Delete** data via API calls. Mention that in Vue.js, this can be easily implemented using **Axios** along with Vue's reactivity.

---

## Answer

### **Steps to Build a CRUD App in Vue.js**

✅ **GET** – Fetch all items from API.  
✅ **POST** – Add a new item.  
✅ **PUT/PATCH** – Update an existing item.  
✅ **DELETE** – Remove an item.

---

## Example CRUD Component

```vue
<template>
  <div>
    <h2>CRUD App</h2>

    <!-- Create -->
    <input v-model="newPost" placeholder="Enter title" />
    <button @click="createPost">Add Post</button>

    <!-- Read -->
    <ul>
      <li v-for="post in posts" :key="post.id">
        {{ post.title }}
        <button @click="updatePost(post.id)">Edit</button>
        <button @click="deletePost(post.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return { posts: [], newPost: "" };
  },
  mounted() {
    this.fetchPosts();
  },
  methods: {
    async fetchPosts() {
      const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
      this.posts = res.data.slice(0, 5); // Limit to 5 posts
    },
    async createPost() {
      const res = await axios.post("https://jsonplaceholder.typicode.com/posts", {
        title: this.newPost,
        body: "Content here",
        userId: 1
      });
      this.posts.push(res.data);
      this.newPost = "";
    },
    async updatePost(id) {
      const res = await axios.put(`https://jsonplaceholder.typicode.com/posts/${id}`, {
        title: "Updated Title",
        body: "Updated content",
        userId: 1
      });
      this.posts = this.posts.map(post => post.id === id ? res.data : post);
    },
    async deletePost(id) {
      await axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`);
      this.posts = this.posts.filter(post => post.id !== id);
    }
  }
};
</script>
```

✅ This app **fetches, adds, updates, and deletes posts** using Axios.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between PUT and PATCH in API calls?**

### How to Answer in an Interview

Explain **full vs partial updates**.

---

### Answer

|Method|Purpose|
|---|---|
|**PUT**|Replaces the entire resource.|
|**PATCH**|Updates only specific fields.|

✅ Example:

- PUT → `{ name: "John", age: 30 }` (full object)
    
- PATCH → `{ age: 30 }` (only updates age)
    

---

---

## **2️⃣ How do you handle API errors in CRUD apps?**

### How to Answer in an Interview

Show `try/catch` with proper messages.

---

### Answer

```javascript
try {
  const res = await axios.post("/api/posts", data);
} catch (err) {
  alert("Error occurred: " + err.message);
}
```

✅ Always show meaningful error messages to users.

---

---

## **3️⃣ How to optimize API calls in a CRUD app?**

### How to Answer in an Interview

Explain **caching and batching**.

---

### Answer

- Use **state management (Vuex/Pinia)** to avoid unnecessary API calls.
    
- Use **`Promise.all()`** for parallel API calls.
    
- Implement **debouncing** for search fields.
    
- Use **lazy loading / pagination** for large lists.
    

---

# **35. Can You Write a Sample Code Snippet to Access All REST Operations?**

## How to Answer in an Interview

Explain that REST operations typically include **GET, POST, PUT/PATCH, and DELETE**, and demonstrate how to perform each operation in a single code example using **Axios**.

---

## Answer

Below is an example of **all four REST operations (CRUD)** in Vue.js using Axios:

---

## **Code Snippet**

```javascript
import axios from "axios";

const API_URL = "https://jsonplaceholder.typicode.com/posts";

// ✅ GET – Read Data
async function getPosts() {
  const res = await axios.get(API_URL);
  console.log("GET:", res.data);
}

// ✅ POST – Create Data
async function createPost() {
  const res = await axios.post(API_URL, {
    title: "New Post",
    body: "This is a new post",
    userId: 1
  });
  console.log("POST:", res.data);
}

// ✅ PUT – Update Data
async function updatePost(id) {
  const res = await axios.put(`${API_URL}/${id}`, {
    title: "Updated Post",
    body: "Updated content",
    userId: 1
  });
  console.log("PUT:", res.data);
}

// ✅ DELETE – Delete Data
async function deletePost(id) {
  await axios.delete(`${API_URL}/${id}`);
  console.log(`Deleted post with ID: ${id}`);
}

// Example Usage
getPosts();
createPost();
updatePost(1);
deletePost(1);
```

✅ This snippet **shows how to perform all REST operations** with Axios.

---

# **Trailing Questions**

---

## **1️⃣ What is the difference between PUT and PATCH in this context?**

### How to Answer in an Interview

Highlight **complete vs partial updates.**

---

### Answer

- **PUT** → Replaces the entire object with the provided data.
    
- **PATCH** → Updates only the specified fields in the object.
    

Example:

```javascript
axios.patch(`${API_URL}/1`, { title: "Only Title Updated" });
```

✅ `PATCH` is **lighter and safer** for partial updates.

---

---

## **2️⃣ How can you make multiple REST calls in parallel?**

### How to Answer in an Interview

Show `Promise.all()` usage.

---

### Answer

```javascript
Promise.all([
  axios.get("/users"),
  axios.get("/posts"),
  axios.get("/comments")
]).then(([users, posts, comments]) => {
  console.log(users.data, posts.data, comments.data);
});
```

✅ Improves performance by **executing requests simultaneously**.

---

---

## **3️⃣ How can you handle authentication with Axios?**

### How to Answer in an Interview

Show global headers setup.

---

### Answer

```javascript
axios.defaults.headers.common["Authorization"] = `Bearer ${localStorage.getItem("token")}`;
```

✅ This **automatically includes JWT tokens** in every API request.

---

# **36. How to Handle a CORS Policy Issue? Write Code.**

## How to Answer in an Interview

Explain that **CORS (Cross-Origin Resource Sharing)** issues occur when a frontend app on one domain tries to access an API hosted on another domain without proper permissions. The solution is to **configure the backend server to allow CORS** or use a **proxy** in development.

---

## Answer

### **What is CORS?**

CORS is a **security feature in browsers** that blocks API calls to different domains unless the server explicitly allows it using the `Access-Control-Allow-Origin` header.

---

### **Ways to Handle CORS Issues in Vue.js**

✅ **1. Enable CORS on the Server (Preferred Solution)**  
Add this header on the API server response:

```
Access-Control-Allow-Origin: *
```

---

✅ **2. Use a Proxy in Vue Development**  
Set up a proxy in `vue.config.js` to bypass CORS during local development.

```javascript
// vue.config.js
module.exports = {
  devServer: {
    proxy: {
      "/api": {
        target: "https://example.com",
        changeOrigin: true
      }
    }
  }
};
```

✅ Then call API as `/api/users` instead of full URL.

---

✅ **3. Use Axios with Proxy URL (Development Only)**

```javascript
import axios from "axios";

axios.get("/api/data").then(res => console.log(res.data));
```

✅ The proxy **forwards the request** to the real API server.

---

✅ **4. Use a CORS Proxy (Not Recommended for Production)**

```javascript
axios.get("https://cors-anywhere.herokuapp.com/https://example.com/api");
```

⚠️ Not secure for production use.

---

# **Trailing Questions**

---

## **1️⃣ Can we fix CORS from the frontend alone?**

### How to Answer in an Interview

Be clear that **frontend cannot override CORS**.

---

### Answer

❌ No. Browsers block cross-origin requests **before they reach frontend JS**, so **CORS must be fixed on the server** or using a proxy.

✅ Any client-side hack (like using a proxy) **only works in development**.

---

---

## **2️⃣ How do you handle CORS with authentication?**

### How to Answer in an Interview

Mention `Access-Control-Allow-Credentials`.

---

### Answer

For authenticated requests (cookies/JWT tokens), server must allow credentials:

```
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Credentials: true
```

Axios must also be configured:

```javascript
axios.defaults.withCredentials = true;
```

✅ This allows **cross-site cookies** for login sessions.

---

---

## **3️⃣ What is the difference between preflight and simple CORS requests?**

### How to Answer in an Interview

Explain **OPTIONS request behavior.**

---

### Answer

- **Simple Request** → GET/POST with standard headers (no preflight).
    
- **Preflight Request** → Browser sends an **OPTIONS request** first to check if the API allows CORS.
    

✅ Preflight happens for **custom headers, PUT, DELETE, or JSON payloads.**

---

# **37. HTTP vs HTTPS? How Do You Handle REST API Calls?**

## How to Answer in an Interview

Explain the difference between **HTTP and HTTPS** (security via SSL/TLS encryption). Then describe how REST API calls are made in Vue.js (using Axios or Fetch) and why HTTPS is always preferred in production.

---

## Answer

### **HTTP vs HTTPS**

|Feature|HTTP|HTTPS|
|---|---|---|
|Security|No encryption, data sent in plain text|Encrypted using SSL/TLS|
|Port|80|443|
|SEO|Less secure, not SEO-friendly|Secure, preferred by search engines|
|Use Case|Local testing or insecure APIs|Production apps, sensitive data|

✅ **Always use HTTPS** in production to protect user data.

---

### **How to Handle REST API Calls in Vue.js?**

1️⃣ Install Axios

```bash
npm install axios
```

2️⃣ Use Axios or Fetch API to make **GET, POST, PUT, DELETE** calls.

---

### **Example API Calls Using Axios**

```javascript
import axios from "axios";

const API = axios.create({
  baseURL: "https://api.example.com", // Always HTTPS in production
  headers: { "Content-Type": "application/json" }
});

// GET
API.get("/posts").then(res => console.log(res.data));

// POST
API.post("/posts", { title: "New Post" });

// PUT
API.put("/posts/1", { title: "Updated Post" });

// DELETE
API.delete("/posts/1");
```

✅ Axios is preferred over Fetch because it **auto-parses JSON, supports interceptors, and handles errors easily.**

---

# **Trailing Questions**

---

## **1️⃣ Why is HTTPS mandatory for modern applications?**

### How to Answer in an Interview

Explain **security, SEO, and browser restrictions.**

---

### Answer

- Encrypts communication → Prevents data theft (man-in-the-middle attacks).
    
- Required for features like **Service Workers and HTTP/2**.
    
- Browsers block certain APIs (geolocation, push notifications) without HTTPS.
    

✅ **HTTPS is essential for all production APIs.**

---

---

## **2️⃣ How can you secure API calls in Vue.js?**

### How to Answer in an Interview

Mention **authentication, HTTPS, and headers.**

---

### Answer

✅ Use **HTTPS** to prevent data leaks.  
✅ Use **JWT tokens or OAuth** for authentication.  
✅ Set up **interceptors** in Axios to attach tokens:

```javascript
API.interceptors.request.use(config => {
  config.headers.Authorization = `Bearer ${localStorage.getItem("token")}`;
  return config;
});
```

---

---

## **3️⃣ How do you handle sensitive API keys in Vue.js?**

### How to Answer in an Interview

Clarify that **API keys should never be exposed in frontend.**

---

### Answer

- Store keys in a **backend server** or use environment variables (`.env`).
    
- Vue’s `.env.production` can hold public variables (`VITE_...`).
    
- Never expose **secret keys** in frontend code.
    

---

# **38. Axios vs Fetch – Which One is Faster, Safer, and More Efficient? (With Code)**

## How to Answer in an Interview

Explain that **both Axios and Fetch are used for API calls**, but Axios provides **more features out-of-the-box**, while Fetch is **native to browsers**. Then, compare both with examples.

---

## Answer

### **Axios vs Fetch – Comparison**

|Feature|Axios ✅|Fetch ❌|
|---|---|---|
|JSON Handling|Auto-parses JSON|Must call `res.json()` manually|
|Interceptors|✅ Built-in|❌ Manual implementation|
|Error Handling|Rejects on HTTP errors|Must check `res.ok` manually|
|Request Cancellation|Built-in Cancel Token / Abort|Requires `AbortController`|
|Node.js Support|✅ Works in Node.js too|❌ Browser only|

✅ **Axios is more developer-friendly and efficient for larger apps.**  
✅ **Fetch is lighter and native (no dependency).**

---

### **Code Comparison**

#### ✅ **Axios Example**

```javascript
import axios from "axios";

async function getDataAxios() {
  try {
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
    console.log("Axios Data:", res.data);
  } catch (err) {
    console.error("Axios Error:", err);
  }
}

getDataAxios();
```

---

#### ✅ **Fetch Example**

```javascript
async function getDataFetch() {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    if (!res.ok) throw new Error("HTTP Error " + res.status);
    const data = await res.json();
    console.log("Fetch Data:", data);
  } catch (err) {
    console.error("Fetch Error:", err);
  }
}

getDataFetch();
```

---

# **Trailing Questions**

---

## **1️⃣ Which one is faster, Axios or Fetch?**

### How to Answer in an Interview

Say **performance is almost identical**.

---

### Answer

- Axios and Fetch **both use the browser’s networking layer**, so speed is nearly identical.
    
- Axios **feels faster** because it has **automatic JSON parsing, better error handling, and interceptors**, reducing boilerplate code.
    

---

---

## **2️⃣ Why is Axios considered safer for production apps?**

### How to Answer in an Interview

Explain **error handling and interceptors.**

---

### Answer

- Axios **rejects promises on HTTP errors**, making error handling easier.
    
- It allows **request/response interceptors** for **authentication tokens, retries, and logging.**
    
- It supports **timeouts and cancellation**, preventing memory leaks.
    

---

---

## **3️⃣ When should you prefer Fetch over Axios?**

### How to Answer in an Interview

Explain **lightweight apps and no dependency scenarios.**

---

### Answer

Use Fetch when:  
✅ You want **zero dependencies** in small projects.  
✅ You don’t need interceptors or advanced features.  
✅ You are working in an **environment where installing packages is not possible.**

---

# **39. Explain Your Current Project (Vue.js Project Explanation)**

## How to Answer in an Interview

Provide a **clear and structured explanation** of your project, focusing on:  
✅ **Overview** – What the app does.  
✅ **Tech Stack** – Vue.js version, libraries (Vue Router, Vuex/Pinia, Axios, etc.).  
✅ **Your Role** – What you implemented.  
✅ **Challenges & Solutions** – Any key problems you solved.

---

## Answer (Sample Response)

**Project Name:** _Smart Task Manager (SPA)_

**Overview:**  
I developed a **Single Page Application** for managing tasks, where users can create, update, delete, and filter tasks. It also includes user authentication, API-based CRUD operations, and a responsive UI.

**Tech Stack:**

- **Frontend:** Vue 3, Vue Router, Pinia (state management), Axios for API calls
    
- **Backend (API):** Node.js + Express + MongoDB
    
- **Features:**  
    ✅ CRUD for tasks (create, update, delete, mark as complete)  
    ✅ Authentication (JWT-based login)  
    ✅ Search and filter functionality  
    ✅ Pagination and lazy loading for better performance
    

**My Role:**

- Developed reusable Vue components (TaskList, TaskForm, TaskItem).
    
- Integrated REST APIs with Axios and handled error states.
    
- Implemented Vue Router for navigation and Pinia for state management.
    
- Improved performance by using code-splitting and `<keep-alive>` for dynamic components.
    

**Challenges Solved:**

- Handled API error states gracefully using Axios interceptors.
    
- Optimized API calls using debouncing for search.
    
- Used `watch` and `computed` properties to reduce unnecessary re-renders.
    

---

# **Trailing Questions**

---

## **1️⃣ What was the biggest challenge you faced in this project?**

### How to Answer in an Interview

Pick a **real technical challenge** and show your solution.

---

### Answer

The biggest challenge was **handling API latency and optimizing performance** when displaying large task lists.

✅ **Solution:**

- Implemented **pagination and lazy loading** to fetch tasks in chunks.
    
- Used **debounce** on search input to reduce API calls.
    
- Cached responses in Pinia store to avoid redundant API requests.
    

---

---

## **2️⃣ Which Vue.js features did you use the most?**

### How to Answer in an Interview

Mention **important features** you worked with.

---

### Answer

I used:  
✅ **Vue Router** for navigation.  
✅ **Pinia** for global state management.  
✅ **Axios interceptors** for attaching tokens to requests.  
✅ **Computed properties and watchers** for reactive UI updates.  
✅ **Dynamic components with `<keep-alive>`** for better performance.

---

---

## **3️⃣ How would you improve this project further?**

### How to Answer in an Interview

Show that you can think ahead.

---

### Answer

- Add **server-side rendering (SSR) with Nuxt.js** for better SEO.
    
- Implement **unit tests with Vue Test Utils + Jest**.
    
- Use **WebSockets** for real-time task updates.
    
- Improve **accessibility (a11y)** and **performance audits** using Lighthouse.
    

---

# **40. Explain All the Modules of the Project You Contributed To**

## How to Answer in an Interview

Give a **module-wise breakdown** of your project, highlighting your contributions to each. Use **clear points**, showing both **technical implementation and problem-solving skills.**

---

## Answer (Sample Response)

My project was a **Smart Task Manager (SPA)** built with Vue 3, Vue Router, Pinia, and Axios. I contributed to the following **key modules**:

---

### **1️⃣ Authentication Module**

✅ Implemented **login, registration, and JWT-based authentication**.  
✅ Used Axios interceptors to **attach tokens automatically to API calls**.  
✅ Redirected users with **Vue Router navigation guards**.

---

### **2️⃣ Task Management (CRUD) Module**

✅ Built **TaskList, TaskItem, and TaskForm components**.  
✅ Implemented **Create, Read, Update, Delete (CRUD)** functionality using Axios.  
✅ Used **computed properties and watchers** to optimize UI updates.

---

### **3️⃣ Search & Filter Module**

✅ Added **search with debouncing** to reduce API calls.  
✅ Implemented filters like **All Tasks, Completed Tasks, Pending Tasks** using computed properties.

---

### **4️⃣ State Management Module**

✅ Integrated **Pinia store** to manage global state for tasks and authentication.  
✅ Used **actions for API calls** and **getters for derived state**.  
✅ Optimized performance by **caching previously fetched API data**.

---

### **5️⃣ Routing & Navigation Module**

✅ Set up **Vue Router with nested routes and dynamic params**.  
✅ Used **navigation guards** for protecting authenticated routes.  
✅ Configured **lazy loading for better performance**.

---

---

# **Trailing Questions**

---

## **1️⃣ Which module was the most challenging?**

### How to Answer in an Interview

Pick a **real challenge** and explain your solution.

---

### Answer

The **Task Management Module** was the most challenging because I had to **sync local state with API responses efficiently**.

✅ I solved this by:

- Using **optimistic UI updates** (updating UI before API confirmation).
    
- Implementing a **retry mechanism for failed requests**.
    
- Caching API data in Pinia to avoid redundant API calls.
    

---

---

## **2️⃣ How did you ensure reusability in components?**

### How to Answer in an Interview

Show your **component-driven approach.**

---

### Answer

- Created **reusable form components** with props and emits.
    
- Used **slots** for flexible content inside components.
    
- Broke down UI into **small, functional components** to improve maintainability.
    

---

---

## **3️⃣ How did you optimize API calls across modules?**

### How to Answer in an Interview

Show Axios + Pinia best practices.

---

### Answer

- Configured **Axios base URL and interceptors** globally.
    
- Used **Pinia store actions** for API calls to avoid duplication.
    
- Implemented **debouncing and pagination** for API-heavy modules.
    

---

# **41. How Many Components Did You Create for the Project?**

## How to Answer in an Interview

Explain that you built the project using **modular and reusable components**. Highlight **key components** you created, their purpose, and how you ensured **reusability**.

---

## Answer (Sample Response)

In my **Smart Task Manager (SPA)** project, I created around **12 reusable components**, grouped into different categories:

---

### **📌 UI Components (Reusable Across App)**

✅ **Button.vue** – Custom button with dynamic props (`type`, `size`, `disabled`).  
✅ **Modal.vue** – Reusable modal with slot-based content.  
✅ **InputField.vue** – Reusable input field with validation props.

---

### **📌 Task-Related Components**

✅ **TaskList.vue** – Displays a list of tasks using `v-for`.  
✅ **TaskItem.vue** – Represents a single task with edit/delete buttons.  
✅ **TaskForm.vue** – Used for creating/updating tasks.

---

### **📌 Auth Components**

✅ **LoginForm.vue** – Handles user login.  
✅ **RegisterForm.vue** – Handles user registration.

---

### **📌 Layout Components**

✅ **Navbar.vue** – Top navigation bar with links.  
✅ **Sidebar.vue** – Sidebar menu for authenticated users.

---

### **📌 Utility Components**

✅ **Pagination.vue** – For navigating through tasks.  
✅ **Loader.vue** – For displaying loading state.

---

**Total Components:** **12+**  
I ensured **reusability** by:

- Using **props and emits** for parent-child communication.
    
- Using **slots** for dynamic content.
    
- Keeping components **small and focused** on a single responsibility.
    

---

# **Trailing Questions**

---

## **1️⃣ How did you ensure components were reusable?**

### How to Answer in an Interview

Show your approach to **flexibility and scalability**.

---

### Answer

- Designed components with **props for customization**.
    
- Used **emits for event communication**.
    
- Added **slots** to allow flexible child content.
    
- Created **base components (BaseButton, BaseInput)** for common UI elements.
    

---

---

## **2️⃣ Which component had the most logic?**

### How to Answer in an Interview

Pick one that shows **state management and event handling**.

---

### Answer

The **TaskForm.vue** component had the most logic because it handled:  
✅ Two-way binding (`v-model`) for form inputs.  
✅ Validation before API calls.  
✅ Both create and update logic, depending on the mode.

---

---

## **3️⃣ How did you manage communication between components?**

### How to Answer in an Interview

Show usage of **props, emits, and store**.

---

### Answer

- **Props** → Passed data from parent to child (e.g., `TaskList → TaskItem`).
    
- **Emits** → Used `$emit` for child-to-parent events (e.g., delete event).
    
- **Pinia Store** → Used for sharing state between unrelated components.
    

---

🔥 Next → **“How Vue.js Components Are Changed to HTML File and Viewed in Browser?”** – shall I continue?