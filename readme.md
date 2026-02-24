1. What is the difference between getElementById, getElementsByClassName, querySelector, and querySelectorAll?
Answer: getElementById Finds exactly one element using its ID. It is very fast.
getElementsByClassName: Finds all elements with a specific class. This list is "live," meaning it updates automatically if you add or remove elements later.
querySelector: Uses CSS styling syntax (like .class or #id) but only grabs the first matching element it finds.
querySelectorAll: Uses CSS syntax to grab all matching elements. This list is a static "snapshot"—it does not update automatically if the page changes.

2. How do you create and insert a new element into the DOM?
Answer: It takes 3 easy steps:
Step 1 - Create: Make the new element using document.createElement('div').
Step 2 - Modify: Add your text, styles, or classes to it.
Step 3 - Insert: Place it on the page inside a parent element using appendChild().

3. What is Event Bubbling?
Answer: When you click an element, the click event doesn't stop there. It "bubbles up" to its parent, then its grandparent, all the way to the top of the page.
Example: If you click a <button> that is inside a <div>, the button's click event happens first, and then the <div>'s click event happens automatically right after it.

4. What is Event Delegation?
Answer: Instead of adding 50 different click listeners to 50 list items (<li>), you attach just one listener to their parent container (like the <ul>).
Why use it? It saves memory and makes your code faster. Also, if you add new list items to the page later, the parent container will automatically handle their clicks too.

5. What is the difference between preventDefault() and stopPropagation()?
Answer: preventDefault(): Stops the browser's normal behavior. 
Example: Stops a form from reloading the whole page when I hit submit, or stops a link from taking you to a new page.
stopPropagation(): Stops Event Bubbling. 
Example: If I click a button inside a card, this stops the click event from bubbling up and triggering the card's click event too.
