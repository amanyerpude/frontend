

--------------------------------------------------------------------------
Video_URL : https://youtu.be/xNf_jEKz13Q?si=4QuTt6gJCiyRQ9G8

This question was asked in Hive's 2025 Frontend Interview Test - [https://learnersbucket.com/wp-content...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXpqak5tU0NoMUZJMGxOSFlmdDVGRG44R01kUXxBQ3Jtc0ttdHlTYmpkN0ZyNmRoLWJjZlVGRVotQTJweXVXWTB3a0x0R3FPQjFUMThiQXN5cEVCdURwQnlQSzUxTlFYQWJNSjhldHBCRkhzSEcxX2hRLTc2VWFIV0NKbkFoYmdJM0VteTQ1QkFUQU4xaFp5WW51cw&q=https%3A%2F%2Flearnersbucket.com%2Fwp-content%2Fuploads%2F2025%2F08%2FHive-Frontend-Developer-Test-2025.pdf&v=xNf_jEKz13Q). The problem statement reads as:- To create a JavaScript class that accepts an array of functions. The functions can be async functions. The class exposes methods to execute the array of promises in serial (one by one) as well as pause the execution. Methods: run() – Executes the array of functions in serial. async pause() – Pauses the execution of the functions. getState() – Returns the current state – InProgress | Paused | Completed and unexecuted functions indices. runAllUnexecutedFunctions() – Executes all unexecuted functions.

--------------------------------------------------------------------------

--------------------------------------------------------------------------

This is a comprehensive reconstruction of the **Promise Scheduler** coding challenge. I have scraped the text from all images and organized it into a clean, structured format optimized for Obsidian.

---

# Promise Scheduler Challenge

## 1. Problem Statement

The goal is to create a **JavaScript Class** that accepts an array of functions (which may be asynchronous). The class exposes methods to execute these functions in **serial** (one by one) while providing the ability to **pause** execution.

### Key Requirements

- Functions must be executed one by one (sequentially).
    
- The scheduler must support pausing.
    
- After a pause, resuming via `run()` should start exactly where the scheduler left off.
    
- The class must handle both synchronous and asynchronous functions.
    

---

## 2. Constructor & Options

The class should be named `PromiseScheduler`. It accepts an array of functions and an optional `options` object.

### Constructor Signature

JavaScript

```
const promiseSchedulerInstance = new PromiseScheduler(asyncFunctionsWhichReturnPromises, options);
```

### The `options` Object

|**Property**|**Type**|**Description**|
|---|---|---|
|`startIndex`|`number`|The index to start execution from when `run()` is called for the first time. (Default: `0`)|
|`callbacks`|`object`|An object containing lifecycle hooks.|
|`callbacks.onCompleted`|`function`|Triggered when all functions have been resolved or rejected. Receives `arrayOfResultsOfAllFunctions` as an argument.|

---

## 3. Class Methods

You are required to implement the following four methods:

### `run()`

- Starts executing functions in serial starting from the `startIndex` (or the current internal index if resumed).
    
- Does not return anything.
    
- If already `in-progress`, calling this should have no effect.
    

### `async pause()`

- Pauses the scheduler.
    
- **Crucial:** It must `await` the currently executing function to resolve before officially pausing.
    
- Next execution of `run()` begins from the next index in the array.
    

### `getState()`

Returns an object representing the current internal state of the scheduler:

JavaScript

```
{
  status: 'in-progress' | 'paused' | 'completed',
  unexecutedFunctionsIndices: [] // Array of indices not yet executed
}
```

### `runAllUnexecutedFunctions()`

- Triggers the scheduler to execute all pending functions in serial.
    
- Must handle cases where `startIndex` was non-zero.
    
- Has no effect if the scheduler is already in an `in-progress` state.
    

---

## 4. Usage Examples

### Input: Array of Functions

The input array can contain various types of functions that return promises or values.

JavaScript

```
const asyncFunctionsWhichReturnPromises = [
  // Example 1: Standard Promise with setTimeout
  () => new Promise((resolve) => setTimeout(() => resolve(true), 5000)),
  
  // Example 2: Async function using await
  async () => {
    await delay(5000);
    return true;
  },
  
  // Example 3: Image loading Promise
  () => {
    return new Promise((resolve, reject) => {
      const image = new Image();
      image.onload = () => resolve(image);
      image.onerror = () => reject();
      image.src = "somePng.png";
    });
  },
  // ... more functions
];
```

### Execution Flow Example

JavaScript

```
// Initialization
const options = {
  startIndex: 0,
  callbacks: {
    onCompleted: (results) => console.log(results)
  }
};

const scheduler = new PromiseScheduler(asyncFunctionsWhichReturnPromises, options);

// Start execution
scheduler.run();

// Example: Pause after 6 seconds
await delay(6000);
await scheduler.pause();

// Check State
const state = scheduler.getState();
/* Example Output if 3 functions finished before pause:
{
  status: 'paused',
  unexecutedFunctionsIndices: [3, 4, 5]
}
*/

// Resume
scheduler.runAllUnexecutedFunctions();
```

--------------------------------------------------------------------------

This is a classic "Senior Frontend/System Design" interview question. It tests your knowledge of **Asynchronous JavaScript**, **State Management**, and **Class Architecture**.

To ace this, you shouldn't just start typing. You need to show the interviewer how you think. Here is the step-by-step roadmap to solving this incrementally while narrating your thought process.

---

## Phase 1: The "Clarification & Strategy" (2-3 Minutes)

**What to say:**

> "Before I jump into the code, I want to make sure I understand the core constraints. We need to execute functions in **serial**, meaning we can't just `Promise.all` them. We also need a way to **pause**, but importantly, `pause()` must wait for the _current_ task to finish rather than killing it mid-flight. I’ll approach this by maintaining an internal pointer (index) and a status flag."

**Mental State:** Calm, analytical, and collaborative. Treat the interviewer as a teammate you are brainstorming with.

---

## Phase 2: The Skeleton (Defining State)

**What to write:** Define the constructor and the initial state.

**What to say:** > "I'll start by setting up the class structure. I need to store the functions, the current index, the results, and the status. I'll also ensure we respect the `startIndex` provided in the options."

JavaScript

```
class PromiseScheduler {
  constructor(tasks, options = {}) {
    this.tasks = tasks;
    this.results = [];
    this.currentIndex = options.startIndex || 0;
    this.onCompleted = options.callbacks?.onCompleted;
    
    // Status can be 'idle', 'in-progress', 'paused', 'completed'
    this.status = 'idle';
    this.currentPromise = null; // To track the currently running task
  }

  getState() {
    return {
      status: this.status,
      unexecutedFunctionsIndices: this.tasks
        .map((_, i) => i)
        .slice(this.currentIndex)
    };
  }
}
```

---

## Phase 3: The Engine (The `run` logic)

**What to write:** Implement the serial execution.

**What to say:** > "Now for the core execution. I’ll create a private method `#execute` that processes tasks one by one. If the status changes to 'paused', the loop should break. I'll use a `while` loop because it's easier to manage the index and the pause condition than a `forEach`."

JavaScript

```
  async run() {
    if (this.status === 'in-progress' || this.status === 'completed') return;
    
    this.status = 'in-progress';
    
    while (this.currentIndex < this.tasks.length && this.status === 'in-progress') {
      const task = this.tasks[this.currentIndex];
      
      try {
        // We store the promise so pause() can wait for it
        this.currentPromise = task();
        const result = await this.currentPromise;
        this.results[this.currentIndex] = result;
        this.currentIndex++;
      } catch (error) {
        this.results[this.currentIndex] = error;
        this.currentIndex++;
      }
    }

    if (this.currentIndex === this.tasks.length) {
      this.status = 'completed';
      if (this.onCompleted) this.onCompleted(this.results);
    }
  }
```

---

## Phase 4: The Control (Pause & Resume)

**What to write:** Implement `pause` and the alias method.

**What to say:** > "The tricky part is `pause()`. The requirement says we must wait for the current task to finish. Since I saved the current task's promise in `this.currentPromise`, I can simply `await` it after setting the status to 'paused'. This ensures a 'graceful' stop."

JavaScript

```
  async pause() {
    if (this.status !== 'in-progress') return;
    
    this.status = 'paused';
    // Wait for the currently executing task to finish its work
    await this.currentPromise;
  }

  runAllUnexecutedFunctions() {
    // This is essentially an alias for run(), 
    // but the name implies we start from wherever we are.
    this.run();
  }
```

---

## Phase 5: The "Polishing" (Corner Cases)

**What to say to impress them:**

> "To make this production-ready, I should consider a few things:
> 
> 1. **Concurrency:** I've added a check in `run()` to prevent multiple loops from running at once.
>     
> 2. **Error Handling:** I wrapped the task execution in a `try/catch` so one failing promise doesn't crash the whole scheduler.
>     
> 3. **Immutability:** In `getState()`, I’m returning a new object and a sliced array to prevent the outside world from accidentally modifying my internal state."
>     

---

### Key Interview Tips:

1. **Think Out Loud:** If you are silent for more than 30 seconds, the interviewer doesn't know if you're stuck or thinking. Say, _"I'm just thinking about how to handle the pause index right now..."_
    
2. **Validate the "Async Pause":** Interviewers love to see if you realize that `await task()` inside a loop means you can't "kill" the task instantly. Emphasize that your `pause()` waits for the current `this.currentPromise`.
    
3. **State Management:** Always use a `status` variable. It makes the logic much cleaner than using multiple booleans like `isPaused = true`.
    

**Would you like me to create a "Mock Interview" scenario where I ask you a follow-up question based on this code?**

--------------------------------------------------------------------------

This is a classic Senior Frontend and System Design interview question, recently featured in Hive's 2025 Frontend Interview Test. It is designed to test your mastery of **Asynchronous JavaScript, State Management, and Class Architecture**.

To effectively practice and deliver this answer in an interview, you should avoid just jumping into writing code. Instead, build the solution incrementally, narrating your thought process to the interviewer. Here is a highly descriptive, step-by-step roadmap to answering this question perfectly.

### Phase 1: Clarification & Strategy (The "Think Out Loud" Phase)

Before writing any code, verbally establish the constraints of the problem with your interviewer.

**What to say:**

- "To ensure I fully understand the requirements: we are building a `PromiseScheduler` class that takes an array of functions (sync or async) and executes them **in serial** (one by one), meaning we cannot use `Promise.all`."
- "The scheduler needs a `pause()` method. A crucial constraint here is that we cannot kill a JavaScript promise mid-flight. Therefore, pausing must be 'graceful'—it must wait for the currently executing task to finish before halting the queue."
- "I will manage this by keeping an internal state pointer for the current index, an array to track unexecuted functions, and a status flag."

### Phase 2: Building the Skeleton (Defining State and Constructor)

Next, define the class structure and how you will track internal state.

**What to explain:**

- The constructor takes the array of tasks and an `options` object.
- The options contain a `startIndex` (defaulting to 0) and lifecycle `callbacks` like `onCompleted`.
- We need variables to track the **current status** (`idle`, `in-progress`, `paused`, or `completed`), the **current index**, and the **currently executing promise** so we can await it if paused.

**The Code Structure:**

```
class PromiseScheduler {
  constructor(tasks, options = {}) {
    this.tasks = tasks;
    this.results = [];
    this.currentIndex = options.startIndex || 0;
    this.onCompleted = options.callbacks?.onCompleted;

    // Crucial state management variables
    this.status = 'idle';
    this.currentPromise = null;
  }
}
```

### Phase 3: The Engine (Implementing `run()`)

Now, explain how you will process the tasks sequentially. You can use either a recursive approach with a processing flag, or a `while` loop. The `while` loop is often easier to explain.

**What to explain:**

- "I'll implement the `run()` method. If the status is already `in-progress`, I will exit early to prevent concurrency issues (running two loops at once)."
- "I'll use a `while` loop to iterate through the tasks as long as the status remains `in-progress` and we haven't reached the end of the array."
- "Inside the loop, I will wrap the task execution in a `try/catch` block. This ensures that if one promise rejects, it doesn't crash the entire scheduler."
- "I will save the execution to `this.currentPromise` so the `pause` method has a reference to wait for."

**The Code Structure:**

```
  async run() {
    if (this.status === 'in-progress' || this.status === 'completed') return;
    this.status = 'in-progress';

    while (this.currentIndex < this.tasks.length && this.status === 'in-progress') {
      const task = this.tasks[this.currentIndex];
      try {
        // Store the promise so pause() can gracefully wait for it
        this.currentPromise = task();
        this.results[this.currentIndex] = await this.currentPromise;
      } catch (error) {
        this.results[this.currentIndex] = error;
      } finally {
        this.currentIndex++;
      }
    }

    // Check if we finished all tasks natively
    if (this.currentIndex === this.tasks.length) {
      this.status = 'completed';
      if (this.onCompleted) this.onCompleted(this.results);
    }
  }
```

### Phase 4: The Control (Implementing `async pause()`)

This is the most critical part of the interview. Interviewers specifically look for how you handle stopping an asynchronous queue.

**What to explain:**

- "For the `pause()` method, I will first check if we are actually `in-progress`. If so, I'll flip the status to `paused`. This immediately breaks the `while` loop from triggering the _next_ task."
- "However, to fulfill the requirement of pausing gracefully, **I must `await this.currentPromise`**. This ensures the currently executing async function resolves before the scheduler officially considers itself fully paused."

**The Code Structure:**

```
  async pause() {
    if (this.status !== 'in-progress') return;
    this.status = 'paused';
    // Wait for the currently executing task to finish
    await this.currentPromise;
  }
```

### Phase 5: State Reporting and Resuming Execution

Finally, you must implement the methods that expose the internal state and allow for executing the remaining functions.

**What to explain:**

- "For `getState()`, the requirement is to return the status and the unexecuted indices. To enforce **immutability**, I'll return a brand new object and slice the array so the caller cannot accidentally mutate our internal state."
- "For `runAllUnexecutedFunctions()`, because my `run()` method relies on the `currentIndex` which is preserved during a pause, I can simply call `this.run()` to pick up exactly where we left off." _Note: If the `startIndex` was greater than 0, you must ensure logic exists to wrap around and execute indices 0 to `startIndex - 1` if that is an expected edge case._

**The Code Structure:**

```
  getState() {
    return {
      status: this.status,
      unexecutedFunctionsIndices: this.tasks
        .map((_, i) => i)
        .filter(i => i >= this.currentIndex) // Filters out executed indices
    };
  }

  runAllUnexecutedFunctions() {
    // Resumes execution from the current preserved index
    this.run();
  }
```

### Final Interview Tips for Practice

1. **Think Out Loud:** Never be silent for more than 30 seconds. If you are stuck on managing the indices, say, _"I'm just thinking about how to handle the pause index right now..."_.
2. **Highlight Edge Cases:** To secure a "Senior" evaluation, explicitly point out your `try/catch` block for error handling and your concurrency checks that prevent multiple `run()` calls from overlapping.
3. **Acknowledge Complexity:** Mention that tracking unexecuted indices gets highly complex if `startIndex` is non-zero (e.g., starting at index 3 out of 5). Explain that a robust way to handle this in a real-world scenario is keeping an internal map (`promisesPending`) to track exactly which index resolved true/false, rather than relying solely on a linear integer.
--------------------------------------------------------------------------