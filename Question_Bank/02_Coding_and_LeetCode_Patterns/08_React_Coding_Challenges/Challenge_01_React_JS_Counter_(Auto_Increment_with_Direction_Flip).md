Awesome — let’s start with the **React JS Auto-Increment Counter** that **flips direction** when it hits bounds.

---

## 🔹 **Challenge 1: React JS Counter (Auto Increment with Direction Flip)**

### 🧠 **Interview-style Prompt:**

> Build a React component that displays a number and **automatically increments it every second**.  
> When it reaches 10, it should start **counting backward**. When it hits 0, it should **flip again** to counting forward — and so on indefinitely.

---

### 🧱 **Step-by-Step Breakdown**

### 🎯 Requirements:

- Counter auto-increments every 1 second
    
- Direction flips at bounds: `0` and `10`
    
- Keeps running like a ping-pong
    

---

## ✅ **Working React Component**

```jsx
import { useEffect, useState } from "react";

function PingPongCounter() {
  const [count, setCount] = useState(0);
  const [direction, setDirection] = useState(1); // 1 for up, -1 for down

  useEffect(() => {
    const interval = setInterval(() => {
      setCount(prev => {
        let next = prev + direction;

        if (next > 10) {
          setDirection(-1);
          return 10;
        }

        if (next < 0) {
          setDirection(1);
          return 0;
        }

        return next;
      });
    }, 1000);

    return () => clearInterval(interval);
  }, [direction]);

  return (
    <div style={{ fontSize: "2rem", textAlign: "center" }}>
      Count: {count}
    </div>
  );
}

export default PingPongCounter;
```

---

### 🔍 Key Concepts Used:

- `useState` for `count` and `direction`
    
- `setInterval` in `useEffect` to update the count every 1 second
    
- Flip `direction` whenever we hit the boundaries (`0` or `10`)
    
- Clean up interval using `return () => clearInterval()`
    

---

### 🧠 What You Say in an Interview:

> “I used state to track the count and direction, then used an interval to increment the count based on direction. At each update, I check if bounds are hit and flip direction accordingly. The interval is cleaned up on re-renders using useEffect.”

---

Want to move on to **Challenge 2: Counter that pauses after 10 and then continues next range** (TEKsystems-style)?