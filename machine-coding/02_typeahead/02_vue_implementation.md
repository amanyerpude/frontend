
--------------------------------------------------------------------------
# 🔵 Stage 0 — FAANG-Level Requirement Framing (Vue Context)

### 🎤 Interviewer says:

> “Build an AutoComplete component using Vue.”

That’s intentionally vague.

As a 6 YOE engineer, you DO NOT start coding.

You clarify.

---

# 🧠 1️⃣ Clarify Functional Scope

You should ask:

### Data Source

- Is data local or remote?
    
- Do we control API?
    
- Is it prefix search or full-text?
    

For our practice:

- Simulated async API
    
- Prefix-based search
    
- Case-insensitive
    
- Limit to 5 results
    

---

### Result Constraints

- Maximum suggestions?
    
- Can list grow indefinitely?
    

We define:

- Maximum 5 suggestions
    
- Later discuss virtualization
    

---

### Selection Behavior

- On click → fill input?
    
- Should dropdown close?
    
- Should it emit event to parent?
    

We define:

- Fill input
    
- Close dropdown
    
- Later we will emit `select` event (reusability stage)
    

---

### Empty States

We define three explicit states:

|Scenario|UI|
|---|---|
|Empty input|Hide dropdown|
|No matches|Show “No results found”|
|Error|Show “Something went wrong”|

---

# 🧠 2️⃣ Non-Functional Requirements

Senior engineers think beyond UI.

### Performance

- Avoid API spam → debounce
    
- Avoid redundant calls → cache
    
- Avoid stale responses → race handling
    

---

### Accessibility

We will eventually support:

- ARIA combobox
    
- Keyboard navigation
    
- Screen reader compatibility
    

---

### Scalability

What if:

- 10k results?
    
- Slow network?
    
- API latency 3s?
    
- Mobile device?
    

We will discuss later.

---

# 🧠 3️⃣ Vue-Specific Architectural Decisions

Before writing Vue code, we decide:

### API Style

We use:

> Vue 3 + Composition API + `<script setup>`

Why?

- Modern
    
- Cleaner
    
- Reusable logic extraction
    
- Closer to React hook mental model
    

---

### Component Structure

For now:  
Everything inside `App.vue`.

Later:  
We extract into `AutoComplete.vue`.

---

### State Strategy

We will use:

- `ref()` → primitive reactive state
    
- `computed()` → derived state
    
- `watch()` → side effects (debounce)
    
- `onMounted()` → lifecycle
    
- `Map` → caching
    

No external libraries.

---

# 🧠 4️⃣ Incremental Plan (Strict Discipline)

We will implement in layers:

### Stage 1

Basic UI + local reactive filtering

### Stage 2

Click selection

### Stage 3

Async fetch simulation

### Stage 4

Debounce with `watch`

### Stage 5

Race condition handling

### Stage 6

Caching (Map)

### Stage 7

Keyboard navigation

### Stage 8

Accessibility

### Stage 9

Refactor into reusable composable

Same maturity ladder as vanilla version.

---

# 🧠 5️⃣ Mental Model Shift (Important)

In Vanilla JS:  
You control DOM manually.

In Vue:  
You control state.  
Vue controls DOM.

That means:

- No document.querySelector
    
- No manual class toggling
    
- No manual event delegation
    
- Everything flows from reactive state
    

If this mindset is wrong, Vue implementation becomes messy.

---

# 🔎 Before We Proceed

Let me confirm:

You want Stage 1 to be:

- Extremely detailed
    
- Fully commented
    
- Explained line-by-line
    
- With reasoning about Vue reactivity
    

Correct?

If yes, say:

**“Proceed to Stage 1 (detailed mode)”**

And we begin properly.

--------------------------------------------------------------------------

Excellent.  
Now we begin **Stage 1 — Detailed Mode (Vue 3 + Composition API)**.

Slow. Clean. Structured. Senior-level clarity.

---

# 🟢 Stage 1 — Basic Reactive Filtering (No Async Yet)

## 🎯 Goal

We will build:

- Input box
    
- Reactive `query`
    
- Local static dataset
    
- Computed filtered results
    
- Limit to 5
    
- Show dropdown only when needed
    
- Handle empty + no-result states
    

No async.  
No debounce.  
No keyboard.  
No optimization.

Just correctness + clean reactivity.

---

# 🧠 Mental Model Before Code

In Vanilla JS:

- We listened to `input` event
    
- We manually filtered
    
- We manually updated DOM
    

In Vue:

- `v-model` tracks input
    
- `computed()` reacts automatically
    
- Template re-renders automatically
    

We move from **imperative DOM control**  
to **declarative state-driven UI**.

---

# 📄 `App.vue`

Read comments carefully.

---

## 🔹 Template Section

```vue
<template>
  <div class="autocomplete-container">

    <!--
      v-model creates two-way binding.
      query.value updates automatically when user types.
      No manual event listener required.
    -->
    <input
      type="text"
      v-model="query"
      placeholder="Search..."
      autocomplete="off"
    />

    <!--
      We render suggestions only if:
      1. query is not empty
      2. filteredResults has items

      Vue automatically tracks dependencies.
    -->
    <ul
      v-if="query && filteredResults.length"
      class="suggestions"
    >
      <!--
        v-for renders each item reactively.
        :key is important for Vue’s diffing algorithm.
      -->
      <li
        v-for="item in filteredResults"
        :key="item"
      >
        {{ item }}
      </li>
    </ul>

    <!-- No Results State -->
    <ul
      v-else-if="query && !filteredResults.length"
      class="suggestions"
    >
      <li class="no-results">
        No results found
      </li>
    </ul>

  </div>
</template>
```

---

## 🔹 Script Section (Composition API)

```vue
<script setup>
import { ref, computed } from "vue";

/*
  ref() creates reactive primitive state.

  query.value holds the actual string.
  In template, Vue automatically unwraps .value.
*/
const query = ref("");

/*
  Static dataset for Stage 1.
  Later this will be replaced with async API.
*/
const data = [
  "Apple",
  "Banana",
  "Mango",
  "Orange",
  "Pineapple",
  "Grapes",
  "Watermelon",
  "Papaya",
  "Kiwi",
  "Strawberry"
];

/*
  computed() creates derived reactive state.

  It automatically re-runs whenever query.value changes.

  No watcher required.
  No manual filtering inside event listener.
*/
const filteredResults = computed(() => {
  const q = query.value.trim().toLowerCase();

  // If empty input, return empty array
  if (!q) return [];

  // Prefix match (case-insensitive)
  return data
    .filter(item =>
      item.toLowerCase().startsWith(q)
    )
    .slice(0, 5); // limit to 5 suggestions
});
</script>
```

---

## 🔹 Style Section

```vue
<style>
.autocomplete-container {
  width: 300px;
  margin: 100px auto;
  position: relative;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
}

.suggestions {
  list-style: none;
  margin: 0;
  padding: 0;
  border: 1px solid #ccc;
  border-top: none;
  background: white;
  max-height: 200px;
  overflow-y: auto;
}

.suggestions li {
  padding: 10px;
}

.no-results {
  color: gray;
}
</style>
```

---

# 🧠 Deep Explanation (Senior Level)

### 1️⃣ Why `ref()` instead of `reactive()`?

Because:

- We only need a primitive string.
    
- `ref()` is lighter and clearer.
    
- `reactive()` is better for objects.
    

---

### 2️⃣ Why `computed()` instead of `watch()`?

Because:

- Filtering is pure derivation.
    
- No side effects.
    
- `computed()` caches automatically.
    
- More declarative.
    

Senior engineers prefer computed when possible.

---

### 3️⃣ Why not manually hide dropdown?

We use:

```vue
v-if="query && filteredResults.length"
```

This means:  
UI is controlled by state.  
No class toggling.  
No DOM manipulation.

Cleaner and safer.

---

### 4️⃣ Why prefix match instead of includes?

Prefix:

- Faster
    
- Common UX pattern
    
- More predictable
    

We can extend later.

---

# 🧪 What You Should Test

Type:

- A
    
- B
    
- Z
    
- Clear input
    

Check:

- Dropdown hides correctly
    
- No results state shows
    
- Max 5 items
    
- No console errors
    

---

# 🧠 What We Achieved

✔ Reactive filtering  
✔ Clean state-driven UI  
✔ No manual DOM  
✔ Clean separation of concerns  
✔ Vue reactivity fundamentals

---

# 🚦 Stop Here

Understand this stage deeply.

This is the foundation.

Next stage will introduce:

👉 Click selection  
👉 Controlled dropdown state  
👉 Proper closing behavior

Say:

**“Stage 1 complete”**

and we layer the next piece properly.

--------------------------------------------------------------------------

