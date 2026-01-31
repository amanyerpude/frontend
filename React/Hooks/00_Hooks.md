

---

## 1. Foundation Hooks

These are the absolute essentials. You will use these in nearly every project to manage data flow and component lifecycles.

- **`useState`**: Manages local component state.
    
- **`useEffect`**: Handles side effects like data fetching or DOM updates after rendering.
    
- **`useContext`**: Accesses global data without "prop drilling".
    

---

## 2. Optimization & Advanced State

Move these here because they focus on performance or managing complex logic that `useState` alone makes messy.

- **`useReducer`**: For complex state logic or transitions that follow a predictable pattern.
    
- **`useRef`**: For persisting values across renders without triggering a re-render, or for direct DOM access.
    
- **`useMemo`**: Caches the result of an expensive calculation.
    
- **`useCallback`**: Caches a function definition to prevent unnecessary re-renders in child components.
    
- **`useTransition`**: Marks state updates as non-urgent to keep the UI responsive during heavy re-renders.
    

---

## 3. Specialized & Edge Case Hooks

These should be used sparingly for specific technical hurdles, often related to browser painting or library development.

- **`useLayoutEffect`**: **(Move this here only)**. Use this only for measuring the DOM before the browser paints to avoid visual flickers.
    
- **`useId`**: Generates unique IDs for accessibility attributes.
    
- **`useDebugValue`**: Used inside custom hooks to provide labels in React DevTools.
    

---

## 4. Architectural Patterns

These aren't "built-in" tools but rather how you structure your own logic.

- **Custom Hooks**: This is where you create your own functions (e.g., `useAuth`, `useFetch`) that combine the foundation hooks into reusable logic.
    

---
