
--------------------------------------------------------------------------
Perfect.

We start from **Stage 0**.

This is the stage most candidates skip.  
Senior candidates don’t.

---

# 🧠 Stage 0 — Problem Framing + Architecture Design (Before Coding)

No DOM.  
No recursion.  
No UI.

Just thinking.

If you skip this in an interview, you look reactive instead of structured.

---

# 🎯 What I Would Say to the Interviewer First

> “Before coding, I want to clarify the data structure and how I plan to manage rendering and state in vanilla JS since we won’t have React’s reactivity.”

That signals control.

---

# 🧩 Step 0.1 — Clarify Requirements

Even if obvious, ask:

- Should nesting be infinite? (Yes)
    
- Should state persist on refresh? (Assume no unless asked)
    
- Are CRUD operations required? (Yes)
    
- Is performance a concern? (Probably moderate)
    
- Is drag-and-drop required? (Assume no unless stated)
    

This prevents assumption mistakes.

---

# 🧠 Step 0.2 — Identify Core Problem Type

This is not a UI problem.

It is:

> A recursive tree data structure rendering + mutation problem.

Core components:

1. Tree data model
    
2. Recursive renderer
    
3. State synchronization
    
4. Event handling
    
5. Immutable updates
    

If you understand this, implementation becomes mechanical.

---

# 🧱 Step 0.3 — Decide Data Model

We will use **nested tree structure**.

Example:

```js
const data = [
  {
    id: "1",
    name: "src",
    isFolder: true,
    children: [
      {
        id: "2",
        name: "index.js",
        isFolder: false
      }
    ]
  }
];
```

Why nested?

Because:

- Natural recursion mapping
    
- Simpler for interview
    
- Clear mental model
    

Senior note you can say:

> “If this needed to scale to thousands of nodes with frequent updates, I’d normalize the structure for O(1) lookup.”

---

# 🧠 Step 0.4 — Decide State Strategy (Vanilla Specific)

In React, state triggers re-render automatically.

In Vanilla JS, we must decide:

### Option A — Full Re-render On Every Update

- Clear container
    
- Rebuild tree
    

Pros:

- Simple
    
- Safe
    
- No DOM inconsistency
    

Cons:

- Potential performance hit for very large trees
    

### Option B — Partial DOM Updates

- Update only affected subtree
    

Pros:

- More performant
    
- Closer to production systems
    

Cons:

- More complex
    
- Easier to introduce bugs
    

Senior move:

> “I’ll start with full re-render for correctness. If needed, I can optimize later.”

Always optimize after correctness.

---

# 🧠 Step 0.5 — Where Will UI State Live?

We have two types of state:

### 1️⃣ Data State

The tree structure.

### 2️⃣ UI State

- Expanded folders
    
- Editing node
    
- Creating node
    
- Input values
    

Important rule:

> Do NOT mix UI state into data model.

Bad:

```js
{
  id,
  name,
  isExpanded: true ❌
}
```

Good:

```js
let expandedNodes = new Set();
```

Keep UI state separate.

That shows maturity.

---

# 🧠 Step 0.6 — Rendering Strategy

We will create:

```
renderTree(data, container)
```

Inside it:

- Loop through nodes
    
- Create DOM element
    
- If folder → recursive call
    

That’s the core engine.

---

# 🧠 Step 0.7 — Event Strategy

Two choices:

### Attach event listener to every node

Simple, but many listeners.

### Use event delegation on container

One listener, check target.

Senior answer:

> “For small trees attaching per node is fine. For large trees I’d prefer event delegation.”

We can start simple and mention upgrade path.

---

# 🧠 Step 0.8 — Complexity Awareness

Initial implementation:

- Insert: O(n)
    
- Delete: O(n)
    
- Rename: O(n)
    
- Render: O(n)
    

That is acceptable for interview scale.

Mentioning complexity = senior thinking.

---

# 🎯 What the Interviewer Is Evaluating at Stage 0

- Do you clarify?
    
- Do you choose appropriate data structure?
    
- Do you avoid premature optimization?
    
- Do you separate concerns?
    
- Do you think about scale?
    

Most candidates jump to code immediately.

Senior engineers think first.

---

# 🏆 Stage 0 Summary

We have decided:

- Nested tree data structure
    
- Separate UI state
    
- Full re-render strategy initially
    
- Recursive rendering function
    
- CRUD via DFS
    
- No premature optimization
    

We are now ready to touch the DOM.

---

If this makes sense, say:

**“Stage 1.”**

And we will implement the minimal static recursive renderer in pure vanilla JS.

--------------------------------------------------------------------------