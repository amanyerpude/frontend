
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