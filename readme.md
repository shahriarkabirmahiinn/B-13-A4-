1. What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?

Ans: All of these are used to select DOM elements, but they work a bit differently under the hood:

getElementById('myId'): It directly looks for a unique ID and returns just that single element (or null). It's the fastest way to grab an element.
getElementsByClassName('myClass'): This selects all elements sharing a specific class. The catch is, it returns a live HTMLCollection. This means if you use JS to add/remove elements with this class later, this collection updates itself automatically.
querySelector('.myClass #myId'): This is super flexible because you can use standard CSS selector syntax. However, it only returns the first element it finds that matches the selector.
querySelectorAll('.myClass'): Similar to querySelector, but it returns all matching elements as a NodeList. Keep in mind, this list is static—it's just a snapshot and won't automatically update if the DOM changes later.


2. How do you create and insert a new element into the DOM?

Ans: Inserting a new element basically takes 3 simple steps: create it, modify it, and put it in the DOM.

1. Create: Use document.createElement('tagName') to make the new node.
2. Modify: Add some content or styles to it (like changing innerText or adding classes via classList.add()).
3. Insert: Grab an existing parent element from the DOM and attach your new element using methods like appendChild(), append(), or prepend().


 3. What is Event Bubbling? And how does it work?

Ans: Event bubbling is how events travel up the DOM tree.

When you trigger an event (like clicking an element), the browser doesn't just run the listener for that specific element. The event actually "bubbles up" to its parent, then the grandparent, and keeps going up to the document root.

How it works in practice:
Imagine you have a <button> inside a <div> inside a <section>, and you click the button. The browser will fire the events in this order:

1. First, the <button> click event fires.
2. Then, the <div> click event fires.
3. Finally, the <section> click event fires.
Just like a bubble rising from the bottom of a glass to the surface.


4. What is Event Delegation in JavaScript? Why is it useful?

Ans: Event delegation is a smart trick that takes advantage of Event Bubbling.

Instead of adding 50 separate event listeners to 50 different <li> tags, you just add one listener to their common parent (like the <ul>). Because clicks bubble up, the parent catches the event, and you can just use event.target to figure out exactly which child was clicked.

Why developers use it:

Performance: Attaching 1 listener takes way less memory than attaching dozens or hundreds.
Handles Dynamic Content: If you add new <li> items to the list later via JS, you don't need to write extra code to attach listeners to them. The parent will automatically catch their clicks.


5. What is the difference between preventDefault() and stopPropagation() methods?

Ans: Both are used to stop things from happening, but they target completely different behaviors.

preventDefault(): This stops the browser from doing its default action. For example, it prevents a form from automatically refreshing the page when you click submit, or stops a link from opening a new URL. It does not stop the event from bubbling.
stopPropagation(): This stops the event from bubbling further up the DOM. For example, if you click a button inside a clickable card, this ensures the parent card's click event doesn't get triggered at the same time. It does not stop default browser behaviors.
