
---

# ⭐ Frontend Machine Coding Question

## Build a Production-Ready Reusable Rating Component

---

# Phase 1 — Core State Model

## 🎯 Requirement

Build a reusable Rating component with:

- Configurable item count
    
- Hover interaction
    
- Click to select
    
- Reset on mouse leave
    
- Parent callback notification
    

---

## 🧠 State Model Diagram

```
                ┌──────────────┐
                │   User Hover │
                └──────┬───────┘
                       │
                       ▼
               ┌───────────────┐
               │ hoverIndex    │
               └───────────────┘
                       │
                       │ (mouse leave)
                       ▼
                ┌──────────────┐
                │   Reset      │
                └──────────────┘
```

```
                ┌──────────────┐
                │   User Click │
                └──────┬───────┘
                       │
                       ▼
               ┌───────────────┐
               │ selectedIndex │
               └───────────────┘
                       │
                       ▼
               ┌───────────────┐
               │ onChange()    │
               └───────────────┘
```

---

## 🔎 Key State Separation

```
hoverIndex     → Temporary visual state
selectedIndex  → Persistent saved state
```

Interviewer is testing whether you **separate these two clearly**.

---

# Phase 2 — Render Props Architecture

## 🎯 Requirement

Make the component UI-agnostic.

Instead of hardcoding a Star:

Parent should pass rendering logic.

---

## 🏗 Component Responsibility Diagram

```
Parent Component
      │
      │  provides renderItem()
      ▼
┌────────────────────┐
│  Rating Component  │
│                    │
│  - hover logic     │
│  - click logic     │
│  - state handling  │
└────────────────────┘
      │
      │  calls renderItem(index, state)
      ▼
Custom UI (Star / Heart / Emoji)
```

---

## 🔎 What Interviewer Checks

```
Logic  ≠  Presentation
```

If tightly coupled → mid-level  
If abstracted cleanly → senior thinking

---

# Phase 3 — Hover vs Selected Conflict

## 🎯 Scenario

User has already selected:

```
Selected = 3
```

Visual:

```
★ ★ ★ ☆ ☆
```

Now user hovers on 5:

---

## 🧠 State Conflict Diagram

```
selectedIndex = 3
hoverIndex    = 5
```

Priority logic:

```
IF hoverIndex exists
    render based on hoverIndex
ELSE
    render based on selectedIndex
```

---

## 🎨 Visual Differentiation Model

```
State Layering

Layer 1 → Selected (saved)
Layer 2 → Hover (preview)
```

Example logic:

```
Index <= selectedIndex → Locked Color
Index <= hoverIndex    → Preview Color
```

Interviewer wants to see:

- State priority thinking
    
- Conditional rendering clarity
    
- UX awareness
    

---

# Phase 4 — Optimistic Update Flow

Now we simulate backend behavior.

---

## 🎯 Requirement

- Instant UI update
    
- Show loading indicator
    
- Revert if API fails
    

---

## 🧠 Optimistic Update Flow Diagram

```
User Click
    │
    ▼
Store previousValue
    │
    ▼
Update selectedIndex immediately
    │
    ▼
Set loading = true
    │
    ▼
Simulated API Call
    │
 ┌──┴───────────────┐
 │                  │
 ▼                  ▼
Success            Failure
 │                  │
 ▼                  ▼
Keep value      Revert to previousValue
 │                  │
 ▼                  ▼
loading = false   loading = false
```

---

## 🔥 Critical State Model

You now have:

```
selectedIndex
hoverIndex
loading
previousValue
```

Interviewer checks:

- Can you track previous state?
    
- Can you revert safely?
    
- Can you handle async logic cleanly?
    

---

# Phase 5 — Accessibility Structure

## 🎯 Requirement

Do NOT use div/span.

---

## 🧠 Semantic Structure Diagram

```
Rating Container
    │
    ├── Button (Item 1)
    ├── Button (Item 2)
    ├── Button (Item 3)
    ├── Button (Item 4)
    └── Button (Item 5)
```

Keyboard flow:

```
Tab → Focus Item
Enter/Space → Select
Arrow Keys → Optional navigation
```

---

# Phase 6 — Dynamic Color Logic

## 🎯 Requirement

Color depends on selected value.

---

## 🧠 Rating-to-Color Mapping Diagram

```
1–2  → Red
3    → Yellow
4–5  → Green
```

For configurable count:

```
percentage = selectedIndex / totalItems
```

Example:

```
0–40%  → Red
40–70% → Yellow
70–100% → Green
```

Interviewer checks adaptability.

---

# 🏆 Final Combined State Architecture

```
                Rating Component

States:
--------------------------------
hoverIndex
selectedIndex
previousValue
loading
totalItems (prop)

Events:
--------------------------------
onMouseEnter
onMouseLeave
onClick
API Response

Derived Logic:
--------------------------------
displayIndex =
    hoverIndex ?? selectedIndex
```

---

# 🎯 What Makes This Senior-Level

```
✔ Clear state separation
✔ Render props abstraction
✔ Async rollback handling
✔ UX state layering
✔ Accessibility awareness
✔ Dynamic logic scaling
```

---

# 💡 Why Line Diagrams Work Well in Interviews

They show:

- Structured thinking
    
- Clear state modeling
    
- System design mindset
    
- Separation of concerns
    

Most candidates jump into code.  
Senior candidates draw state diagrams first.

---
