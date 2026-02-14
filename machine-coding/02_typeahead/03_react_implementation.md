
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

Excellent.  
Now we move into something that reveals real React maturity.

---

# 🟢 Stage 3 — Click Outside Handling (React Way)

This is where:

- `useRef`
    
- `useEffect`
    
- Cleanup discipline
    
- Event propagation awareness
    

all come together.

---

# 🎯 Goal

If user clicks outside the autocomplete component:

- Dropdown closes
    
- No memory leak
    
- No accidental closing when clicking inside
    

---

# 🧠 Step 1 — Create Container Ref

At top of component:

```tsx
import React, { useState, useRef, useEffect } from "react";
```

Then inside component:

```tsx
const containerRef = useRef<HTMLDivElement | null>(null);
```

Explanation:

- `useRef` stores a mutable reference
    
- Does NOT cause re-render
    
- Used for DOM access
    
- TypeScript typed for safety
    

---

# 🧠 Step 2 — Attach Ref to Container

Update outer div:

```tsx
<div
  ref={containerRef}
  style={{
    width: "300px",
    margin: "100px auto",
    position: "relative",
  }}
>
```

Now we can detect outside clicks.

---

# 🧠 Step 3 — Add Click Outside Effect

Add this inside component:

```tsx
useEffect(() => {
  const handleClickOutside = (event: MouseEvent) => {
    if (
      containerRef.current &&
      !containerRef.current.contains(event.target as Node)
    ) {
      setIsOpen(false);
    }
  };

  document.addEventListener("click", handleClickOutside);

  return () => {
    document.removeEventListener("click", handleClickOutside);
  };
}, []);
```

---

# 🧠 Why This Is Correct

### 1️⃣ Why empty dependency array `[]`?

Because:

- We only want to attach once on mount
    
- And remove on unmount
    

If we included `isOpen`, listener would reattach every render.

Senior discipline.

---

### 2️⃣ Why Type Assertion `as Node`?

Because:

`event.target` is `EventTarget | null`

TypeScript requires proper casting.

---

### 3️⃣ Why Cleanup?

Without cleanup:

- Memory leak
    
- Duplicate listeners
    
- Hard-to-debug behavior
    

Senior React = always cleanup side effects.

---

# 🧪 Test It

1. Type “A”
    
2. Dropdown opens
    
3. Click outside → closes
    
4. Click inside → stays open
    
5. Click suggestion → works
    

---

# 🧠 Why This Is More Subtle Than It Looks

Common mistakes:

- Forgetting cleanup
    
- Missing null check
    
- Attaching inside render
    
- Using wrong dependency array
    

We avoided all.

---

# 🧱 Current Architecture Status

✔ Controlled input  
✔ Derived filtering  
✔ Explicit dropdown state  
✔ Click selection  
✔ Click outside handling  
✔ Proper effect cleanup

Now we’re structurally clean.

---

Still missing:

❌ Async  
❌ Loading state  
❌ Debounce  
❌ Race protection  
❌ Cache  
❌ Keyboard navigation  
❌ Highlight  
❌ Accessibility

---

# 🚀 Next Stage

Stage 4 — Convert to Async API Simulation

This is where React side-effects start becoming interesting.

Say:

**“Stage 3 complete”**

and we move into async complexity.

--------------------------------------------------------------------------

Excellent.  
Now we enter:

# 🔵 Stage 4 — Async API Simulation (React + TypeScript)

Now complexity increases.

We are introducing:

- Loading state
    
- Error state
    
- Async fetch simulation
    
- Side-effect driven state updates
    

Still no debounce.  
Still no race protection.  
Correctness first.

---

# 🎯 Architectural Shift

Until now:

```
filteredResults = derived from query
```

Now:

Results come from async API.

So:

- We cannot derive results synchronously
    
- We must store `results` in state
    
- We must trigger fetch in `useEffect`
    

This is a major React shift.

---

# 🧠 Step 1 — Add New State

Inside component:

```tsx
const [results, setResults] = useState<Suggestion[]>([]);
const [isLoading, setIsLoading] = useState<boolean>(false);
const [error, setError] = useState<string | null>(null);
```

Explanation:

- `results` → API data
    
- `isLoading` → controls loading UI
    
- `error` → error message
    

We are now in side-effect territory.

---

# 🧠 Step 2 — Simulated Async API Function

Add inside component (or outside if preferred):

```tsx
const fetchSuggestions = (query: string): Promise<Suggestion[]> => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      // Simulate occasional error
      if (Math.random() < 0.05) {
        reject("Network error");
        return;
      }

      const filtered = data
        .filter((item) =>
          item.toLowerCase().startsWith(query.toLowerCase())
        )
        .slice(0, 5);

      resolve(filtered);
    }, Math.random() * 800 + 200);
  });
};
```

Random delay simulates real-world unpredictability.

---

# 🧠 Step 3 — Replace Derived Filtering With Effect

Remove old `filteredResults`.

Add:

```tsx
useEffect(() => {
  const trimmed = query.trim();

  if (!trimmed) {
    setResults([]);
    setIsOpen(false);
    return;
  }

  setIsLoading(true);
  setError(null);

  fetchSuggestions(trimmed)
    .then((response) => {
      setResults(response);
    })
    .catch((err) => {
      setError(err);
      setResults([]);
    })
    .finally(() => {
      setIsLoading(false);
    });

}, [query]);
```

---

# 🧠 Important React Concept

`useEffect` runs whenever `query` changes.

This replaces Vue’s `watch`.

React requires explicit dependency arrays.

---

# 🧠 Step 4 — Update Render Logic

Replace list rendering with:

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
    {isLoading ? (
      <li style={{ padding: "10px" }}>Loading...</li>
    ) : error ? (
      <li style={{ padding: "10px", color: "red" }}>
        Something went wrong
      </li>
    ) : results.length === 0 ? (
      <li style={{ padding: "10px", color: "gray" }}>
        No results found
      </li>
    ) : (
      results.map((item) => (
        <li
          key={item}
          onClick={() => handleSelect(item)}
          style={{ padding: "10px", cursor: "pointer" }}
        >
          {item}
        </li>
      ))
    )}
  </ul>
)}
```

---

# 🧪 Test Carefully

Type quickly:

- A
    
- Ap
    
- App
    

You may notice:

Sometimes older results override newer.

That is:

🔥 Race Condition

We intentionally introduced it.

---

# 🧠 What We Achieved

✔ Async behavior  
✔ Loading state  
✔ Error handling  
✔ Realistic delay  
✔ Proper useEffect usage

But still:

❌ No debounce  
❌ No race protection  
❌ No cache

---

# 🚀 Next Stage

Stage 5 — Debounce in React (useEffect + timer)

This is where many React candidates make mistakes.

Say:

**“Stage 4 complete”**

and we optimize properly.

--------------------------------------------------------------------------

Excellent.  
Now we move into **Stage 5 — Debouncing in React (Correctly, Without Bugs)**.

This is where React discipline really matters.

---

# 🟣 Stage 5 — Debounce API Calls

## 🎯 Problem

Right now:

Every keystroke → `query` changes → `useEffect` runs → API call fires.

If user types:

```
A
Ap
App
Appl
Apple
```

We fire 5 API calls.

Not acceptable.

---

# 🧠 React Debounce Strategy

We will:

- Add a separate debounced value
    
- Use `setTimeout`
    
- Clear previous timer
    
- Trigger API only when debounce completes
    

Important:

We will NOT debounce inside the fetch effect.  
We will debounce the query itself.

This keeps architecture clean.

---

# 🧠 Step 1 — Add Debounced Query State

Add:

```tsx
const [debouncedQuery, setDebouncedQuery] = useState<string>("");
```

Now we separate:

- `query` → immediate input value
    
- `debouncedQuery` → stable value after delay
    

Senior pattern.

---

# 🧠 Step 2 — Add Debounce Effect

Add this above the fetch effect:

```tsx
useEffect(() => {
  const handler = setTimeout(() => {
    setDebouncedQuery(query);
  }, 400); // 400ms delay

  return () => {
    clearTimeout(handler);
  };
}, [query]);
```

---

# 🧠 Why This Pattern Is Correct

Instead of:

Debouncing inside fetch effect,

We:

- Derive a debounced value
    
- Use it as trigger for API effect
    

This keeps responsibilities separated.

---

# 🧠 Step 3 — Update Fetch Effect

Now change dependency from `query` to `debouncedQuery`:

```tsx
useEffect(() => {
  const trimmed = debouncedQuery.trim();

  if (!trimmed) {
    setResults([]);
    setIsOpen(false);
    return;
  }

  setIsLoading(true);
  setError(null);

  fetchSuggestions(trimmed)
    .then((response) => {
      setResults(response);
    })
    .catch((err) => {
      setError(err);
      setResults([]);
    })
    .finally(() => {
      setIsLoading(false);
    });

}, [debouncedQuery]);
```

Now API fires only after debounce.

---

# 🧪 Test It

Add console log inside `fetchSuggestions`.

Type quickly.

You should see:

Only one API call after you stop typing.

Debounce works.

---

# 🧠 Why This Is Senior-Level React

Common mistakes:

❌ Debouncing inside onChange  
❌ Storing timer in state  
❌ Missing cleanup  
❌ Incorrect dependency arrays  
❌ Causing stale closure bugs

We avoided all.

---

# 🚨 Important: Race Condition Still Exists

Even with debounce:

If:

- API call #1 starts
    
- User types again
    
- API call #2 starts
    
- #1 returns after #2
    

Older response can overwrite newer.

We fix that next.

---

# 🧱 Current Architecture Status

✔ Async  
✔ Loading  
✔ Error  
✔ Debounce  
✔ Click outside  
✔ Click selection

Still missing:

❌ Race handling  
❌ Cache  
❌ Keyboard navigation  
❌ Highlight  
❌ Accessibility

---

# 🚀 Next Stage

Stage 6 — Race Condition Handling (React-Safe Version)

This is where most candidates break.

Say:

**“Stage 5 complete”**

and we harden the system.

--------------------------------------------------------------------------

Excellent.  
Now we enter **Stage 6 — Race Condition Handling (React + TypeScript, Production-Safe)**.

This is where senior React thinking becomes very visible.

---

# 🔴 Stage 6 — Prevent Stale API Responses

## 🎯 The Problem (Revisited)

Even with debounce:

1. `debouncedQuery = "A"` → API call #1
    
2. User types → `debouncedQuery = "Ap"` → API call #2
    
3. Call #2 returns first → correct results
    
4. Call #1 returns later → overwrites results ❌
    

This creates inconsistent UI.

We must guarantee:

> Only the latest request is allowed to update state.

---

# 🧠 Design Strategy

We will use:

> Request ID tracking via `useRef`

Why `useRef`?

- It persists across renders
    
- Updating it does NOT cause re-render
    
- Perfect for mutable concurrency control
    

---

# 🧠 Step 1 — Add Request ID Ref

Add at top of component:

```tsx
const requestIdRef = useRef<number>(0);
```

Explanation:

- Stores latest request ID
    
- Mutable
    
- Safe across renders
    

---

# 🧠 Step 2 — Modify Fetch Effect

Update fetch effect like this:

```tsx
useEffect(() => {
  const trimmed = debouncedQuery.trim();

  if (!trimmed) {
    setResults([]);
    setIsOpen(false);
    return;
  }

  const currentRequestId = ++requestIdRef.current;

  setIsLoading(true);
  setError(null);

  fetchSuggestions(trimmed)
    .then((response) => {
      // Ignore stale responses
      if (currentRequestId !== requestIdRef.current) return;

      setResults(response);
    })
    .catch((err) => {
      if (currentRequestId !== requestIdRef.current) return;

      setError(err);
      setResults([]);
    })
    .finally(() => {
      if (currentRequestId === requestIdRef.current) {
        setIsLoading(false);
      }
    });

}, [debouncedQuery]);
```

---

# 🧠 What Just Happened

Each time effect runs:

```
requestIdRef.current++
```

Each request captures its own ID.

When response returns:

If ID ≠ latest → ignore it.

Guarantee:

✔ No stale UI  
✔ No incorrect overwrites  
✔ Predictable state

---

# 🧪 Test Aggressively

Type:

- A
    
- Quickly Ap
    
- Quickly App
    

Even with random delay:

Results should always match latest input.

No flickering.  
No wrong results.

---

# 🧠 Why This Is Senior-Level React

Because you now understand:

- Async concurrency in React
    
- Non-deterministic timing
    
- State consistency guarantees
    
- Mutable refs for concurrency control
    

Most developers stop at debounce.  
You didn’t.

---

# 🧱 Current Architecture Status

✔ Async  
✔ Debounce  
✔ Race-safe  
✔ Loading  
✔ Error  
✔ Click selection  
✔ Click outside

Still missing:

❌ Cache  
❌ Keyboard navigation  
❌ Highlight  
❌ Accessibility

---

# 🚀 Next Stage

Stage 7 — Caching (Map + useRef)

We now prevent redundant API calls.

Say:

**“Stage 6 complete”**

and we add intelligent caching.

--------------------------------------------------------------------------

Excellent.  
Now we move into:

# 🟡 Stage 7 — Caching (React + TypeScript, Senior Pattern)

At this point your async logic is already production-safe.

Now we optimize intelligently.

---

# 🎯 Problem

Even with:

- Debounce
    
- Race protection
    

If user types:

```
Apple
(clear)
Apple
```

We still call API twice.

Wasteful.

We fix that.

---

# 🧠 Design Strategy

We will:

- Use a `Map` to cache results
    
- Store cache in `useRef`
    
- Check cache before fetching
    
- Skip API call if data exists
    
- Avoid loading flicker
    

Why `useRef`?

Because:

- Cache is mutable
    
- It should persist across renders
    
- Updating cache should NOT cause re-render
    

Perfect use case.

---

# 🧠 Step 1 — Add Cache Ref

Add at top of component:

```tsx
const cacheRef = useRef<Map<string, Suggestion[]>>(new Map());
```

Explanation:

- Key = query string
    
- Value = suggestion array
    
- Not reactive
    
- Internal optimization
    

---

# 🧠 Step 2 — Modify Fetch Effect

Update effect:

```tsx
useEffect(() => {
  const trimmed = debouncedQuery.trim();

  if (!trimmed) {
    setResults([]);
    setIsOpen(false);
    return;
  }

  // 🔥 Check Cache First
  if (cacheRef.current.has(trimmed)) {
    setResults(cacheRef.current.get(trimmed)!);
    setIsOpen(true);
    return;
  }

  const currentRequestId = ++requestIdRef.current;

  setIsLoading(true);
  setError(null);

  fetchSuggestions(trimmed)
    .then((response) => {
      if (currentRequestId !== requestIdRef.current) return;

      // 🔥 Store in Cache
      cacheRef.current.set(trimmed, response);

      setResults(response);
    })
    .catch((err) => {
      if (currentRequestId !== requestIdRef.current) return;

      setError(err);
      setResults([]);
    })
    .finally(() => {
      if (currentRequestId === requestIdRef.current) {
        setIsLoading(false);
      }
    });

}, [debouncedQuery]);
```

---

# 🧠 What Just Improved

Now flow is:

1. User types
    
2. Debounce fires
    
3. Check cache
    
    - If exists → instant render
        
    - If not → fetch → store → render
        

No duplicate network calls.

---

# 🧪 Test It

Add inside `fetchSuggestions`:

```tsx
console.log("API CALL:", query);
```

Then:

1. Type “Apple”
    
2. Clear
    
3. Type “Apple” again
    

You should see:

Only one API call logged.

Second time = instant render.

---

# 🧠 Senior Interview Insight

If interviewer asks:

> What about cache growth?

You say:

- For small datasets → acceptable
    
- For large scale → implement:
    
    - LRU eviction
        
    - TTL expiration
        
    - Max cache size
        

That shows production thinking.

---

# 🧱 Current Architecture Status

✔ Async  
✔ Debounce  
✔ Race safe  
✔ Cache  
✔ Loading  
✔ Error  
✔ Click selection  
✔ Click outside

This is now serious production-level async logic.

---

Still missing:

❌ Keyboard navigation  
❌ Highlight  
❌ Accessibility  
❌ Reusable hook extraction

---

# 🚀 Next Stage

Stage 8 — Keyboard Navigation (React Controlled State)

This is where coordination gets interesting.

Say:

**“Stage 7 complete”**

and we move into interactive state mastery.