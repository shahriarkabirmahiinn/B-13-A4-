1. What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?

Ans: These are all methods used to select elements from the DOM, but they differ in what they look for, what they return, and how flexible they are.

getElementById('myId'):
Target  - Selects a single element based on its unique id attribute.
Returns - A single DOM element (or null if not found).
Pros    - It is the fastest selector available.

getElementsByClassName('myClass'):
Target: Selects all elements that share a specific class name.
Returns: A live HTMLCollection. "Live" means if you add or remove elements with this class later via JavaScript, this collection automatically updates itself.

querySelector('.myClass #myId div'):
Target: Highly flexible; it uses standard CSS selector syntax to find elements.
Returns: Only the first element that matches the selector.

querySelectorAll('.myClass'):
Target: Also uses standard CSS selector syntax.
Returns: A static NodeList of all matching elements. "Static" means it is a snapshot; if the DOM changes later, this list will not update automatically.


2. How do you create and insert a new element into the DOM?

Ans: Creating and inserting an element usually involves three distinct steps: creating the node, giving it content/styling, and placing it into the document.

1. Create the element: Use document.createElement().
2. Modify the element: Add text, classes, or other attributes.
3. Insert the element: Select an existing parent element in the DOM and use methods like appendChild(), append(), or prepend() to attach it.


3. What is Event Bubbling? And how does it work?

Ans: Event bubbling is the mechanism by which events propagate (travel) through the DOM tree.

When an event (like a click) happens on an element, it doesn't just trigger the listener on that specific element. After triggering the target element, the event "bubbles up" to its parent, then its grandparent, and so on, all the way up to the document object.

How it works:
If you have a <button> inside a <div> inside a <section>, and you click the button:

1. The <button>'s click event fires.
2. Then, the <div>'s click event fires.
3. Finally, the <section>'s click event fires.
It behaves exactly like a bubble rising from the bottom of a glass of water to the surface.


 4. What is Event Delegation in JavaScript? Why is it useful?

Ans: Event delegation is a clever design pattern that directly relies on Event Bubbling.

Instead of attaching individual event listeners to multiple child elements (like 50 different <li> tags in a list), you attach one single event listener to their common parent (the <ul> tag). When a child is clicked, the event bubbles up to the parent, and you use event.target to figure out exactly which child triggered it.

Why it is useful:

Performance: Attaching 1 listener uses significantly less memory than attaching 50 listeners.
Dynamic Elements: If you use JavaScript to add new <li> items to the list later, you don't need to attach new listeners to them. The parent's listener will automatically catch their clicks via bubbling.

5. What is the difference between preventDefault() and stopPropagation() methods?

Ans: While both methods interrupt standard browser behaviors, they target completely different things:

preventDefault(): Stops the browser's default action associated with an event.
Example: It stops a <form> from refreshing the page when you click submit, or stops an <a> link from navigating to a new URL. It does not stop the event from bubbling up the DOM.

stopPropagation(): Stops the event from bubbling further up the DOM tree.
Example: If you click a button inside a card, stopPropagation() ensures that the parent card's click listener doesn't get triggered. It does not stop default browser behaviors.
