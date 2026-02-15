

# ⭐ The Nested File Explorer (VS Code Style)

This is written exactly the way a strong company would give it — with clarity, scope, constraints, edge cases, evaluation criteria, and hidden expectations.

You can use this to:

- Practice properly
    
- Simulate interviews
    
- Or even take mock interviews yourself
    

---

# 🧩 Machine Coding Problem

## 📌 Title

**Build a Nested File Explorer Sidebar (VS Code Style)**

---

## 📝 Problem Statement

Design and implement a dynamic file explorer component similar to the left sidebar of VS Code.

The component must render a hierarchical tree structure of files and folders and support infinite nesting.

The UI must be interactive and support full CRUD operations.

---

# 🎯 Functional Requirements

## 1️⃣ Rendering

- Display a tree of files and folders.
    
- Each node contains:
    
    - `id` (unique identifier)
        
    - `name` (string)
        
    - `isFolder` (boolean)
        
    - `children` (array, only if folder)
        
- Must support **infinite nesting**.
    
- Use indentation to visually represent hierarchy.
    
- Show:
    
    - 📁 for folders
        
    - 📄 for files
        

---

## 2️⃣ Expand / Collapse

- Clicking on a folder toggles its expanded state.
    
- Default state: collapsed.
    
- When collapsed, children must not render.
    
- Clicking a file should not toggle anything.
    
- Child interactions must not accidentally toggle parent folders.
    

---

## 3️⃣ Create (Add File / Folder)

- Each folder should have:
    
    - ➕ Add File
        
    - ➕ Add Folder
        
- When clicked:
    
    - Show an input inside that folder.
        
    - Auto-focus the input.
        
    - Pressing Enter → creates node.
        
    - On Blur → cancel creation.
        
    - Empty names are not allowed.
        
    - Duplicate names in the same folder should be prevented.
        
- Newly created item must:
    
    - Appear immediately
        
    - Persist in state
        
    - Have unique ID
        

---

## 4️⃣ Rename

- Each file/folder should have an Edit icon.
    
- Clicking it:
    
    - Replace name with input field.
        
    - Pre-fill with current name.
        
    - Press Enter → save.
        
    - Press Escape or Blur → cancel.
        
    - Prevent empty rename.
        
    - Prevent duplicate sibling names.
        

---

## 5️⃣ Delete

- Each node should have Delete icon.
    
- Deleting a folder must:
    
    - Remove entire subtree.
        
- UI must update immediately.
    
- No orphaned children should remain.
    

---

# 🧠 Non-Functional Requirements

## 1️⃣ Immutability

- State must not be mutated directly.
    
- All operations must return new tree references.
    

---

## 2️⃣ Performance

- Should handle at least 5,000 nodes without freezing.
    
- Avoid unnecessary re-renders.
    
- Use stable keys.
    

---

## 3️⃣ Clean Architecture

Expected separation:

```
App (holds tree state)
  |
  ├── TreeContext (optional)
  ├── useTreeOperations (custom hook)
  └── FileNode (recursive component)
```

---

## 4️⃣ Edge Cases (Must Handle)

1. Prevent event bubbling issues.
    
2. Adding inside collapsed folder should still work.
    
3. Deleting expanded folder should not crash expansion state.
    
4. Rapid multiple operations should not break tree.
    
5. Must work for deeply nested levels (10+ depth).
    

---

# 📦 Initial Data Example

```js
const initialData = [
  {
    id: "1",
    name: "src",
    isFolder: true,
    children: [
      {
        id: "2",
        name: "components",
        isFolder: true,
        children: []
      },
      {
        id: "3",
        name: "App.js",
        isFolder: false
      }
    ]
  }
];
```

---

# 🎨 UI Expectations

- Clean indentation
    
- Smooth expand/collapse
    
- Proper spacing
    
- Icons aligned
    
- No layout breaking on deep nesting
    

---

# 🚀 Bonus (Senior Level Enhancements)

1. Persist state in localStorage
    
2. Keyboard navigation (Arrow keys)
    
3. Right-click context menu
    
4. Drag and Drop reordering
    
5. Lazy rendering large trees
    
6. Normalize data for O(1) updates
    
7. Use React Context to avoid prop drilling
    
8. Memoize tree nodes
    
9. Use TypeScript types
    

---

# 🧪 Evaluation Criteria (How Interviewer Scores You)

|Criteria|Weight|
|---|---|
|Recursion understanding|20%|
|State management|20%|
|CRUD correctness|20%|
|Immutability|15%|
|Edge case handling|10%|
|Code cleanliness|10%|
|Performance awareness|5%|

---

# ⏱ Expected Time

- Basic version: 45–60 minutes
    
- Full CRUD + clean structure: 75–90 minutes
    
- Senior polished version: 2+ hours
    

---

# 🎤 Follow-Up Questions Interviewer May Ask

1. How would you optimize for very large trees?
    
2. How would you implement drag-and-drop?
    
3. What is time complexity of insert/delete?
    
4. How would you normalize this structure?
    
5. How would you add search?
    
6. How would you persist backend state?
    
7. What happens if two nodes have same ID?
    

---

# 🏆 What a Perfect 10/10 Candidate Does

- Uses recursion correctly
    
- Maintains immutability
    
- Separates traversal logic
    
- Prevents duplicate names
    
- Uses stable keys
    
- Explains time complexity
    
- Mentions performance tradeoffs
    
- Structures code professionally
    
- Handles edge cases proactively
    

---

# 🎯 Why This Is a 10/10 Machine Coding Question

Because it tests:

- Data Structures (Tree)
    
- Algorithms (DFS)
    
- React architecture
    
- State management
    
- UI interactivity
    
- Performance awareness
    
- Clean coding
    

This question alone reveals your true frontend maturity.

---

If you want next, we can:

- 🔥 Simulate a real interview setting
    
- 🧠 Convert this into an LLD explanation
    
- 🧩 Break into implementation stages
    
- 🚀 Do React + TypeScript structure
    
- 🎯 Do performance-optimized version
    

You choose the direction.