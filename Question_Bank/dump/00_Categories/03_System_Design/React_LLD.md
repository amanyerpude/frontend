# React Low-Level Design (LLD)

## 🚀 React.js Low-Level Design (LLD) Interview Questions

**[Source: dump_three.md, Lines 11-75]**

### 1️⃣ Infinite Scrolling

- State management for pagination + loaders
- Intersection Observer vs Scroll Events

### 2️⃣ Debounced Search Input

- Avoiding race conditions in APIs
- Caching past results for performance

### 3️⃣ Virtualized List

- Dynamic vs fixed item heights
- Maintaining scroll position

### 4️⃣ Custom Hook for Data Fetching

- Request deduplication
- Background refetching & optimistic updates

### 5️⃣ Accessible Modal Component

- Escape key, backdrop handling
- Preventing body scroll

### 6️⃣ Global State Without Libraries

- Context + useReducer
- Async middleware (logging, API calls)

### 7️⃣ Form Validation System

- Real-time validation + error messages
- Conditional fields, dynamic schemas

### 8️⃣ Drag & Drop for Lists

- Smooth visual feedback
- Touch device & accessibility support

### 9️⃣ Notification/Toast System

- Multiple notification lifecycles
- Types + priority handling

### 🔟 Multi-Step Form Wizard

- State across steps
- Draft saving + resume later

---

## 🧱 React Low-Level Design (LLD) Interview Questions That Truly Test Depth

**[Source: dump_five.md, Lines 115-220]**

### 🧠 Virtualized Lists

- How would you render 100,000+ rows efficiently?
- Would you use a library or build your own?
- How do you handle dynamic row heights?

### 📊 Reusable Table Component

- Sorting, filtering, pagination, resizing — how would you design this?
- How do you separate logic vs. UI?
- How would you expose APIs to parent components?

### 🔔 Notification System

- Queuing toasts with auto-dismiss + priority
- Context vs Redux — what fits better?
- Accessibility: Have you thought about screen readers?

### 🔐 Role-Based Routing + Code Splitting

- Lazy load routes based on roles (Admin/User)?
- Per-route fallback UIs with React.Suspense?
- How do you guard protected routes?

### 🪝 State Sync with LocalStorage

- Sync React state with localStorage across tabs?
- Handle JSON parsing edge cases?
- Hydration-safe hooks?

### ⚠️ Global Error Boundaries

- App-wide + page-level error boundaries?
- Show different fallbacks for 404, 500, network errors?
- Any best practices for logging?

### 📝 Collaborative Text Editor (like Google Docs)

- Real-time cursor + typing indicators?
- Handling sync conflicts?
- Would you use OT/CRDT?

### 🎨 Theme Switcher (Light/Dark)

- Persist theme across sessions/devices?
- CSS variables vs CSS-in-JS?
- Global vs per-component theming?

### ↩️ Undo/Redo Mechanism

- What data structure would you use?
- Performance for large history stacks?

### ♿️ Accessibility (a11y) at Scale

- Enforce WCAG across teams?
- Reusable accessible components?
- Tools like axe-core or NVDA?


