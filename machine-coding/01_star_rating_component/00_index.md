






---

[Nikhil Jha on LinkedIn: #webdevelopment #javascript #reactjs](https://www.linkedin.com/posts/nikhiljha01_webdevelopment-javascript-reactjs-activity-7073305313654816770-g2TE?utm_source=share&utm_medium=member_desktop)

𝐏𝐫𝐨𝐛𝐥𝐞𝐦 𝐒𝐭𝐚𝐭𝐞𝐦𝐞𝐧𝐭 :

1️⃣ Create a star rating component as shown in image.

2️⃣ Rating should change on user click .

3️⃣ Change the colour of the star on hover temporarily.

4️⃣ Number of stars provided to the user must be dynamic .

🔥 𝐁𝐨𝐧𝐮𝐬 / 𝐀𝐝𝐝 𝐨𝐧 : Try to provide customisable styles .

Time : 45 mins to come up with a working solution

---

---

# Frontend Machine Coding Interview Guide: Star Rating Component

I'll provide you with a complete walkthrough for conducting this frontend machine coding interview about building a star rating component, without including any code solutions.

## Pre-Interview Assessment (5 minutes)

Start by determining the candidate's experience level with these questions:

1. "How many years of experience do you have with frontend development?"
2. "Which frontend technologies are you most comfortable with? Vanilla JavaScript, React, Vue, or something else?"
3. "Have you created any custom UI components from scratch before?"

This will help you calibrate your expectations and adjust your evaluation criteria accordingly.

## Interview Introduction (5 minutes)

"Today, we'll be doing a machine coding exercise where you'll build a star rating component. You'll have 45 minutes to complete it. I'll be evaluating:

- Your approach to component design
- Event handling techniques
- State management
- CSS styling capabilities
- Code organization and readability

Feel free to ask clarifying questions at any time. You can use any JavaScript framework or library you're comfortable with, or plain JavaScript if you prefer."

## Problem Statement with Visual Explanation

"You will be building a star rating component that looks like this:"

_[Reference the Star Rating Component Visual artifact]_

"The component should have the following functionality:

1. Display a series of stars (default unselected state)
2. Allow users to click on a star to select a rating
3. On hover, temporarily change the color of the star (and all stars before it)
4. The number of stars should be configurable (passed as a parameter)
5. Bonus/Add-on: Make the component's styles customizable

The component should handle three states as shown in the visual:

- Default state: Unselected stars (gray)
- Hover state: Temporarily highlighted stars (yellow)
- Selected state: Permanently selected stars (orange)"

## Clarification Questions

Address these points proactively or when the candidate asks:

For functionality requirements:

- "When a user hovers over a star, all stars up to and including the hovered star should be highlighted"
- "When a user clicks a star, that rating should be saved (all stars up to and including the clicked star remain highlighted)"
- "If a user hovers over a rating higher than the selected rating, only show the hover state up to the hovered star"
- "If a user hovers over a rating lower than the selected rating, temporarily show the hover state only up to the hovered star"

For technical requirements:

- "The component should be reusable - potentially multiple instances on the same page"
- "The component should accept a maximum rating parameter (e.g., 5 stars, 10 stars)"
- "For the bonus challenge, the component should accept custom styling options (like star colors, sizes)"

## Starting the Exercise (45 minutes)

"You can now start coding. Feel free to think aloud so I can understand your approach. You'll have 45 minutes to complete this task."

## What to Expect/Look For During the Exercise

### For Freshers:

- **Basic DOM manipulation:** Can they create the star elements dynamically?
- **Event handling:** Can they implement hover and click events correctly?
- **State tracking:** How do they keep track of the current rating?
- **Basic styling:** Can they style the stars according to different states?

### For Experienced Developers:

- **Component design:** How well-structured and reusable is their component?
- **State management:** Is their approach to managing state clean and efficient?
- **Event handling efficiency:** Do they use event delegation or attach individual handlers?
- **CSS techniques:** How sophisticated is their styling approach?
- **Extensibility:** How well do they implement the customization bonus challenge?

## Checkpoints to Assess During Development

At 15 minutes:

- Basic structure of stars should be rendered
- Starting to implement event handlers

At 30 minutes:

- Click and hover functionality should be working
- Dynamic star count should be implemented

At 45 minutes:

- Full functionality should be working
- Potentially working on the bonus customization feature

## Areas to Ask Questions During Development

When they implement the star generation:

- "Can you explain your approach to generating the star elements dynamically?"

When they implement the hover functionality:

- "How are you handling the hover state for stars before the hovered star?"

When they implement the click functionality:

- "How are you managing the selected state after a user clicks?"

## Post-Coding Discussion (10-15 minutes)

Ask the candidate to explain their solution:

- "Can you walk me through your implementation and key design decisions?"
- "What challenges did you face and how did you overcome them?"
- "If you had more time, how would you enhance this component?"

Ask targeted follow-up questions:

- "How would you implement half-star ratings?"
- "How would you handle accessibility concerns for this component?"
- "How would you modify this component to support read-only mode?"
- "What if you needed to allow users to reset their rating? How would you implement that?"

## Evaluation Criteria

### For Freshers:

- Can they implement the basic star rendering?
- Do they correctly handle hover and click states?
- Can they dynamically generate the requested number of stars?
- Is their code organized and readable?

### For Experienced Developers:

All of the above, plus:

- Component architecture and reusability
- State management approach
- Event handling efficiency
- CSS methodology and organization
- Implementation of the customization bonus
- Consideration of edge cases

## Feedback Framework

End with constructive feedback structured like this:

1. **Strengths:**
    - Note specific aspects they handled well (e.g., "Your component structure was clean and well-organized")
    - Highlight any particularly elegant solutions they came up with
2. **Areas for Improvement:**
    - Suggest alternative approaches that might be more efficient
    - Point out any missed edge cases or requirements
3. **Overall Assessment:**
    - Provide a balanced summary of their performance

For example: "I was impressed with how you implemented the hover state logic and your clean approach to generating stars dynamically. For improvement, consider how you might handle accessibility better and optimize the event listeners. Overall, you demonstrated solid component development skills."

## Common Edge Cases to Watch For

Pay attention to whether the candidate handles these situations:

1. What happens when the user hovers away without selecting?
2. Is the component reusable (can multiple instances exist on a page)?
3. Does it handle the parameter for number of stars correctly?
4. Is there any error handling for invalid inputs?
5. How does the component behave when the window is resized?

## Additional Challenges for Strong Candidates

If a candidate finishes early, you might suggest these extensions:

1. "Can you implement half-star ratings?"
2. "Can you add an animation when the rating changes?"
3. "Can you add an 'on rating change' callback function parameter?"
4. "How would you implement a 'reset rating' feature?"

These additional challenges can help you distinguish between good and exceptional candidates.

---

[https://youtu.be/DCkqIRe3w4A?si=_nYzw4OEwcJB_NIA](https://youtu.be/DCkqIRe3w4A?si=_nYzw4OEwcJB_NIA)

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=IBm1vsK0vXE&list=PL2M5yZr78G0rkhHnEhH7kQuhJ8akiLOnT&index=7](https://www.youtube.com/watch?v=IBm1vsK0vXE&list=PL2M5yZr78G0rkhHnEhH7kQuhJ8akiLOnT&index=7)

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=_gToDN-aoyI](https://www.youtube.com/watch?v=_gToDN-aoyI)

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=WOKTZUZ74Uc](https://www.youtube.com/watch?v=WOKTZUZ74Uc)

---

XXX

XXX

XXX

---

---

---

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=dsRJTxieD4U](https://www.youtube.com/watch?v=dsRJTxieD4U)

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=9GqhvxHNFag](https://www.youtube.com/watch?v=9GqhvxHNFag)

---

XXX

XXX

XXX

---

---

---

[https://www.youtube.com/watch?v=yAMsX-JFqrY](https://www.youtube.com/watch?v=yAMsX-JFqrY)



---

XXX

XXX

XXX

---

---

---

[Star Rating in ReactJS (Myntra, Swiggy) Frontend Machine Coding Interview #reactjs](https://youtu.be/3woZSW_ciHg?si=5Dp8s_p7UAn0tFZq)

- XXX
- XXX

---

---

[React Star Rating | React Interview Questions | Machine Coding Round](https://youtu.be/88NsoYaGvJk?si=r7_mr6zfg3f0aFqv)

- XXX
- XXX

---

---

[🚀Star Rating Component- React JS Interview Challenge #11, Machine Coding Round #javascript #react](https://youtu.be/St1NZEXzD6U?si=fM95ven-WZJoRKVA)

- XXX
- XXX

---