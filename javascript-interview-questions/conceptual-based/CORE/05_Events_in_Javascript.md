

----------------------------------------------------------------------------------------------------------------------------------------------------
- ## Events in Javascript | Even and Event handler in Javascript
- https://youtu.be/CGjHpnm8TeE?si=Jngkp7NDNchuPBoC

This response details all concepts, implementations, definitions, and technical insights regarding JavaScript Events, Event Listeners, and Event Propagation found within the provided source materials.

---

## 1. Introduction to JavaScript Events

Events are a critically important topic in JavaScript. Mastering events is essential for building projects. The concepts are described as simple, but require diving into depth to gain complete clarity.

**Initial Scenario Example:** The goal is to click on an element displaying "Our Premium Courses" and have its text change to "Hello Coder Army". JavaScript needs a mechanism to detect that the click occurred and subsequently change the content.

## 2. Defining Events and the Three Event Handling Phases

An **Event** is defined as an action that occurs within the browser or on the webpage.

Events occur constantly on a page (e.g., mouse moving, clicking, key inputs). It is the developer's responsibility to choose which events to listen to and where.

The entire event handling process is generally broken down into three phases or concepts:

1. **Event:** The action itself (e.g., mouse movement, click, double click, scroll, keyboard input).
2. **Event Listener:** The mechanism used to listen for or listen to a specific event on a specific element. The listener determines if the specified action has happened on the targeted element.
3. **Event Action (Event Handler):** The behavior or code that is executed when the event listener hears the event (e.g., changing text content, changing styles).

### Examples of Event Types Demonstrated:

The source demonstrates that event listeners can be attached to various event types, including:

- **`click`** (single click).
- **`dblclick`** (double click).
- **`mouseenter`** (when the mouse enters the element).
- **`mouseleave`** (when the mouse leaves the element).
- Mouse movement or hovering.
- Scrolling or keyboard input.

---

## 3. Methods for Attaching Event Listeners

The source explores three methods for attaching event handlers, noting the disadvantages of the first two:

### Method 1: Inline Event Handler (Not Preferred)

This involves attaching the event handler directly in the HTML element using an attribute like `onclick`.

- _Example:_ `<H1 id="first" onclick="handleclick()">Hello Coder Army</H1>`.
- _Action:_ Calls a JavaScript function (`handleclick`) when the element is clicked.
- **Reason Not Preferred:** It involves writing JavaScript code directly inside the HTML structure.

### Method 2: Element Property Assignment (Not Preferred)

This involves selecting the element in JavaScript and assigning a function directly to the event property (e.g., `element.onclick`).

- _Example:_ `element.onclick = function() { element.textContent = 'Strike Is Coming' }`.
- **Reason Not Preferred:** Since `element.onclick` is a property on the element object, defining a new function for it will **overwrite** any previous function assigned to that property. This prevents attaching multiple actions to the same event type on that element.

### Method 3: `addEventListener` (The Preferred Method)

This is the most robust and preferred way to attach events.

- _Example:_ `element.addEventListener('click', callbackFunction)`.
- _Arguments:_ It takes the event type (e.g., `'click'`) and a callback function as arguments.
- **Key Advantage:** Since `addEventListener` is a **method** call on the object, you can call it multiple times, attaching multiple distinct event handlers to the same event type without overwriting previous ones. Both actions will execute.

---

## 4. Handling Multiple Elements and Optimization

### The Problem of Manual Iteration

When dealing with multiple similar elements (e.g., five child divs inside a parent), selecting and adding event listeners to each element manually (e.g., Child One, Child Two, etc.) is inefficient.

### Optimization 1: Using Loops

An improved approach is to select the parent, access its children using **`parent.children`** (which returns an HTML Collection), and then iterate through them using a `for...of` loop. An event listener is then attached to **each child** inside the loop.

- _Critique:_ Even using a loop, this approach still attaches an individual event listener to every single child element. If there are 100 children, 100 listeners are attached, which is not the most optimized approach.

### Optimization 2: Event Delegation via Bubbling (Best Approach)

The most optimized technique utilizes **Event Bubbling** combined with the Event Object (see Section 6).

The concept involves placing the event listener **only** on a higher-level ancestor (like the `parent` or `grandParent` div). This avoids needing multiple listeners on all the children.

---

## 5. Event Propagation: Bubbling and Capturing

Event propagation defines the order in which events are handled when nested elements are clicked.

When an inner element (the target) is clicked, the event traverses the DOM tree in three distinct phases:

### Phase 1: Capture Phase (Top-Down)

- The browser determines the element that was clicked (the target).
- The traversal starts from the top of the DOM (Window) and moves down toward the target element.
- _Typical Path:_ Window $\rightarrow$ Document $\rightarrow$ HTML $\rightarrow$ Body $\rightarrow$ Grand Parent $\rightarrow$ Parent $\rightarrow$ Child (Target).

### Phase 2: Target Phase

- The moment the event reaches the element that was directly clicked.

### Phase 3: Bubbling Phase (Bottom-Up)

- Propagation reverses and moves from the target element back up to the Window.

### Default Execution Order and Controlling Phases

1. **Default Behavior (Bubbling):** By default, event listeners are triggered during the **Bubbling Phase** (bottom-up). If an inner element is clicked, the event triggers its listener first, then its parent's, then the grand parent's, and so on.
    
    - _Example:_ Clicking Child outputs: Child $\rightarrow$ Parent $\rightarrow$ Grand Parent.
2. **Controlling the Phase:** The `addEventListener` method accepts a **third optional argument**. This argument determines whether the listener is active during the Capturing Phase.
    
    - If the third argument is **`false`** (default): The Capturing Phase is **off**, and the event listener is executed during the **Bubbling Phase**.
    - If the third argument is **`true`**: The Capturing Phase is **on**, and the event listener is executed during the **Capture Phase** (top-down traversal).
    - _Result of True:_ If set to true, clicking the Child would output: Grand Parent $\rightarrow$ Parent $\rightarrow$ Child.

### Stopping Propagation

The default bubbling behavior (the event propagating up to ancestors) can be stopped using a method on the Event Object: **`e.stopPropagation()`**. This ensures that once the event is handled by the target element, it does not proceed to trigger listeners on its parent elements.

---

## 6. The Event Object and `e.target`

The callback function provided to `addEventListener` automatically receives an **Event Object** (often named `e` or `event`). This object contains comprehensive information about the event that occurred.

### Key Information in the Event Object (`e`):

- **Type of Event:** Details the event that was triggered (e.g., 'click').
- **Coordinates:** Provides screen coordinates (`clientX`, `clientY`) indicating the exact position where the click happened.

### The `e.target` Property (Key to Delegation)

The `e.target` property within the Event Object is highly important. It specifically points to the **single, exact element** that initially triggered the event.

**Using `e.target` for Event Delegation:** By placing the event listener only on the `parent` element, `e.target` allows the parent's listener to identify _which_ specific child element was clicked. Once the target element is identified, its properties (like `textContent` or `style`) can be manipulated.

- This approach is beneficial because it requires **only one event listener** on the outer element, solving the optimization problem faced when using loops.

---

## 7. Removing Event Listeners

It is often necessary to **remove** event listeners, especially when they are no longer needed.

The method used is **`element.removeEventListener(type, handlerFunction)`**.

### Requirement for Successful Removal

For `removeEventListener` to work correctly, the reference to the callback function passed to `removeEventListener` **must be the exact same reference** that was originally passed to `addEventListener`.

- If an **anonymous function** (a function defined directly inside the `addEventListener` call) is used, removal will fail. This is because each anonymous function is treated as a separate object instance with different memory allocation, even if the code looks identical.
- **Solution:** Define the handler function separately (e.g., `function handleclick() { ... }`) and pass its reference to both `addEventListener` and `removeEventListener`. This ensures both methods point to the same memory location, allowing the listener to be successfully removed.

**Example:** A listener can be made to execute once and then remove itself by including `removeEventListener` inside its own handler function.

----------------------------------------------------------------------------------------------------------------------------------------------------
- ## Javascript Interview Questions ( Event Propagation ) - Bubbling, Capturing, and Deligation
- https://youtu.be/rS_4YfbEo2U?si=80HjjKBGofgf9Cym

This response draws exhaustively on the provided source material regarding JavaScript Event Propagation, ensuring all concepts, examples, and interview-related details are included and formatted for clarity and enhanced understanding.

---

## I. Introduction and Core Concepts

Events are a critically important part of JavaScript, required for actions like button presses, text inputs, and drag-and-drop actions. Developers must be very careful about where and when they place these events in their code. Sometimes events may not perform as expected, such as when triggering an event that was added to a parent element. This phenomenon is known as **event propagation**.

### What is Event Propagation?

Event propagation is the complete process of deciding **when and in which direction** the event will be executed. It is not a small concept and encompasses several behaviors.

**Illustrative Setup:** The examples in the source use a nested HTML structure: $$\text{Div} \longrightarrow \text{Form} \longrightarrow \text{Button}$$ If event listeners are placed on all three elements, clicking the button means clicking the form and the div as well. Event propagation addresses the sequence of event execution.

## II. Event Bubbling

Event bubbling is a mechanism where events are executed from **bottom up**. This analogy is based on how bubbles go from down to up.

- **Default Behavior:** Event bubbling is the **default behavior** when dealing with propagation.
- **Execution Sequence (Default):** When clicking the button in the nested structure, events fire in the order: **Button, Form, Div**.
- **Examples of Execution:**
    - Clicking the **Button** triggers: Button alert, then Form alert, then Div alert.
    - Clicking the **Form** triggers: Form event, then Div event (Button is skipped).
    - Clicking the **Div** triggers: Only the Div event.
- **Non-Bubbling Events:** There are specific events that do not bubble, such as `focus` and `blur`. Interviewers may ask candidates to name events that do not bubble.

## III. Event Capturing (or Trickling)

Event capturing is the reverse process of bubbling, causing events to execute from **top to bottom**. It is sometimes also known as **trickling**.

- **Execution Sequence:** When clicking the button, events fire in the order: **Div, Form, then Button**.
- **Achieving Capturing:** To enable capturing, a third argument must be passed to the `addEventListener` method: `capture: true`.
- **Implementation Note:** If `capture: true` is only set on the parent (e.g., the `div`), the div will execute capturing (top-down), but the subsequent nested elements will still follow the default bubbling process. To achieve full capturing (Div, Form, Button), `capture: true` must be added to the event listeners of all three elements (Div, Form, and Button).
- **Interview Relevance:** Event capturing/trickling is one of the most frequently asked interview questions in Junior as well as Senior JavaScript interviews.

## IV. Controlling Propagation: `stopPropagation`

A common interview question is how to stop event bubbling or capturing. This is useful if a developer only wants the clicked element's event to execute, preventing execution on parents.

- **Method:** Use `e.stopPropagation()` (where `e` is the event object) inside the callback function.
- **Example (Stopping Immediately):** If `e.stopPropagation()` is added to the button's event listener (during default bubbling), clicking the button triggers **only the button event**, and nothing else.
- **Example (Stopping Mid-Flow):** If the propagation is stopped at the form, clicking the button triggers **button, then form**, and then the propagation halts, preventing the div event from triggering.
- This method (`stop propagation`) can be used in both the bubbling and capturing processes.

## V. Key Event Terminologies (Target vs. CurrentTarget vs. This)

Interviewers frequently ask about the differences between `event.target`, `event.current Target`, and `this` when dealing with event propagation.

|Terminology|Description|Execution Behavior|
|:--|:--|:--|
|**`event.current Target`**|Points to the tag on which the current event listener is being executed.|**Bubbles** (or captures). When clicking Button, it successively alerts: `button`, then `form`, then `div`.|
|**`event.target`**|Points only to the **origin of the bubbling** (the element that was originally clicked).|Does **not** change during propagation. When clicking Button, it consistently alerts: `button`, `button`, then `button`. This is very helpful when handling bubbling.|
|**`this`** (`this.tag name`)|Points only to the function that it has been called on.|Works exactly like `event.current Target`. When clicking Button, it alerts: `button`, then `form`, then `div`.|

## VI. Event Delegation

Event delegation is cited as the **most asked question** among all event propagation topics in JavaScript interviews.

### Definition and Purpose

1. **Inefficiency Problem:** If a page has an unlimited list of products or similar elements, adding an individual event listener to _every single one_ of these descendant elements would burden the page with too many listeners.
2. **Delegation Solution:** Event delegation involves adding the event listener to the **parent element** instead of adding listeners to all descendant elements.
3. **Process:** The single parent listener then checks which specific descendant element was clicked (e.g., if mobile was clicked, route to the mobile page).

### Implementation Details

- The event listener is added to the parent container (e.g., a `products` div).
- To identify the specific child clicked, the `event.target` property is used, often checking the `tag name` or `class name`.
- **Example Logic:** A script may check: `if event.target.tag name is equal to span`. If true, an action is performed, such as setting the window location based on the element's class name (`event.target.class name`).
- **Handling Nested Elements (The `closest` method):** If the clicked element is nested within the intended target (e.g., clicking a `<b>` tag inside a `<span>`), the `event.target.tag name` might not be the desired tag (`span`).
    - **Solution:** Use `event.target.closest('span')`. This checks if the clicked element has a closed node with the target tag (`span`) and returns that node, allowing the necessary action to be performed.

**Benefit:** Using good practices like event delegation is highly appreciated by interviewers.

## VII. Advanced Interview Scenarios and Output Questions

Interviewers can ask tricky output-based questions or component creation tasks that test understanding of event propagation principles.

### 1. Mixed Propagation Output Question

**Scenario:** Given the default bubbling setup (Div -> Form -> Button), how can you achieve the execution sequence: **Form, then Button, then Div** when the button is clicked?.

**Solution:** This requires enabling capturing only on the Form element.

1. Set `capture: true` _only_ on the Form's event listener.
2. **Flow Analysis:**
    - Click Button.
    - The event travels down. The Form listener executes capturing (top-down approach) $\rightarrow$ **Form event executes**.
    - The event continues down to the Button, and then the default bubbling (bottom-up) takes over.
    - The **Button event executes**.
    - The event bubbles up to the Div $\rightarrow$ **Div event executes**.
    - Resulting sequence: Form, Button, Div.

### 2. Creating a Modal that Closes on Negative Space Click

This scenario uses event delegation/propagation to ensure the modal closes only when clicking outside the content.

**Requirement:** The modal should close when clicking the negative space (the container), but **not** when clicking on the modal content itself.

**Initial Problem:** If a click event listener is added to the container to close the modal, clicking the internal modal content also closes it because the event bubbles up to the container.

**Solution using `event.target.class name`:**

1. The listener is added to the outer container (`modal container` class).
2. When a click occurs, identify the element that was _originally_ clicked using `e.target.class name`.
    - If the user clicks outside (negative space), `e.target.class name` is `'modal container'`.
    - If the user clicks inside the modal content, `e.target.class name` is `'model'`.
3. The logic is implemented to only execute the closing function (`toggleModel(false)`) **IF** `e.target.class name` is strictly equal to `'modal container'`.

This successfully prevents closure when clicking inside the model content. (A similar concept applies to creating a navigation bar).

----------------------------------------------------------------------------------------------------------------------------------------------------

- ## Events in Javascript | chai aur javascript
- https://youtu.be/_ALUMTa8BAE?si=0LflxePiHxIGA42u

This response draws exhaustively from the provided transcript to detail the discussion on JavaScript Events, focusing on structure, approaches, the Event Object, and propagation mechanisms.

### I. Series Context, Goals, and Setup

The video is a continuation of the JavaScript journey within the "Chai aur Code" series.

#### A. Video and Series Goals

- The video was recorded because the speaker found some free time after lunch, following a period of high pressure due to exams and job responsibilities, including live classes.
- The speaker emphasizes that the job must be done ("jab toh karni padegi") in order to bring videos to YouTube.
- This specific series is considered exceptional and requires more time because the goal is to make it **rock solid for the next 4, 5, or 6 years**.
- The aim is to teach JavaScript from scratch in a **professional way**, as it is used in production environments, enabling viewers to **crack all interviews** and never need to look up JavaScript elsewhere.
- The speaker is taking time, explaining every concept thoroughly, and sometimes re-recording and deleting videos.
- The discussion on Events will be detailed and taught in a **project style**, which is considered the best method for learning events.
- The series previously covered four projects related to **DOM manipulation**, including creating and removing elements.
- The speaker notes the channel currently has a small audience (20–25,000 people) and asks for support to quickly reach 100,000 subscribers.

#### B. Development Environment and HTML Structure

- The work is being done in **VS Code**.
- A new folder named `08 Events` was created.
- A file named `one.html` was created for the lesson.
- The basic document is titled "HTML ke Events".
- The HTML structure includes basic elements:
    - An `<h2>` tag containing "Amazing Images".
    - A `<div>` that holds an Unordered List (`<ul>`).
    - The `<ul>` contains multiple List Items (`<li>`).
    - Each `<li>` contains an Image tag (`<img>`).
    - Images were sourced from **Pexels**, where the speaker uploads photos from their travels.
    - Images have an `alt` tag and an **ID**.
    - Specific IDs mentioned: `photoshop` (also in the first image's `alt` tag), `japan`, `river`, `all`, and `prayer`.
    - The final list item contains an Anchor Tag (`<a>`) for a link to Google.

#### C. Styling (Basic CSS)

- The focus is not on CSS, but basic styling was applied for visual comfort:
    - `body` background color: **`414141`** (darkish).
    - `body` text color: **`aliceblue`**.
    - The link tag color was changed to `aliceblue` so it would be visible.

#### D. JavaScript Execution Flow

- The JavaScript code is placed inside a `<script>` tag after the `<body>`.
- **CoPilot** is disabled to avoid excessive suggestions in a beginner class.
- JavaScript is generally a **sequentially run language**.
- **Browser Events are an exception** to sequential execution.
- Events are invoked by an **activity**, such as:
    - Mouse movement.
    - Keyboard press or release.
    - Mouse press or removal.
    - Drag-and-drop actions.

---

### II. Approaches to Handling Events

The source details three main approaches to implementing event listeners, starting with the least recommended and moving to the best practice.

#### A. Approach 1: Inline HTML Injection (Bad Practice)

- The event handler (e.g., `onclick`) is written directly inside the HTML tag.
- Example: `<img onclick="alert('auww')">`.
- **Critique:** While the code works, it is **not a good approach**. It is not a feasible approach when the application needs to scale, and this practice should generally be avoided. (The speaker notes React handles this differently, but for vanilla JS, mixing knowledge here can cause confusion).

#### B. Approach 2: Using the `on[Event]` Property in JavaScript

- The element is selected (e.g., using `document.getElementById`).
- The event is attached directly as a property, like `.onclick`, and assigned a function.
- Example: `document.getElementById('all').onclick = function() { alert('All clicked') }`.
- **Critique:** This approach **looks good but has problems**. It does not provide enough information and **lacks features** such as propagation ability, which are necessary for modern development.

#### C. Approach 3: Using `addEventListener` (Best Practice)

- This is the **third and best approach** currently used in the market.
- It is described as **very interesting and powerful**.
- It allows listening to various events, including keyboard events, mouse events, and drag events (useful for projects like a Trello clone).
- It is frequently asked about in interviews.
- The method takes three parameters:
    1. The Event Name (must be written as a **string**, e.g., `'click'`).
    2. The Function (callback).
    3. A Third Parameter (Boolean, defaults to `false`).

#### D. Historical/Alternative Methods

- **`attachEvent`:** This method was used in early times when there were significant challenges running applications on **Internet Explorer**.
- **jQuery:** This historical framework (once as popular as React is now) had a direct `.on` event listener.

---

### III. The Event Object and its Properties

When working with event listeners, the callback function receives the **Event Object**. Understanding this object in detail is highly beneficial.

#### A. Core Event Object Properties

The event object is a detailed JavaScript object that contains many values:

- **`type`**: Used to identify the type of event (e.g., keyboard type, mouse type).
- **`timeStamp`**: Crucial for tracking when an event occurred, which is relevant in interview questions.
- **`bubbles`**.
- **`buttons`, `cancelButton`**.
- **`view`**: Can provide details like the window height and width at the time of the click.
- **`defaultPrevented`**: Indicates if the default behavior was prevented (an example is covered later).
- **`target`**: The specific element on which the event originated.
- **`sourceElement`**: Highly useful and heavily used in examples.
- **`toElement`**.
- **`currentTarget`**.
- **Event Types:** Events are mostly related to the browser or the environment (e.g., mouse position).

#### B. Interview-Relevant Properties (Position and Key Detection)

Interviewers often ask questions requiring knowledge of position or special keys:

- **Client Position Related:**
    - `clientX`, `clientY` (Client X/Y position).
    - `offsetX`, `offsetY` (Offset values).
    - `screenX`, `screenY` (Screen X/Y values).
    - `tiltX`, `tiltY` (Position related).
    - _Example Interview Task:_ Create a circle at the exact location where the user clicks (solved using X/Y position data).
- **Key Detection:**
    - `altKey`, `ctrlKey`, `shiftKey`: Direct access to check if these special keyboard keys were pressed during the event.
    - `code`: Used to identify the keyboard code of the pressed key. This foundation can be used for projects like testing keyboard typing speed.

---

### IV. Event Propagation: Bubbling and Capturing

Event propagation relates to the third parameter of `addEventListener` (which defaults to `false`).

#### A. Contexts of Propagation

There are two main contexts for event propagation:

1. **Event Bubbling:** This is the default mode (`false` or omitted).
    - The event flows from the **inner element to the outer element** (bottom-up).
    - The name comes from the idea of a **bubble** rising.
    - _Example:_ If an image inside an `<li>` inside a `<ul>` is clicked, the image event fires first, followed by the `<li>`, and then the `<ul>` event.
2. **Event Capturing:** This occurs when the third parameter is set to `true`.
    - The event flows from the **top element down to the bottom/inner element**.
    - _Example:_ The `<ul>` event is captured first, followed by the specific element clicked.

- Neither capturing nor bubbling is strictly right or wrong; the choice depends entirely on the specific use case.

#### B. Controlling Propagation

- **Stopping Propagation:** Sometimes, bubbling must be stopped so that the event does not pass up to outer elements (especially in frameworks like React where the top element might have its own tracking script).
    - The method used is **`event.stopPropagation()`**.
    - Executing this stops the event from bubbling up to parent elements.

---

### V. Preventing Default Behavior

Another crucial method is stopping the built-in action of an element.

- **Method:** **`event.preventDefault()`**.
    - _Note:_ The correct method name is `preventDefault()`, not `defaultPrevented`.
- This method allows you to change the **default behavior** of any tag.
- **Use Cases:**
    - Stopping an anchor tag (`<a>`) from navigating upon click.
    - Stopping a form from submitting upon clicking the submit button.
- **Example Implementation:** The speaker tracks the Google link element (ID: `google`) and uses `event.preventDefault()` to stop the browser from navigating to the Google website when clicked.
- This method can be combined with `event.stopPropagation()` to prevent both the default action and the bubbling up of the event.

---

### VI. Project Example: Event Delegation and Element Removal

The final section demonstrates using event knowledge to solve a real-world problem—removing an image on click.

#### A. Delegation Strategy

- **Goal:** Click an image within the list and make it disappear.
- **Inefficient Approach:** Giving IDs and event listeners to every single image (especially if there are hundreds).
- **Better Approach (Event Delegation):** Target a common ancestor element, in this case, the **`<ul>` with the ID `images`**.
- The `addEventListener` is attached to the parent `<ul>`. This allows the listener to capture all clicks occurring within the list.

#### B. Identifying and Removing the Element

1. **Identifying the Target:** Use **`event.target`** to determine the specific element that was clicked.
2. **Identifying the Element to Remove:** The goal is to remove the entire List Item (`<li>`), not just the image, to prevent the list bullet point from remaining.
    - The parent node of the image is the `<li>`, accessed via **`event.target.parentNode`**.
3. **Removal Methods:**
    - **Method 1 (Modern/Simple):** Using the `.remove()` method directly on the parent node: `removeIt.remove()`.
    - **Method 2 (Alternative/Older):** Using the parent's `removeChild` method: `removeIt.parentNode.removeChild(removeIt)`. This is slightly more confusing as it requires moving up two levels to remove the child.

#### C. Handling Spillover (Strict Checks)

- **Problem:** If the user clicks on the List Item (`<li>`) itself (instead of the image), `event.target.parentNode` points to the `<ul>`, causing the entire `<ul>` to disappear (spillover effect).
- **Solution (If Statement/Strict Check):** Implement a check to ensure the clicked target is specifically an image.
    - Use the property **`event.target.tagName`**.
    - The tag name is returned in **uppercase** (e.g., `IMG`).
    - The check: `if (event.target.tagName === 'IMG') { // Execute removal code }`.
- This ensures that clicking the `<li>`, or the Google link, does not trigger the removal functionality.

----------------------------------------------------------------------------------------------------------------------------------------------------

- ## Event Listeners Explained in Depth | The Complete JavaScript Course | Ep.61
- https://youtu.be/5mo0xQu4FOM?si=dYfDE0PV-oSW_pLM
  
This response details all information about events and event listeners provided in the source transcript, organized for comprehensive understanding.

---

### I. Introduction to Events and Event Listeners

Events in JavaScript allow a particular piece of code to run on a web page. We can use events to perform a task based on user interactions.

**Examples of Events:**

- User clicks on a button.
- User drags something.
- User hovers over an element.
- Double-clicking.
- Inputting.
- Pressing a key.

**Event Listeners:**

- An event listener can be placed on a particular element.
- When the event happens (e.g., a click), we know it occurred, and then we can run any associated code.
- Event listeners are a very interesting concept, and further detailed explanation, including passing parameters to get extra information (like coordinates of where the click happened), will be covered in future videos.
- Learning event listeners unlocks endless possibilities for making a web page interactive.

### II. Event Listener Implementation Methods

The source details three ways to add an event listener, noting that the third method is the ultimate and recommended approach.

#### Method 1: Using HTML Attributes (e.g., `onclick`)

This is the most basic form of adding an event listener.

|Feature|Details|Source|
|:--|:--|:--|
|**Syntax**|Use attributes starting with `on` (e.g., `onclick`, `onblur`, `onchange`, `ondblclick`) directly in the HTML element.||
|**Value (Inline Code)**|To use JavaScript code like `console.log` as the attribute value, **single quotes or backticks must be used** inside the double quotes enclosing the attribute value to avoid structural problems.||
|**Value (Function)**|A JavaScript function (e.g., `sayHi`) defined elsewhere can be called: `onclick="sayHi()"`.||
|**Behind the Scenes**|Whether using inline code or a function call, the browser **creates an anonymous function** (e.g., `function on click`) behind the scenes and puts the provided code/function call inside it.||
|**Dev Tool Observation**|The Event Listeners tab shows the event (e.g., `click` event on H1). The Properties tab shows that the `onclick` property of the element is set to a created function (not null).||
|**Removing Event**|To correctly remove the event listener, the attribute must be removed from the HTML code. Removing it through Dev Tools (Event Listener tab) is temporary and requires a page reload to fully reflect the removal if it was added via HTML.||
|**Limitation: Overwriting**|Only **one** function can be assigned to the attribute property. If a second function is assigned (`ondblclick`), it overwrites the first one.||
|**Drawbacks**|This method requires writing JavaScript inside HTML, which is considered "janky". It also has limitations, such as not allowing control over options like triggering the event only once (which is possible with Method 3).||
|**Context**|This method is not considered the best; Angular developers sometimes use a similar syntax, although Angular itself uses Method 3 behind the scenes.||

#### Method 2: Setting the `.onclick` Property in JavaScript

This method sets the event listener directly on the element's property using JavaScript.

|Feature|Details|Source|
|:--|:--|:--|
|**Process**|Select the element (e.g., `const H1 = document.querySelector('H1')`) and assign a function to its property (e.g., `H1.onclick = sayHi`).||
|**Requirement**|The property assignment requires a function. If a function name is provided, the browser does not need to create one itself.||
|**Function Definition**|Showing the function definition (in Dev Tools) will take the user directly to the JavaScript file where the function is defined.||
|**Major Limitation**|This method can only add **one** event listener to an element. Assigning a second function (e.g., `H1.onclick = secondSayHi`) will **overwrite** and remove the first listener.||
|**Status**|This is the second method, but it is **not the ultimate way**.||

#### Method 3: Using `addEventListener`

This is the recommended, ultimate, and best method, also recommended by the MDN website.

|Feature|Details|Source|
|:--|:--|:--|
|**Syntax**|Use the `addEventListener` method on the element: `element.addEventListener('event_type', function)`. The event type (e.g., `'click'`) is passed as a string.||
|**Mechanism**|It does **not** set the function in the `.onClick` property; it uses a different mechanism to add the listener. The `.onClick` property will remain `null` when this method is used.||
|**Major Benefit: Multiple Listeners**|This method allows adding **multiple event listeners** of the same type to the same element (e.g., two different functions can be called on a single click). Both listeners will be visible in the Event Listeners tab.||
|**Additional Benefits**|This method offers more control, such as the ability to specify that the functionality should run only once. Other benefits exist and will be covered in future videos.||
|**Function**|An existing defined function (e.g., `sayHi`) or an inline function (like an arrow function) can be passed as the second argument.||

### III. Mini-Project Implementation: Adding Cards

The source demonstrates Method 3 by creating a dynamic "Add Card" feature.

#### Project Setup and Styling (The Card Element)

1. **Element Selection:** The first `.card` element is selected using `document.querySelector('.card')`. This is done because `querySelector` returns the first element matching the selector.
2. **Cursor Styling:** The card is made clickable by changing the cursor to a pointer via CSS (`cursor: pointer`).
3. **Visual Modifications:** The element is styled to look like an "Add Card" button (a plus icon).
    - Specific CSS applied: `Cadet Blue` background color, `black` text (which automatically turns white in dark mode), `absolute` position (`bottom: 0`, `right: 0`), `100%` border radius (to make it a circle), and height/width set to `32px`.
    - A `title` attribute "add new card" is added to display a tooltip on hover.

#### Adding Functionality (Creating New Elements)

An `addEventListener` is added to the selected card element (the plus icon) for the `'click'` event, using an anonymous arrow function.

The logic inside the event listener performs the following steps:

1. **Initialization:** A counter variable (`let count = 1`) is created outside the listener function.
2. **Element Creation:** A new `div` element is created: `const newCard = document.createElement('div')`.
3. **Styling Application:** The essential class (`card`) is added to the new element so it inherits styling (height, width, background color, display flags) from the CSS: `newCard.classList.add('card')`.
4. **Content and Counting:** The current `count` value is assigned to the card's inner text, and the count is immediately incremented using the post-increment operator (`newCard.innerText = count++`).
    - _Note on Post-Increment:_ When `count++` is used in the assignment, the original value of `count` is assigned (e.g., 1), and _then_ the `count` variable is increased (e.g., to 2). Placing the increment operator ahead (`++count`) would cause it to assign the increased value (starting at 2).
5. **Appending:** The new card element is appended to the main `container`: `container.append(newCard)`.

When subsequent cards are added, they do not have event listeners attached, as the listener was only placed on the initial plus card.

#### Alternative Approach: Cloning (Drawbacks)

Using `card.cloneNode` to create a new card element was attempted.

- **Problem:** Cloning copies all attributes and classes from the original card. Since the original card had special styling to make it a plus button (e.g., absolute positioning, border-radius, potentially a class like `addCard`), the cloned card inherited this styling.
- **Consequence:** The new card overlapped the original plus button, preventing further clicks because the event listener was obscured.
- **Resolution:** To fix this, the extra styling class would have to be explicitly removed from the cloned element.
- **Conclusion:** Creating a new element (`createElement`) is generally better than cloning in this scenario to avoid complications related to class management.

### IV. Conclusion and Next Steps

The video introduces events and details three methods for adding event listeners, highlighting `addEventListener` as the superior method due to its flexibility (e.g., allowing multiple listeners).

The current demonstration acts as a "mini project". Future videos will cover more events (like mouse events) and further features of the event listener.

For questions or errors, users are directed to the comment section, a Telegram group (for big errors/screenshots), or live Google Meet sessions every Sunday at 8 pm.

----------------------------------------------------------------------------------------------------------------------------------------------------

- ## Form Event and Event Object in JavaScript | The Complete JavaScript Course | Ep.62
- https://youtu.be/J5-yOKK--78?si=JUroRnX3ZtYTSlKa
  
This response draws comprehensively on the provided YouTube video transcript excerpts to detail all mentioned concepts regarding form events and the event object in JavaScript.

## 1. Introduction to Events and Setup

The video aims to explain **form events** and the **event object** in JavaScript.

**Initial Setup Details:**

- The project involves a small setup with HTML and minimal JavaScript.
- The presenter intentionally **removed dark mode** because the outline/focus appearance of the input element looked "weird" with dark mode enabled.
- The primary elements discussed initially are an input element and a submit button.

**Selecting the Input Element:**

- The input element is selected using `document.querySelector`.
- Although initially only one input exists, selection by **ID** (e.g., `userNameInput`) is suggested as the better practice, especially since a second input (email) is planned later.
- Code used for selection: `const input = document.querySelector('input')` (initially) or `document.querySelector('#userNameInput')` (preferred ID selection).

## 2. Basic Input-Related Events

Before introducing new form-specific events, the video reviews two commonly known events used on the input:

|Event|Description|Behavior|
|:--|:--|:--|
|**Click Event**|Fired when clicking anywhere on the input element, including the border.|Mainly put on buttons or elements like a hamburger menu.|
|**Double Click (DBL Click) Event**|Fired when double-clicking the input.|When a double-click occurs, the **click event fires twice**, and the double-click event fires once.|

## 3. Core Input and Focus Events

The video introduces specific events commonly used on input fields:

### A. Input Event

- The `input` event can be put on an input element.
- **Behavior:** The input event is **not** fired by clicking or double-clicking. It fires only **when something is typed** into the input.
- **Use Case:** Often used when typing (behind the scenes) to keep updating a JavaScript variable.

### B. Change Event

- **Behavior:** The `change` event is similar to the input event but fires only when two conditions are met: 1) the value inside the input is changed, AND 2) the user **exits** the input (by clicking anywhere outside).
- **Condition for Firing:** If the user enters a value, exits, re-enters, and exits again without changing the value, the change event will **not** fire. It fires only when the value is changed _and_ the element is blurred.
- **Use Case:** Often used in projects to perform validation (e.g., checking if an email is valid) when the user exits the input field.

### C. Focus and Blur Events

These events relate to whether the input is active:

- **Focus Event:** Fires when the user clicks **inside** the input element, signifying the input is "in focus".
- **Blur Event:** Is the opposite of the focus event. It fires when the user clicks **outside** the input element, signifying the input "gets blurred".
- The blur event is related to the focus event, which can be observed in the object's properties or type.

## 4. The Event Object

When any event is fired, an **event object** is passed to the event listener function.

|Detail|Description|Citation|
|:--|:--|:--|
|**Parameter**|The function passed to `addEventListener` accepts a parameter, which is this event object.||
|**Naming**|This object can be given **any name** (like `event`, `e`, or `evt`), though `e` is the most common variable name used.||
|**Purpose**|The event object contains many properties and details about the event that occurred.||

### Accessing Values and Targets

The event object allows developers to access data related to the element that triggered the event:

1. **`e.Target`**: This property identifies the element **on which the event happened**.
2. **`e.Target.Value`**: This property allows access to the current value typed into the input field.
3. **Utilizing the Value**: The retrieved value can be used to update other elements (e.g., setting the `innerText` of a paragraph tag) or storing it in a variable (e.g., `let inputValue`).

### Event Target vs. Current Target

When an event listener is attached to a parent element (like a form) and an event is triggered on a child element (like an input), two properties describe where the event occurred:

- **`event.target`**: Keeps changing based on the specific element that was clicked or interacted with (where the event **started**).
- **`event.currentTarget`**: Does **not** change and always points to the element **on which the event listener was originally attached** (e.g., the form).

### Event Types

- Different events have different types.
- The property `event.type` (or `e.type`) can be used to specifically print the event type, such as 'focus', 'blur', 'input', or 'submit'.
- The name visible outside the object may represent the whole concept (e.g., the blur event often appears related to 'focus'); the actual type is seen in the `type` property. This behavior is related to the **prototype concept**, which will be detailed in future videos.

## 5. Form Element and Default Behavior

### Default Form Submission

- An input element is a component of a form, though it can exist outside a form.
- When a button (default type is **submit**) and inputs are enclosed within a `<form>` tag:
    - Clicking the button causes the page to **reload**.
    - This default behavior is similar to an anchor tag, redirecting to another page defined by the `action` attribute (e.g., `/search`).
- If the button is placed **outside** the form, the default submission behavior does not occur.
- **Submitting via Enter Key:** The form can be submitted by pressing the **Enter** key while focused on an input, but only if a button is present inside the form.

### Dynamic URL Creation (Query String)

The default form behavior automatically generates a URL structure called a query string:

1. It appends a **question mark** to the action URL.
2. It uses the **`name` attribute** of the input element to create key-value pairs.
3. The structure is `name=value` (e.g., `userName=Anurag`).
4. **Character Encoding:** If the input value contains characters that cannot appear directly in a URL (like `@`), the browser replaces them (e.g., `@` is replaced with `%40`).

### The Submit Event

- When a form is submitted (by clicking a submit button or pressing Enter), it fires a **submit event**.
- The submit event fires on the **form element**, not the button or inputs.
- **Other Button Types:** A button inside a form can also have `type="reset"`, which clears all input values instead of submitting the form.

## 6. Controlling Default Behavior

### Preventing Page Reload

The default submission behavior (page reload) must often be stopped in JavaScript applications:

- The event object provides a method called **`event.preventDefault()`**.
- Calling this method stops the form's default behavior (reloading/submitting) while still allowing the `submit` event to fire and be processed by the JavaScript listener.

### Debugging Default Behavior (Preserve Log)

When testing default form submission:

- Because the page reloads, the console clears.
- The browser has a **Preserve Log** option that prevents the console printouts from clearing upon reload.
- **Limitation:** Even with Preserve Log enabled, if the page navigates to another URL, the event object and related memory are lost, making it impossible to inspect the printed object details.

## 7. Extracting Form Data (Advanced Concept)

The video briefly touches upon extracting all form data easily, noting this is a more complex topic:

- The form contains information related to the inputs.
- A constructor method called **`FormData`** exists (it is a **global method**, not a property of the form element).
- Usage requires the `new` keyword: `new FormData(formElement)`.
- This method returns an object that can be iterated upon (e.g., using `entries`) to extract all form key-value pairs (based on the input `name` attributes and their values).
- This extracted data is typically stored in an object and used for sending to a database or API. This concept is explicitly noted as confusing and something that will be studied in coming videos.

----------------------------------------------------------------------------------------------------------------------------------------------------