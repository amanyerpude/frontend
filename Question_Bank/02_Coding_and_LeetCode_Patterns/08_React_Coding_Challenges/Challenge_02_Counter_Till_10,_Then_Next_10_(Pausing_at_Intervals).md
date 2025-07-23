Awesome — let’s dive into:

---

## 🔹 **Challenge 2: Counter Till 10, Then Next 10 (Pausing at Intervals)**

📌 _Asked in TEKsystems 2nd round_

---

### 🧠 **Interview-style Prompt:**

> Build a React counter that:
> 
> - Counts from `1` to `10`, then **pauses for 1 second**
>     
> - Resumes from `11` to `20`, pauses again...
>     
> - Keeps doing this — count → pause → next batch
>     

---

## 🧱 **Step-by-Step Breakdown**

### 🎯 Requirements:

- Continuous counting
    
- Pauses after every 10 numbers (i.e. after 10, 20, 30, ...)
    
- Each number shows for 1 second
    

---

## ✅ **React Component with Staged Counting**

```jsx
import { useEffect, useState, useRef } from "react";

function StagedCounter() {
  const [count, setCount] = useState(1);
  const [isPaused, setIsPaused] = useState(false);
  const intervalRef = useRef(null);

  useEffect(() => {
    // Only run if not paused
    if (!isPaused) {
      intervalRef.current = setInterval(() => {
        setCount(prev => {
          if (prev % 10 === 0) {
            clearInterval(intervalRef.current);
            setIsPaused(true);

            // Resume after 1 second pause
            setTimeout(() => {
              setIsPaused(false);
            }, 1000);
          }
          return prev + 1;
        });
      }, 1000);
    }

    return () => clearInterval(intervalRef.current);
  }, [isPaused]);

  return (
    <div style={{ fontSize: "2rem", textAlign: "center" }}>
      Count: {count - 1}
    </div>
  );
}

export default StagedCounter;
```

---

### 🔍 Explanation:

- `count` starts from 1 and increments every second.
    
- When `count % 10 === 0`, it:
    
    - Clears the interval
        
    - Sets `isPaused = true`
        
    - Schedules a `setTimeout` to resume counting after 1 second
        
- `useEffect` re-runs whenever `isPaused` changes, restarting the interval
    

---

### 🧠 What You Say in an Interview:

> “I used an interval to increment the counter every second. Once it reaches a multiple of 10, I pause using a timeout. When the pause is over, I resume the interval using state control.”

---

Would you like to:

- Try a variation (e.g. customizable batch size)?
    
- Or move on to another real-world React coding challenge like **debounced search**, **controlled form**, or **infinite scroll**?