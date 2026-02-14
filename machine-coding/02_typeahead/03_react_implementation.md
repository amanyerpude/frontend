
--------------------------------------------------------------------------
Perfect.  
Now we begin **Stage 0 — React + TypeScript (FAANG-Level Requirement Framing)**.

No code yet.

Just thinking like a Senior Engineer.

---

# 🔵 Stage 0 — Requirement Framing (React Context)

### 🎤 Interviewer says:

> “Build an autocomplete component in React.”

That’s intentionally vague.

At 6 YOE, you do NOT open VS Code.

You clarify.

---

# 🧠 1️⃣ Functional Clarifications

## Data Source

You should ask:

- Is data local or remote?
    
- Do we control API?
    
- What is response shape?
    
- Is it prefix match or fuzzy search?
    

For our build:

- Simulated async API
    
- Prefix match
    
- Case-insensitive
    
- Limit results to 5
    

---

## Selection Behavior

Ask:

- Should selecting populate input?
    
- Should dropdown close?
    
- Should it emit callback to parent?
    

We define:

- Yes, populate input
    
- Yes, close dropdown
    
- Later: add `onSelect` callback (reusability stage)
    

---

## Empty States

We explicitly define:

|Scenario|Behavior|
|---|---|
|Empty input|Hide dropdown|
|Loading|Show “Loading…”|
|No results|Show “No results found”|
|Error|Show “Something went wrong”|

Senior engineers separate these states clearly.

---

# 🧠 2️⃣ Non-Functional Requirements

Now we think deeper.

## Performance

We anticipate:

- Debounce input
    
- Avoid API spam
    
- Handle race conditions
    
- Add caching
    

Even before writing code.

---

## Accessibility

We plan to support:

- ARIA combobox
    
- Keyboard navigation
    
- Screen reader compatibility
    

---

## Scalability

Ask:

- What if 10k results?
    
- What if API takes 3 seconds?
    
- What about mobile?
    
- What about SSR?
    

We will discuss after implementation.

---

# 🧠 3️⃣ React-Specific Architectural Decisions

React requires explicit thinking.

---

## State Strategy

We will use:

- `useState` → reactive state
    
- `useEffect` → side effects (async, debounce)
    
- `useRef` → DOM reference + cache storage
    
- Derived values computed during render
    

No Redux.  
No external debounce library.  
No UI libraries.

Pure React.

---

## Derived State Principle

In React:

> Don’t store what you can derive.

Example:

- We won’t store `filteredResults` in state initially.
    
- We compute from `query`.
    

Avoid redundant state.

---

## Avoid Common React Mistakes

We will avoid:

- Stale closure bugs
    
- Incorrect dependency arrays
    
- Memory leaks
    
- Unnecessary re-renders
    
- Storing timer in state
    

This is where senior React knowledge matters.

---

# 🧠 4️⃣ Incremental Plan (Same Discipline)

We will implement in strict order:

### Stage 1

Basic UI + Local Filtering (synchronous)

### Stage 2

Click selection + controlled dropdown

### Stage 3

Click outside handling (useRef + useEffect cleanup)

### Stage 4

Async fetch simulation

### Stage 5

Debounce using useEffect

### Stage 6

Race handling (request ID)

### Stage 7

Caching (Map + useRef)

### Stage 8

Keyboard navigation

### Stage 9

Highlight matching substring

### Stage 10

Accessibility (ARIA)

### Stage 11

Extract into reusable component + hook

---

# 🧠 5️⃣ Mental Model Shift (Vue → React)

In Vue:

- Reactive system auto-tracks dependencies
    
- computed() + watch()
    

In React:

- Everything re-renders on state change
    
- Derived values computed each render
    
- useEffect handles side effects
    
- Dependency arrays must be precise
    

React is more explicit.  
More manual.  
More control.  
More room for bugs.

That’s why senior discipline matters.

---

# 📂 Assumed File: `App.tsx`

We will start inside `App.tsx`.

Later refactor.

---

# 🚦 Before Stage 1

Confirm:

You want:

- Extremely detailed code
    
- TypeScript types everywhere
    
- Comments explaining React reasoning
    
- Explanation outside code as well
    

If yes, say:

**“Proceed to Stage 1 (React detailed mode)”**

And we begin building properly.

--------------------------------------------------------------------------

Perfect.  
Now we begin:

# 🟢 Stage 1 — Basic UI + Local Filtering (React + TypeScript)

We move slowly. Clean foundation first.

No async.  
No debounce.  
No optimization.  
No keyboard.

Just correctness + proper React thinking.

---

# 🎯 Goal

We will build:

- Controlled input
    
- Local dataset
    
- Derived filtered results
    
- Limit to 5 suggestions
    
- Conditional rendering
    
- Proper TypeScript typing
    

---

# 🧠 React Mental Model Reminder

In React:

- State changes → component re-renders
    
- Derived values should NOT be stored in state
    
- They should be computed during render
    

We follow:

> Store minimal state. Derive the rest.

---

# 📄 `App.tsx`

Read comments carefully.

---

```tsx
import React, { useState } from "react";

/*
  Define type for suggestion.
  Even though we are using strings now,
  we type it explicitly for scalability.
*/
type Suggestion = string;

function App() {
  /*
    query is controlled input state.
    React state must be minimal.
  */
  const [query, setQuery] = useState<string>("");

  /*
    Static dataset for Stage 1.
    Later replaced with async API.
  */
  const data: Suggestion[] = [
    "Apple",
    "Banana",
    "Mango",
    "Orange",
    "Pineapple",
    "Grapes",
    "Watermelon",
    "Papaya",
    "Kiwi",
    "Strawberry",
  ];

  /*
    Derived results.
    We DO NOT store this in state.
    It is computed during render.

    This avoids:
    - Extra re-renders
    - State duplication
    - Inconsistency bugs
  */
  const filteredResults: Suggestion[] = (() => {
    const trimmed = query.trim().toLowerCase();

    if (!trimmed) return [];

    return data
      .filter((item) =>
        item.toLowerCase().startsWith(trimmed)
      )
      .slice(0, 5);
  })();

  return (
    <div
      style={{
        width: "300px",
        margin: "100px auto",
        position: "relative",
      }}
    >
      {/* Controlled input */}
      <input
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Search..."
        autoComplete="off"
        style={{
          width: "100%",
          padding: "10px",
          fontSize: "16px",
        }}
      />

      {/* Show suggestions only if query exists */}
      {query && filteredResults.length > 0 && (
        <ul
          style={{
            listStyle: "none",
            margin: 0,
            padding: 0,
            border: "1px solid #ccc",
            borderTop: "none",
            background: "white",
          }}
        >
          {filteredResults.map((item) => (
            <li
              key={item}
              style={{
                padding: "10px",
              }}
            >
              {item}
            </li>
          ))}
        </ul>
      )}

      {/* No Results State */}
      {query && filteredResults.length === 0 && (
        <ul
          style={{
            listStyle: "none",
            margin: 0,
            padding: 0,
            border: "1px solid #ccc",
            borderTop: "none",
            background: "white",
          }}
        >
          <li style={{ padding: "10px", color: "gray" }}>
            No results found
          </li>
        </ul>
      )}
    </div>
  );
}

export default App;
```

---

# 🧠 Deep Explanation (Senior-Level)

### 1️⃣ Why Not Store `filteredResults` in useState?

Because:

- It depends entirely on `query`
    
- Storing it creates duplicated state
    
- Leads to synchronization bugs
    

Senior rule:

> Never store what you can derive.

---

### 2️⃣ Why Compute Inside Render?

Because:

- Filtering small dataset is cheap
    
- Keeps logic simple
    
- Avoids unnecessary useEffect
    

Later when async comes, we change this pattern.

---

### 3️⃣ Why Controlled Input?

React expects:

```tsx
value + onChange
```

This ensures:

- Single source of truth
    
- Predictable state updates
    

---

### 4️⃣ Why Limit to 5?

UX discipline:

- Prevent overwhelming user
    
- Prevent layout overflow
    
- Good performance habit
    

---

# 🧪 Test It

Run Vite.

Type:

- A
    
- B
    
- Z
    
- Clear input
    

Verify:

- Filtering works
    
- Max 5 items
    
- No results state works
    
- Dropdown hides when empty
    

---

# 🧱 Current Architecture Status

✔ Controlled input  
✔ Derived filtering  
✔ Clean minimal state  
✔ TypeScript safe

Still missing:

❌ Click selection  
❌ Controlled dropdown state  
❌ Async  
❌ Debounce  
❌ Race handling  
❌ Cache  
❌ Keyboard navigation  
❌ Accessibility

---

# 🚀 Next Stage

Stage 2 — Controlled Dropdown + Click Selection

This introduces:

- Explicit `isOpen` state
    
- Better visibility control
    
- Selection logic
    

Say:

**“Stage 1 complete”**

and we continue layering properly.

--------------------------------------------------------------------------

Excellent.  
Now we move into **Stage 2 — Controlled Dropdown + Click Selection (React + TS)**.

This is where we move from “basic filtering demo” to “structured component.”

---

# 🟢 Stage 2 — Explicit Dropdown State + Selection Logic

## 🎯 Why We Need This

Right now dropdown visibility depends on:

```tsx
query && filteredResults.length > 0
```

This is fragile.

If user selects an item:

- `query` still has value
    
- `filteredResults` still matches
    
- Dropdown immediately reappears
    

We need:

> Explicit UI visibility control

Senior engineers separate:

- Data state (`query`)
    
- UI state (`isOpen`)
    

---

# 🧠 Step 1 — Add Dropdown State

Update state section:

```tsx
const [isOpen, setIsOpen] = useState<boolean>(false);
```

---

# 🧠 Step 2 — Control Dropdown Opening

Modify input `onChange`:

```tsx
onChange={(e) => {
  const value = e.target.value;
  setQuery(value);
  setIsOpen(!!value.trim());
}}
```

Explanation:

- If input not empty → open dropdown
    
- If empty → close dropdown
    

Explicit control.

---

# 🧠 Step 3 — Add Selection Handler

Add this function inside component:

```tsx
const handleSelect = (item: Suggestion) => {
  setQuery(item);   // Populate input
  setIsOpen(false); // Close dropdown
};
```

---

# 🧠 Step 4 — Update Rendering Logic

Replace previous conditional blocks with:

```tsx
{isOpen && (
  <ul
    style={{
      listStyle: "none",
      margin: 0,
      padding: 0,
      border: "1px solid #ccc",
      borderTop: "none",
      background: "white",
    }}
  >
    {filteredResults.length > 0 ? (
      filteredResults.map((item) => (
        <li
          key={item}
          onClick={() => handleSelect(item)}
          style={{
            padding: "10px",
            cursor: "pointer",
          }}
        >
          {item}
        </li>
      ))
    ) : (
      <li style={{ padding: "10px", color: "gray" }}>
        No results found
      </li>
    )}
  </ul>
)}
```

---

# 🧠 What Changed Architecturally

Before:  
Dropdown visibility = derived from filtering.

Now:  
Dropdown visibility = controlled state.

This gives us:

✔ Better predictability  
✔ Better future async handling  
✔ Cleaner UX

---

# 🧪 Test It

1. Type “A”
    
2. Click “Apple”
    
3. Dropdown should close
    
4. It should NOT reopen immediately
    

Clear input → dropdown should remain closed.

---

# 🧠 Why This Matters for Senior Interviews

Interviewers check:

- Do you separate UI state from data state?
    
- Do you avoid accidental derived UI bugs?
    
- Do you think about UX edge cases?
    

This is where mid-level vs senior separation begins.

---

# 🧱 Current System Status

✔ Controlled input  
✔ Derived filtering  
✔ Explicit dropdown state  
✔ Click selection

Still missing:

❌ Click outside handling  
❌ Async  
❌ Debounce  
❌ Race handling  
❌ Cache  
❌ Keyboard navigation  
❌ Accessibility

---

# 🚀 Next Stage

Stage 3 — Click Outside Handling (useRef + useEffect + cleanup)

This is where React lifecycle discipline matters.

Say:

**“Stage 2 complete”**

and we continue.

--------------------------------------------------------------------------

