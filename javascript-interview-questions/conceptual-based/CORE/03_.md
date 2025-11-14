

----------------------------------------------------------------------------------------------------------------------------------------------------
- #### What is Event Loop in Javascript | What are task queues
	- https://youtu.be/JdJIUoa9qJU?si=ipMpKVMkJeFLUrd_

This response adheres strictly to the details provided in the sources regarding the JavaScript Event Loop, its components, behaviors, and the key concepts discussed.

### I. Session Agenda and Core Takeaways

The agenda for exploring the Event Loop in JavaScript includes covering:

1. What is single-thread vs. multi-thread programming.
2. The problem specific to single-threaded languages like JavaScript.
3. The different queues available in the JavaScript runtime and how they function.
4. What the Event Loop is.
5. The internal components working within the Event Loop.
6. Implementing a small functionality simulating the Event Loop to understand the theoretical part.
7. Solving two to three questions based on the Event Loop.
8. Sharing **four essential things** (mantras) to remember at the end. These four points are considered the **crux** or **resultant** of the session and can help solve Event Loop questions within seconds.

### II. Single-Threaded vs. Multi-Threaded Concepts

**Threads and Operating Systems:**

- Threads are a concept of the Operating System (OS).
- When a program like Microsoft Word or Chrome is launched, it can perform multiple tasks simultaneously, such as fetching data from a server, taking a photo, or checking location.
- **Java is a multi-threaded language**.

**JavaScript (JS) Specifics:**

- **JavaScript is a single-threaded language**.
- When a browser tab is opened, it is managed by **only one thread**.
- In a single-threaded system, only **one single work** can be done at a given time.

**Problems with Single-Threaded JS:**

- The primary problem is that only **one task can be completed at one time**.
- Execution runs **top-to-bottom**.
- If one line of code is executing, the next line must wait until the first line's execution is finished.
- If a long-running or heavy task (like an infinite loop) is executed, the entire tab/browser can become **unresponsive**.
- When running a heavy operation, other pieces of code have to wait.

_Example of Unresponsiveness:_ If an infinite loop is run in a JS thread, tasks like text selection or button clicks cannot occur. While some browsers (like the one demonstrated, likely Edge/Chrome) might move GIF logic to the GPU to keep graphics playing, others (like Safari in the demo) will freeze completely, demonstrating the blocking nature of long tasks.

### III. Execution Mechanism: The Call Stack

- The **Call Stack** is the concept responsible for **executing your code**.
- Code is pushed line by line into the Call Stack.
- The Call Stack executes tasks one by one.
- Only ** one task** can be pushed onto the Call Stack at a time.
- Execution of a subsequent function cannot start until the execution of the preceding function is finished.
- Tasks are pushed onto the Call Stack and, upon completion, they are **popped** from memory.
- The Call Stack operates on a **Last In, First Out (LIFO)** basis, like a normal stack.

### IV. Web APIs and Asynchronous Operations

The Call Stack model alone cannot explain asynchronous behavior like `setTimeout` or Promises, where execution order might be out of sync (e.g., `setTimeout(log 2, 0)` executes _after_ synchronous logs 1 and 3).

**APIs and Web APIs:**

- **API (Application Programming Interface)** means Application Programming Interface. APIs help connect two different systems together (analogous to a translator between speakers of different languages).
- **Web API** is a generalized term used in the context of the browser.
- Web APIs connect the **JavaScript Run Time** (where the Call Stack resides) to the **Browser**.
- The JavaScript Run Time does not inherently understand concepts like `fetch`, `setTimeout`, or `setInterval`.
- Web APIs are provided by the **browser**, not JavaScript.
- _Popular Web APIs:_ `setTimeout`, Promises, `fetch`, `localStorage`, `sessionStorage`, `document` (DOM manipulation), `console.log`, `geolocation`, and anything that is part of the browser.

**Web API Workflow (The Cycle):**

1. The JavaScript engine encounters an asynchronous task (e.g., `setTimeout`) and immediately passes it to the Web API.
2. Web APIs relay the instructions to the browser.
3. Once the browser completes the instruction (e.g., the specified time for `setTimeout` is up), the browser notifies the Web API.
4. **Web APIs do not run the callback**.
5. Web APIs simply hand over the callback to the JavaScript Run Time.
6. The JavaScript Run Time does **not execute the code immediately**.
7. Web APIs push the task to the **relevant Task Queues**. This is necessary because the Call Stack might be busy.

### V. Browser Capabilities and Rendering

**The Browser Platform:**

- The browser is a powerful software written in C++.
- Unlike JavaScript, browsers are **not limited** to single-threading and **can perform tasks in parallel**.
- _Features managed by the Browser:_ Rendering, Camera, Microphone, Network services, GPU, Sensors, Storage options, and File System.
- Heavy work is offloaded by JS to the browser via Web APIs.

**Rendering and Timing:**

- The statement that `setTimeout` runs a callback _after_ the specified time is a **myth**.
- `setTimeout` schedules a callback that is **added to the Task Queue after the specified time** and is only executed **once the Call Stack is empty**.
- **Rule for UI Updates:** **JavaScript code always runs to completion before any rendering can happen**. UI updates are not instantaneous.
- Browsers are intelligent; they wait for the **right time** to update the UI (style changes, animations).
- The waiting time is typically around **16 milliseconds (ms)**, which corresponds to 60 Frames Per Second (1000 ms / 60 ≈ 16 ms).
- Developers generally have **12 to 14 ms** to perform their work before performance issues (lagging, choppy animations) occur, as the remaining time is reserved for browser rendering tasks.
- If performing sequential DOM manipulations (e.g., changing background color multiple times), the browser typically processes only the **last instruction** because it recognizes it as the same repetitive work.

**Request Animation Frame (RAF):**

- RAF is provided by the browser to manage UI updates.
- RAF has a **higher priority** than other DOM operations.
- The callback passed to RAF runs **before** style calculation, layout calculation, and painting.
- If an animation is performed, RAF is preferable to `setTimeout` because it is **well-calibrated** with the device's frame rate (e.g., 60 Hz, 120 Hz, 144 Hz).
- If a normal DOM update conflicts with a subsequent RAF call (changing the same style), the RAF will **override** the previous instruction because of its higher priority in the rendering engine.
- If a developer wants two separate rendering steps to occur, they must use RAF twice (or equivalent queuing) to ensure they run in separate Event Loop cycles.

### VI. Task Queues and the Event Loop

The Event Loop mechanism is metaphorically based on **nepotism** (favoritism/discrimination). The JavaScript Runtime sets rules for which queue gets processed first.

**The Four Task Queues (By Priority Order):**

|Queue Type|Priority|Typical Tasks|
|:--|:--|:--|
|**Microtask**|Highest (1)|Promise callbacks (`.then()`, `.catch()`, `.finally()`), Mutation Observer|
|**Request Animation Frame**|High (2)|Callbacks from `requestAnimationFrame` method|
|**Rendering Pipeline**|Medium (3)|All DOM updates, CSS calculations, Layout calculations, Painting|
|**Macrotask**|Lowest (4)|`setTimeout`, `setInterval`, Event Listener callbacks (e.g., `document.addEventListener`)|

_Note on Rendering Pipeline:_ UI updates involve three steps in specific order: Style calculation, Layout calculation, and Painting.

**The Event Loop (The Function):**

- The Event Loop is **just a function** that runs infinitely.
- Its sole job is to check if the **Call Stack is empty**.
- If the Call Stack is empty, it pushes a task from the Task Queues into the Call Stack **based on priority order**.
- The Event Loop works in sync with the rendering pipeline and animation; if it is time to render, rendering happens; otherwise, tasks can run.

**Processing Rules (Discrimination):**

|Queue Type|Execution Rule|Effect|
|:--|:--|:--|
|**Microtask**|**Execute until the queue is empty**.|If a Microtask schedules another Microtask, the execution continues without interruption, potentially freezing the UI.|
|**Animation/Rendering**|All existing tasks are processed **when it's the right time for a UI update** (e.g., 16 ms frame interval). New tasks added during this execution run in the **next cycle**.|Execution of the batch happens until the queue is empty.|
|**Macrotask**|**One task at a time**.|After one task executes, the Event Loop checks all other queues again (Microtask, then RAF, etc.). This yields time for other operations, including UI updates.|

### VII. The Four Event Loop Mantras

These four points summarize the entire concept:

1. **JavaScript code runs in multiple cycles/iterations**.
2. The **Event Loop is just a function** whose job is to push tasks from Task Queues to the Call Stack whenever the Call Stack is empty.
3. **Task Queues work on priority:** Microtask has the highest, Macrotask has the lowest.
4. **How Queues are Processed:**
    - Microtasks: If present, **no other task can run** until the queue is empty.
    - Render/Animation Tasks: Execute until the queue is empty; newly added tasks run in the **next cycle**.
    - Macrotasks: **One task at a time**, then check for Micro or Render queues (in the next render cycle).

----------------------------------------------------------------------------------------------------------------------------------------------------

- #### Asynchronous JavaScript & EVENT LOOP from scratch 🔥
	- https://youtu.be/8zKuNo4ay8E?si=2psApjlvXzNn7kK8

The sources provide a comprehensive, detailed breakdown of how asynchronous JavaScript code is handled within the browser environment, focusing specifically on the **Call Stack, Web APIs, Event Loop, Callback Queue, and Micro Task Queue**. Understanding this topic is crucial, as many developers (up to 90%) often fail to grasp it.

Here is a detailed analysis of the components and execution process described in the sources:

### I. Core Components and Execution Flow

#### A. The JavaScript Engine and Call Stack

The JavaScript code is executed inside the JavaScript (JS) Engine, which is housed within a larger structure referred to as the "Big Grey Box," which is the Browser.

1. **Call Stack:** This is a single thread where all JavaScript code is executed.
2. **Global Execution Context (GEC):** When a JavaScript program starts, the Global Execution Context is created and pushed onto the Call Stack.
3. **Code Execution:** Code runs line by line within the GEC.
4. **Function Execution Context:** When a function is invoked, an Execution Context is created for that function and pushed onto the Call Stack. For example, when running a piece of code, function definitions are allocated memory, but function invocation creates the context.
5. **Completion:** Once a function finishes execution, its Execution Context is popped off the Call Stack.
6. **Synchronous Nature:** The JS code inside the Call Stack executes immediately and does **not wait** for external events like timers to expire. If the code takes a long time, it blocks the entire process.

#### B. The Browser and Superpowers (Web APIs)

The browser itself is highly powerful and is described as one of the "most remarkable creations in the history of mankind". It provides capabilities beyond the JS Engine. These capabilities are referred to as "Superpowers".

1. **Browser Capabilities:** These include Local Storage, timing functions (like timers), rendering the UI (DOM manipulation), managing URLs, and communicating with the external world (e.g., HTTP/HTTPS requests).
2. **Accessing Superpowers (Web APIs):** To access these external Superpowers, the JS engine needs a connection. The browser provides access to these powers through **Web APIs**.
    - Examples of Web APIs are `setTimeout`, `document.getElementById`, and `fetch`.
3. **Global Object/Window:** The browser gives access to all these Superpowers through a "window" or **Global Object**. Functions like `setTimeout` can be called as `window.setTimeout` or just `setTimeout`. `console.log` also uses a console API, which is accessible through the `window` object.

### II. Asynchronous Handling: Queues and the Event Loop

When asynchronous operations are registered via Web APIs (like `setTimeout` or event listeners), they are handled outside the Call Stack.

#### A. The Event Loop

The Event Loop is described as the "super hero". It has one primary job: continuously monitor the Call Stack and the queues (Callback Queue and Micro Task Queue).

1. **Function Transfer:** When the Event Loop detects that the Call Stack is empty, and there are functions lined up in a queue waiting for execution, it picks up a function from the queue and pushes it into the Call Stack for execution.

#### B. The Queues

The sources define two types of queues where callback functions wait to be pushed onto the Call Stack.

##### 1. Callback Queue (Macro Task Queue)

This queue holds functions that are ready to execute after an asynchronous Web API completes. It is also known as the Task Queue or Macro Task Queue.

- **Mechanism Example (`setTimeout`):**
    
    - When `setTimeout(callback, delay)` is called, the callback function is registered, and the timer starts running within the Web API environment of the browser.
    - Once the timer expires (e.g., 500 milliseconds), the callback function is moved into the **Callback Queue**.
    - The Event Loop then waits for the Call Stack to be empty before moving the callback from the Callback Queue to the Call Stack.
- **Mechanism Example (DOM Event Listener):**
    
    - An event listener (e.g., `document.addEventListener('click', callback)`) registers the callback function inside the Web API environment.
    - The callback waits for the associated event (e.g., a button click).
    - When the event occurs, the callback is pushed into the **Callback Queue**.
- **Items that use the Callback Queue:**
    
    - `setTimeout` callbacks.
    - DOM Event Listener callbacks (like click events).
    - Fetch callbacks.

##### 2. Micro Task Queue

This queue is conceptually like a "sibling" to the Callback Queue, but it holds a **higher priority**. It is also known as the Job Queue.

- **Priority Rule:** Whatever functions enter the Micro Task Queue will be executed first, before functions in the Callback Queue.
- **Execution Rule:** The Event Loop checks the Micro Task Queue after the Call Stack becomes empty. It must empty the _entire_ Micro Task Queue before it even begins to check the Callback Queue.
- **Items that use the Micro Task Queue:**
    - All callback functions that come through **Promises** (e.g., the code inside a `.then()` block).
    - Callbacks registered via the **Mutation Observer** (which checks for mutations in the DOM Tree).

### III. Potential Issues

#### Starvation

Starvation is a possibility where the Callback Queue is neglected because the Micro Task Queue constantly generates new micro tasks.

- If a Micro Task function creates another Micro Task, and this cycle continues, the functions waiting in the Callback Queue will **never get a chance to execute**, as the Event Loop prioritizes emptying the Micro Task Queue first.
- This means the Callback Queue can wait for a long time.
  
----------------------------------------------------------------------------------------------------------------------------------------------------

- ####
- 

----------------------------------------------------------------------------------------------------------------------------------------------------