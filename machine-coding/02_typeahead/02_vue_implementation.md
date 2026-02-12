
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

Perfect.  
Now we move to **Stage 2 — Click Selection + Controlled Dropdown State**.

We’re still disciplined.

No async yet.  
No debounce.  
No optimization.

We now refine behavior.

---

# 🟢 Stage 2 — Click Selection & Proper Dropdown Control

## 🎯 Goal

We will add:

- Click on suggestion → populate input
    
- Close dropdown after selection
    
- Prevent dropdown from showing when selection is made
    
- Clean state control (not hacky)
    

---

# 🧠 Important Design Change

Right now dropdown visibility depends on:

```vue
v-if="query && filteredResults.length"
```

But this is insufficient.

Why?

Because if user clicks a suggestion:

- `query` still has value
    
- `filteredResults` still matches
    
- Dropdown would reappear immediately
    

So we need **explicit dropdown state control**.

Senior engineers always separate:

> Data state  
> UI visibility state

---

# 🧠 Step 1 — Add Dropdown Visibility State

Inside `<script setup>`:

```js
const isOpen = ref(false);
```

Now dropdown visibility will depend on `isOpen`.

---

# 🧠 Step 2 — Open Dropdown When Typing

Instead of relying purely on computed rendering,  
we control it with a watcher.

Add:

```js
import { watch } from "vue";

watch(query, (newValue) => {
  if (newValue.trim()) {
    isOpen.value = true;
  } else {
    isOpen.value = false;
  }
});
```

Now:

- When user types → dropdown opens
    
- When input cleared → dropdown closes
    

---

# 🧠 Step 3 — Update Template Visibility Conditions

Modify template:

```vue
<ul
  v-if="isOpen && filteredResults.length"
  class="suggestions"
>
```

And:

```vue
<ul
  v-else-if="isOpen && !filteredResults.length"
  class="suggestions"
>
```

Now dropdown is controlled explicitly.

---

# 🧠 Step 4 — Add Click Selection Handler

Inside `<script setup>`:

```js
function selectItem(item) {
  query.value = item;   // Populate input
  isOpen.value = false; // Close dropdown
}
```

---

# 🧠 Step 5 — Attach Click in Template

Modify `li`:

```vue
<li
  v-for="item in filteredResults"
  :key="item"
  @click="selectItem(item)"
>
  {{ item }}
</li>
```

---

# 🧠 Why This Is Better Than Vanilla

In vanilla:

- We had to manually clear innerHTML
    
- Manually toggle class
    
- Manually manage state
    

In Vue:

We update reactive state → Vue updates DOM.

Cleaner.  
Safer.  
Predictable.

---

# 🧪 Test It

1. Type "A"
    
2. Click "Apple"
    
3. Input should show "Apple"
    
4. Dropdown should close
    
5. It should NOT immediately reopen
    

Now clear input:

- Dropdown should remain closed
    

---

# 🧠 What We Achieved

✔ Explicit dropdown state  
✔ Clean click selection  
✔ No DOM manipulation  
✔ Controlled behavior

This is already architecturally cleaner than many Vue tutorials.

---

# 🧱 Current Status

✔ Reactive filtering  
✔ Controlled dropdown  
✔ Click selection

Still missing:

❌ Click outside close  
❌ Async behavior  
❌ Debounce  
❌ Race handling  
❌ Cache  
❌ Keyboard navigation  
❌ Accessibility

---

# 🚀 Next Stage

Stage 3 — Click Outside Handling (Vue Way)

This introduces:

- `onMounted`
    
- `onBeforeUnmount`
    
- Proper event cleanup
    

Say:

**“Stage 2 complete”**

and we move deeper.

--------------------------------------------------------------------------

Excellent.  
Now we move into something that separates mid-level Vue developers from senior ones.

---

# 🟢 Stage 3 — Click Outside Handling (Vue Lifecycle Correct Way)

In vanilla JS, we did:

```js
document.addEventListener("click", ...)
```

But in Vue, we must:

- Attach listener in `onMounted`
    
- Remove it in `onBeforeUnmount`
    
- Avoid memory leaks
    
- Avoid breaking reactivity
    

This is lifecycle discipline.

---

# 🎯 Goal

If user clicks outside the autocomplete container:

- Dropdown closes
    
- No memory leak
    
- No accidental close when clicking inside
    

---

# 🧠 Step 1 — Get Container Reference

In template, add a `ref`:

```vue
<div class="autocomplete-container" ref="containerRef">
```

Now Vue will bind this DOM element to a reactive reference.

---

# 🧠 Step 2 — Create containerRef in Script

Inside `<script setup>`:

```js
import { onMounted, onBeforeUnmount } from "vue";

const containerRef = ref(null);
```

This will hold the DOM node after mount.

---

# 🧠 Step 3 — Add Click Outside Logic

Add:

```js
function handleClickOutside(event) {
  if (
    containerRef.value &&
    !containerRef.value.contains(event.target)
  ) {
    isOpen.value = false;
  }
}
```

Explanation:

- `containerRef.value` → actual DOM node
    
- `.contains()` → checks if click was inside component
    
- If not → close dropdown
    

Clean and safe.

---

# 🧠 Step 4 — Attach & Cleanup Properly

Add:

```js
onMounted(() => {
  document.addEventListener("click", handleClickOutside);
});

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
});
```

This ensures:

- Listener attaches when component mounts
    
- Listener removes when component unmounts
    
- No memory leak
    

This is senior-level hygiene.

---

# 🧪 Test It

1. Type "A"
    
2. Dropdown appears
    
3. Click outside → dropdown closes
    
4. Click inside → dropdown stays open
    
5. Click suggestion → works as before
    

---

# 🧠 Why This Is Important

Common mistakes:

- Not cleaning event listener
    
- Forgetting null check on ref
    
- Causing dropdown to close even when clicking inside
    

We avoided all.

---

# 🧱 Current Architecture Status

✔ Reactive filtering  
✔ Controlled dropdown  
✔ Click selection  
✔ Click outside handling  
✔ Proper lifecycle cleanup

This is now structurally clean.

---

# 🚀 Next Stage

Stage 4 — Convert to Async API Simulation

Now we introduce:

- Loading state
    
- Promise-based fetch
    
- Async thinking in Vue
    
- Error handling
    

We begin real-world complexity.

Say:

**“Stage 3 complete”**

and we evolve to async behavior.

--------------------------------------------------------------------------

