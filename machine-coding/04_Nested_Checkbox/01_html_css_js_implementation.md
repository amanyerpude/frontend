
--------------------------------------------------------------------------

# 🟢 Stage 0 — Static Recursive Tree Rendering (No Selection Logic)

---

## 🎯 Goal of This Stage

Only this:

- Render nested tree from JSON
    
- Use recursion
    
- Proper indentation
    
- Clean DOM structure
    
- No checkbox propagation logic yet
    

If this stage is clean, everything else becomes easier.

---

# 🧠 What You Say To Interviewer

> “I’ll start by rendering the tree structure recursively. I won’t implement selection logic yet. I want to first ensure the structure and rendering are correct.”

This signals:

- Structured thinking
    
- Controlled scope
    
- No rushing
    

---

# 🧠 What Interviewer Is Evaluating

- Do you understand recursion?
    
- Can you structure DOM cleanly?
    
- Do you separate data from rendering?
    
- Do you avoid premature complexity?
    

---

# 📦 Step 1 — Define Sample Data

We start simple.

```js
const treeData = [
  {
    id: 1,
    label: "Fruits",
    children: [
      { id: 11, label: "Apple" },
      { id: 12, label: "Banana" }
    ]
  },
  {
    id: 2,
    label: "Vegetables",
    children: [
      { id: 21, label: "Carrot" },
      { id: 22, label: "Broccoli" }
    ]
  }
];
```

Notice:

- Unique IDs
    
- Optional `children`
    
- No `checked` yet
    

We keep state minimal for now.

---

# 🏗️ Step 2 — Basic HTML Structure

```html
<!DOCTYPE html>
<html>
<head>
  <title>Nested Checkbox Tree</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div id="tree-root"></div>
  <script src="script.js"></script>
</body>
</html>
```

Clean container. Nothing fancy.

---

# 🎨 Step 3 — Minimal CSS (Indentation Only)

```css
.tree-node {
  margin-left: 20px;
  font-family: Arial, sans-serif;
}

.tree-label {
  cursor: pointer;
}
```

Why margin-left?

Because recursion visually represents hierarchy.

We don’t hardcode depth.  
We let nesting create indentation naturally.

---

# ⚙️ Step 4 — Recursive Render Function (Core Part)

Now the important part.

```js
function renderTree(nodes, container) {
  nodes.forEach(node => {
    const wrapper = document.createElement("div");
    wrapper.classList.add("tree-node");

    const checkbox = document.createElement("input");
    checkbox.type = "checkbox";
    checkbox.dataset.id = node.id;

    const label = document.createElement("span");
    label.textContent = node.label;
    label.classList.add("tree-label");

    wrapper.appendChild(checkbox);
    wrapper.appendChild(label);

    container.appendChild(wrapper);

    // Recursively render children if exist
    if (node.children && node.children.length > 0) {
      renderTree(node.children, wrapper);
    }
  });
}
```

---

# 🚀 Step 5 — Initialize Rendering

```js
const root = document.getElementById("tree-root");
renderTree(treeData, root);
```

That’s it.

No selection logic.  
No propagation.  
Only structure.

---

# 🧠 Why This Is Correct Stage 0

Because:

- You established recursive pattern.
    
- You created predictable DOM structure.
    
- Each node has dataset id.
    
- Children render inside parent wrapper.
    

This structure makes traversal easier later.

---

# 🧠 Internal Thought Process (Important)

You are thinking:

- Later I can use `dataset.id` for lookup
    
- Parent wrapper contains children — useful for propagation
    
- Structure is depth-agnostic
    
- No state logic yet — reduce cognitive load
    

This is clean incremental thinking.

---

# ❌ Common Mistakes At This Stage

- Mixing selection logic immediately
    
- Adding indeterminate prematurely
    
- Hardcoding indentation by depth manually
    
- Not checking if `children` exists
    
- Rendering children outside parent wrapper
    

---

# 🧪 Quick Self-Test

If I add:

```js
{
  id: 111,
  label: "Granny Smith",
  children: []
}
```

Inside Apple — will it render?

Yes.

Because recursion handles unknown depth.

That’s what interviewer wants to see.

---

# 🟢 Stage 0 Complete

We now have:

✔ Recursive tree rendering  
✔ Clean DOM structure  
✔ Ready for event handling

---

Next stage:

# 🟢 Stage 1 — Basic Checkbox Toggle (Independent State)

We will:

- Track state in JS
    
- Sync checkbox with state
    
- No propagation yet
    

Say:

> next

And we proceed carefully.

--------------------------------------------------------------------------
# 🟢 Stage 1 — Basic Checkbox Toggle (Independent State)

⚠️ Still **no parent-child propagation**.  
Each checkbox behaves independently.

---

# 🎯 Goal of This Stage

- Introduce state in JS
    
- Sync checkbox UI with state
    
- Handle toggle events
    
- Keep logic simple
    

We are building **state discipline** before complexity.

---

# 🧠 What You Say To Interviewer

> “Now that rendering works, I’ll introduce state management. I’ll keep selection independent for now and later extend it to support propagation.”

This signals:

- Incremental approach
    
- You are intentionally scoping
    

---

# 🧠 What Interviewer Is Evaluating

- Can you separate data from DOM?
    
- Do you understand source of truth?
    
- Can you wire event listeners cleanly?
    
- Do you avoid using DOM as state?
    

---

# ⚠️ Important Design Decision Now

We must choose:

### ❌ Option A — Use DOM as source of truth

(check `checkbox.checked` directly)

### ✅ Option B — Maintain JS state model

For interview prep:

Always choose **JS as source of truth**.

Why?

Because propagation logic becomes predictable.

---

# 🧩 Step 1 — Normalize Data With `checked`

We update initial data:

```js
function initializeTree(nodes) {
  return nodes.map(node => ({
    ...node,
    checked: false,
    children: node.children ? initializeTree(node.children) : []
  }));
}

const state = initializeTree(treeData);
```

Now every node has:

```js
{
  id,
  label,
  checked,
  children
}
```

We created a proper state tree.

---

# 🧠 Why This Is Smart

Later:

- Propagation updates state tree
    
- UI re-renders from state
    
- No confusion between DOM and data
    

---

# 🧩 Step 2 — Modify Render Function To Use State

Update render:

```js
function renderTree(nodes, container) {
  container.innerHTML = ""; // Clear before render

  nodes.forEach(node => {
    const wrapper = document.createElement("div");
    wrapper.classList.add("tree-node");

    const checkbox = document.createElement("input");
    checkbox.type = "checkbox";
    checkbox.checked = node.checked;
    checkbox.dataset.id = node.id;

    checkbox.addEventListener("change", handleToggle);

    const label = document.createElement("span");
    label.textContent = node.label;
    label.classList.add("tree-label");

    wrapper.appendChild(checkbox);
    wrapper.appendChild(label);

    container.appendChild(wrapper);

    if (node.children.length > 0) {
      renderTree(node.children, wrapper);
    }
  });
}
```

Notice:

- We use `node.checked`
    
- We attach event listener
    
- We clear container before render
    

This makes it re-renderable.

---

# 🧩 Step 3 — Implement Toggle Handler (Simple Version)

```js
function handleToggle(event) {
  const id = Number(event.target.dataset.id);

  toggleNode(state, id);

  renderTree(state, root);
}
```

---

# 🧩 Step 4 — Toggle Function (Recursive Search)

```js
function toggleNode(nodes, targetId) {
  for (let node of nodes) {
    if (node.id === targetId) {
      node.checked = !node.checked;
      return true;
    }

    if (node.children.length > 0) {
      const found = toggleNode(node.children, targetId);
      if (found) return true;
    }
  }

  return false;
}
```

---

# 🧠 What Just Happened

Flow:

1. User clicks checkbox
    
2. We find node in state tree
    
3. Flip `checked`
    
4. Re-render entire tree
    

This is simple and correct.

---

# ⚠️ Yes, We Re-render Entire Tree

That’s fine for now.

Later we optimize.

In interviews:

Correctness > premature optimization.

---

# 🧠 Internal Thinking

You are preparing for:

- Stage 2 → Top-down propagation
    
- Stage 3 → Bottom-up logic
    

Because state is centralized, this will be easier.

---

# ❌ Common Mistakes Here

- Mutating DOM only
    
- Forgetting to re-render
    
- Not clearing container
    
- Not normalizing children to empty array
    
- Attaching multiple event listeners accidentally
    

---

# 🟢 Stage 1 Complete

We now have:

✔ Recursive render  
✔ Centralized state  
✔ Toggle handler  
✔ Full re-render loop

---

Now complexity begins.

Next stage:

# 🟡 Stage 2 — Top-Down Propagation (Parent → Children)

We will make:

Checking parent selects all descendants.

This is where DFS thinking begins.

Say:

> next

And we level up.