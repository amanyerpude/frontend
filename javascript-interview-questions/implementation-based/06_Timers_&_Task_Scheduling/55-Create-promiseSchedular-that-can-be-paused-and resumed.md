

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

