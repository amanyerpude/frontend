# Async Patterns

## 🚦 Throttle

**[Source: dump_one.md, Lines 137-183]**

### Q: How Can You Prevent a Function from Being Called Multiple Times?

Common challenge — especially with **scroll**, **resize**, or **button spam** events.

### ✨ Answer: Throttle

Throttle ensures a function runs at most **once every X milliseconds**,

no matter how many times it's triggered.

### Implementation:

```jsx
function throttle(fn, limit) {
  let inThrottle;
  return function (...args) {
    if (!inThrottle) {
      fn.apply(this, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}
```

### Use Case:

```jsx
window.addEventListener(
  'scroll',
  throttle(() => console.log('Scrolling...'), 500)
);
```

### ✅ Why Use Throttle?

- Controls rapid-fire events (scroll, resize)
- Improves performance & UX
- Prevents duplicate API calls

💡 **Master throttle = smoother, faster apps**

---

## 🛑 Debounce

**[Source: dump_two.md, Lines 173-235]**

5. **Implement a debounce function.**
    - How would you cancel a pending call?
    - Where is debounce useful in real-world apps?

---

## 🚦 Throttle (Advanced)

**[Source: dump_two.md, Lines 173-235]**

6. **Implement a throttle function.**
    - How would you support both leading and trailing options?
    - Where would throttle be preferred over debounce?

---

## 🔥 Advanced Debounce/Throttle

**[Source: dump_four.md, Lines 119-145]**

7. Create a debouncing function with leading and trailing calls.

