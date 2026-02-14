
--------------------------------------------------------------------------

# 🚀 Stage 0 — Problem Framing & Mental Model (Before Writing Code)

Most candidates jump into coding.

Senior candidates **clarify first**.

---

# 🎤 What You Say to the Interviewer (Before Coding)

> “Before I start coding, I want to clarify the requirements and outline the architecture I’ll follow.”

Then summarize:

- Configurable item count
    
- Hover preview
    
- Click to select
    
- Reset on leave
    
- Parent callback
    
- Optimistic update
    
- Rollback on failure
    
- Accessibility
    
- Dynamic coloring
    
- UI abstraction support
    

This signals structured thinking.

---

# 🧠 Step 0.1 — Identify Core States

From the diagram:

We need:

```
selectedIndex → persistent state
hoverIndex    → temporary state
loading       → async state
previousValue → rollback state
totalItems    → config
```

You tell interviewer:

> “I will model this component around a single state object and derive UI from state instead of mutating DOM directly.”

This is VERY strong.

---

# 🧠 Step 0.2 — Decide Architecture Pattern (Vanilla JS)

We will NOT:

- Randomly attach event listeners everywhere
    
- Directly mutate styles on hover
    
- Write spaghetti code
    

Instead, we’ll structure like this:

```
createRating({
  container,
  totalItems,
  onChange,
  renderItem
})
```

Why?

Because Phase 2 requires UI abstraction.

---

# 🧠 Step 0.3 — Define Rendering Philosophy

We will follow:

```
UI = render(state)
```

Meaning:

Every interaction:

1. Update state
    
2. Call render()
    
3. Render reflects state
    

Never:

```
button.style.color = ...
```

outside of render.

This is React-like thinking in vanilla.

Interviewers LOVE this.

---

# 🧠 Step 0.4 — Decide SVG Strategy

We will:

- Use inline SVG
    
- Set `fill` dynamically
    
- Wrap inside `<button>` for accessibility
    

We will NOT:

- Use div
    
- Use span
    
- Use img
    
- Use text star
    

---

# 🧠 Step 0.5 — Define File Structure

In interview, we simulate:

```
index.html
styles.css
script.js
```

Simple and clean.

---

# 🎯 Stage 0 Summary (Before Writing Code)

You have now demonstrated:

- Requirement analysis
    
- State modeling
    
- Separation of concerns
    
- Declarative rendering mindset
    
- Async awareness
    
- Accessibility awareness
    
- Scalability thinking
    

Without writing a single line of code.

That’s senior-level beginning.

---

# 🏆 What Interviewer Is Thinking Now

If you speak like this before coding:

They think:

> “This person understands architecture.”

Instead of:

> “Let’s see if they can hack something together.”

Huge difference.

---

# ⏸ Now We Move to Stage 1

Next step will be:

👉 Build minimal static structure  
👉 Create `createRating()` factory  
👉 Render static SVG buttons  
👉 No interaction yet

Say:

**Start Stage 1**

And we’ll begin actual implementation — incrementally.

--------------------------------------------------------------------------

Good. Now we start writing code.

But we still go step-by-step.

No hover.  
No click.  
No async.  
No abstraction yet.

Just foundation.

---

# 🚀 Stage 1 — Minimal Static Structure (Structured Vanilla)

---

## 🎤 What You Say to the Interviewer

> “I’ll first create a minimal structure and a factory function to encapsulate the rating logic.  
> Initially, I’ll render static SVG buttons to establish the base UI.”

This shows:

- You’re not dumping logic in global scope
    
- You’re thinking component-style even in vanilla JS
    

---

# 🧠 What You’re Thinking Internally

We need:

1. HTML container
    
2. CSS base styles
    
3. `createRating()` function
    
4. `render()` function
    
5. Static SVG rendering (no state yet)
    

We are building the skeleton.

---

# 📁 File Structure

```
index.html
styles.css
script.js
```

---

# 💻 Step 1 Code

---

## 📄 index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Rating Component</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>

  <h2>Rate this product</h2>
  <div id="rating-root"></div>

  <script src="script.js"></script>
</body>
</html>
```

---

## 📄 styles.css

```css
.rating-container {
  display: inline-flex;
  gap: 8px;
}

.rating-item {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}

.rating-item:focus {
  outline: 2px solid #333;
}
```

Notice:

- We used `<button>`
    
- We added focus styling
    
- Already thinking accessibility
    

---

## 📄 script.js

```javascript
function createRating({ container, totalItems = 5 }) {
  function render() {
    container.innerHTML = "";

    const wrapper = document.createElement("div");
    wrapper.className = "rating-container";

    for (let i = 0; i < totalItems; i++) {
      const button = document.createElement("button");
      button.className = "rating-item";

      button.innerHTML = `
        <svg viewBox="0 0 24 24" width="32" height="32" fill="lightgray">
          <path d="M12 2l2.9 6.6 7.1.6-5.4 4.6 1.6 7-6.2-3.7-6.2 3.7 1.6-7L2 9.2l7.1-.6L12 2z"/>
        </svg>
      `;

      wrapper.appendChild(button);
    }

    container.appendChild(wrapper);
  }

  render();
}

const root = document.getElementById("rating-root");

createRating({
  container: root,
  totalItems: 5,
});
```

---

# 🎤 What You Say After Writing It

> “Right now this is a static implementation.  
> I’ve encapsulated rendering inside a `createRating` factory function to avoid polluting the global scope.  
> Next, I’ll introduce internal state and click interaction.”

This shows:

- You’re not writing loose JS
    
- You’re building a reusable module
    

---

# 🔎 What Interviewer Is Evaluating

- Did you structure code?
    
- Did you avoid global variables?
    
- Did you use semantic buttons?
    
- Did you separate HTML/CSS/JS cleanly?
    
- Did you think in component terms?
    

---

# 🧠 Why This Step Is Important

Many candidates:

- Directly query DOM
    
- Add random event listeners
    
- Mutate style inline
    

You didn’t.

You created a clean factory.

This is already above average.

---

# ⏸ Pause Here

Next Stage:

👉 Introduce state object  
👉 Add click interaction  
👉 Derive UI from `selectedIndex`  
👉 Keep render-driven updates

Say:

**Start Stage 2**

And we move forward.

--------------------------------------------------------------------------

Good.

Now we introduce **real state**.

This is where the interviewer starts evaluating your thinking seriously.

---

# 🚀 Stage 2 — Introduce State + Click Interaction

We are still in Phase 1 of the question.

We will now implement:

- Persistent selected state
    
- Click interaction
    
- UI derived from state
    
- No hover yet
    

---

# 🎤 What You Say to the Interviewer

> “Now I’ll introduce an internal state object to manage the selected value.  
> I’ll follow a render-driven approach where the UI always reflects the current state.”

That sentence alone shows maturity.

---

# 🧠 What You're Thinking Internally

We now need:

```
state = {
  selectedIndex: -1
}
```

Important rule:

We will NOT:

```
button.style.fill = ...
```

directly inside click.

Instead:

1. Update state
    
2. Call render()
    
3. Render reflects state
    

This mirrors React thinking.

---

# 💻 Updated script.js

We’ll modify the factory.

---

```javascript
function createRating({ container, totalItems = 5 }) {
  const state = {
    selectedIndex: -1,
  };

  function render() {
    container.innerHTML = "";

    const wrapper = document.createElement("div");
    wrapper.className = "rating-container";

    for (let i = 0; i < totalItems; i++) {
      const button = document.createElement("button");
      button.className = "rating-item";

      const fillColor =
        i <= state.selectedIndex ? "gold" : "lightgray";

      button.innerHTML = `
        <svg viewBox="0 0 24 24" width="32" height="32" fill="${fillColor}">
          <path d="M12 2l2.9 6.6 7.1.6-5.4 4.6 1.6 7-6.2-3.7-6.2 3.7 1.6-7L2 9.2l7.1-.6L12 2z"/>
        </svg>
      `;

      button.addEventListener("click", () => {
        state.selectedIndex = i;
        render();
      });

      wrapper.appendChild(button);
    }

    container.appendChild(wrapper);
  }

  render();
}

const root = document.getElementById("rating-root");

createRating({
  container: root,
  totalItems: 5,
});
```

---

# 🎤 What You Say After Writing It

> “Now the component maintains a `selectedIndex` state.  
> On click, I update the state and re-render.  
> The UI is fully derived from state instead of directly mutating DOM styles.”

This is very strong phrasing.

---

# 🔎 What Interviewer Is Evaluating

- Did you separate state from DOM?
    
- Did you avoid direct mutation?
    
- Is your render function deterministic?
    
- Is your logic clean?
    
- Are you thinking declaratively?
    

---

# 🧠 What You Just Demonstrated

You showed:

```
UI = f(state)
```

That’s framework-level thinking in vanilla JS.

That’s impressive in interviews.

---

# ⚠️ Small Discussion Point (If Asked)

We are re-rendering entire component on click.

That’s fine for small UI.

You don’t optimize unless asked.

---

# ⏸ Pause Here

Next Stage:

👉 Introduce hover state  
👉 Separate temporary vs persistent state  
👉 Implement preview behavior  
👉 Reset on mouse leave

This is where complexity increases.

Say:

**Start Stage 3**

And we continue.

--------------------------------------------------------------------------

Good.

Now the real separation test begins.

Most candidates fail here.

---

# 🚀 Stage 3 — Add Hover Preview (State Separation)

Now we implement:

- `hoverIndex` (temporary)
    
- Reset on mouse leave
    
- Hover overrides visually
    
- Keep `selectedIndex` untouched
    

This directly tests Phase 1 state separation.

---

# 🎤 What You Say to the Interviewer

> “Now I’ll introduce a separate `hoverIndex` state to handle temporary preview behavior.  
> Hover should not mutate the selected state.  
> The display logic will prioritize hover when it exists.”

That sentence signals strong architectural clarity.

---

# 🧠 What You're Thinking Internally

We now have:

```
state = {
  selectedIndex: -1,
  hoverIndex: -1
}
```

Display rule:

```
displayIndex = hoverIndex !== -1
               ? hoverIndex
               : selectedIndex
```

Important:

Hover must NOT overwrite selected.

---

# 💻 Updated script.js

We modify state + render logic.

---

```javascript
function createRating({ container, totalItems = 5 }) {
  const state = {
    selectedIndex: -1,
    hoverIndex: -1,
  };

  function render() {
    container.innerHTML = "";

    const wrapper = document.createElement("div");
    wrapper.className = "rating-container";

    const displayIndex =
      state.hoverIndex !== -1
        ? state.hoverIndex
        : state.selectedIndex;

    for (let i = 0; i < totalItems; i++) {
      const button = document.createElement("button");
      button.className = "rating-item";

      const fillColor =
        i <= displayIndex ? "gold" : "lightgray";

      button.innerHTML = `
        <svg viewBox="0 0 24 24" width="32" height="32" fill="${fillColor}">
          <path d="M12 2l2.9 6.6 7.1.6-5.4 4.6 1.6 7-6.2-3.7-6.2 3.7 1.6-7L2 9.2l7.1-.6L12 2z"/>
        </svg>
      `;

      button.addEventListener("click", () => {
        state.selectedIndex = i;
        render();
      });

      button.addEventListener("mouseenter", () => {
        state.hoverIndex = i;
        render();
      });

      button.addEventListener("mouseleave", () => {
        state.hoverIndex = -1;
        render();
      });

      wrapper.appendChild(button);
    }

    container.appendChild(wrapper);
  }

  render();
}
```

---

# 🎤 What You Say After Writing It

> “Now the component maintains two separate states:  
> `selectedIndex` for persistent value and `hoverIndex` for temporary preview.  
> The UI derives from a computed `displayIndex`.”

That explanation shows layered thinking.

---

# 🔎 What Interviewer Is Evaluating

- Did you separate temporary vs persistent state?
    
- Did you avoid overwriting selectedIndex?
    
- Is your derived logic clear?
    
- Is render still deterministic?
    
- Are event listeners structured cleanly?
    

---

# 🧠 What You Just Demonstrated

You now have layered state logic:

```
Persistent state  → selectedIndex
Temporary state   → hoverIndex
Derived state     → displayIndex
```

This is framework-level design in plain JS.

Very strong signal.

---

# ⚠️ Current Limitation

If:

```
selectedIndex = 2
hoverIndex = 4
```

All 5 stars turn gold.

We are not yet distinguishing locked vs preview.

That’s the bar-raiser question.

---

# ⏸ Pause Here

Next Stage:

👉 Differentiate locked vs hover visually  
👉 Layered color logic  
👉 Improve UX clarity

Say:

**Start Stage 4**

And we continue.

--------------------------------------------------------------------------

Good.

Now we enter the **UX bar-raiser phase**.

This is where average candidates stop.  
Stronger candidates level up.

---

# 🚀 Stage 4 — Differentiate Locked vs Hover Preview

Right now:

If

```
selectedIndex = 2
hoverIndex = 4
```

All 5 stars turn gold.

That hides which rating is actually saved.

We’ll fix that.

---

# 🎤 What You Say to the Interviewer

> “Currently hover completely overrides the selected state visually.  
> In a real product, it’s better to distinguish between the saved rating and the temporary preview.  
> I’ll layer the rendering logic to reflect both states clearly.”

That sentence signals UX maturity.

---

# 🧠 What You're Thinking Internally

We want this behavior:

If:

```
selectedIndex = 2
hoverIndex = 4
```

Then:

```
0 1 2 → gold (locked)
3 4   → blue (preview)
others → gray
```

So logic becomes:

```
IF hover exists:
    IF index <= selectedIndex → gold
    ELSE IF index <= hoverIndex → blue
    ELSE → gray
ELSE:
    IF index <= selectedIndex → gold
    ELSE → gray
```

This introduces layered rendering.

---

# 💻 Updated script.js

We modify only the color logic inside `render()`.

---

```javascript
function createRating({ container, totalItems = 5 }) {
  const state = {
    selectedIndex: -1,
    hoverIndex: -1,
  };

  function getFillColor(index) {
    if (state.hoverIndex !== -1) {
      if (index <= state.selectedIndex) {
        return "gold"; // locked
      } else if (index <= state.hoverIndex) {
        return "dodgerblue"; // preview
      } else {
        return "lightgray";
      }
    }

    return index <= state.selectedIndex
      ? "gold"
      : "lightgray";
  }

  function render() {
    container.innerHTML = "";

    const wrapper = document.createElement("div");
    wrapper.className = "rating-container";

    for (let i = 0; i < totalItems; i++) {
      const button = document.createElement("button");
      button.className = "rating-item";

      const fillColor = getFillColor(i);

      button.innerHTML = `
        <svg viewBox="0 0 24 24" width="32" height="32" fill="${fillColor}">
          <path d="M12 2l2.9 6.6 7.1.6-5.4 4.6 1.6 7-6.2-3.7-6.2 3.7 1.6-7L2 9.2l7.1-.6L12 2z"/>
        </svg>
      `;

      button.addEventListener("click", () => {
        state.selectedIndex = i;
        render();
      });

      button.addEventListener("mouseenter", () => {
        state.hoverIndex = i;
        render();
      });

      button.addEventListener("mouseleave", () => {
        state.hoverIndex = -1;
        render();
      });

      wrapper.appendChild(button);
    }

    container.appendChild(wrapper);
  }

  render();
}
```

---

# 🎤 What You Say After Writing It

> “I extracted the color logic into a separate function to keep the render method clean.  
> Now the saved rating and preview state are visually distinguishable.”

That shows code hygiene.

---

# 🔎 What Interviewer Is Evaluating

- Did you think about UX clarity?
    
- Did you avoid messy inline conditionals?
    
- Is your logic readable?
    
- Is state layering correct?
    
- Did you refactor responsibly?
    

---

# 🧠 What You Just Demonstrated

You moved from:

Functional implementation  
→ UX-aware layered architecture

That’s a noticeable jump.

---

# ⚠️ Architecture Observation

We are still:

- Re-rendering fully each interaction
    
- Not yet handling async
    
- Not yet handling rollback
    
- Not yet abstracting UI
    
- Not yet handling dynamic color scaling
    

Good.

We are pacing correctly.

---

# ⏸ Pause Here

Next Stage:

👉 Add parent callback  
👉 Add optimistic update simulation  
👉 Add loading state  
👉 Implement rollback on failure

This is where we move into system thinking.

Say:

**Start Stage 5**

And we continue.

--------------------------------------------------------------------------

