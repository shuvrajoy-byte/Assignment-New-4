## Answers to Questions

### 1. What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?
Answers : These methods are interfaces provided by the Document Object Model (DOM) to retrieve elements from an HTML document. They differ in their selection criteria and the type of data they return.
getElementById('id'): Targets a single element with a specific, unique ID. It returns a single Element object. It is the most performant selector because IDs are unique within a document.
getElementsByClassName('class'): Targets all elements with a specific class name. It returns an HTMLCollection, which is a "live" collection (it automatically updates if the DOM changes).
querySelector('selector'): Uses CSS selector syntax to find the first matching element in the document. It is highly versatile but only returns one element.
querySelectorAll('selector'): Uses CSS selector syntax to find all matching elements. It returns a NodeList, which is "static" (it does not update if elements are added or removed later).

Feature	getElementById	getElementsByClassName	querySelector	querySelectorAll
Returns	Single Element	HTMLCollection (Live)	Single Element	NodeList (Static)
Criteria	ID only	Class only	CSS Selector	CSS Selector

### 2. How do you create and insert a new element into the DOM?
Answers : The process of adding a new element to the DOM involves three distinct architectural steps:
Creation Phase: Use the document.createElement(tagName) method to generate a new Node object in the browser's memory.
Configuration Phase: Set the element’s properties, such as textContent, innerHTML, className, or id. You may also use setAttribute() to define custom attributes.
Insertion Phase: Attach the newly created node to the document tree using an existing parent element. Common methods include:
appendChild(): Adds the element as the last child of the parent.
prepend(): Adds the element as the first child of the parent.
insertBefore(newNode, referenceNode): Places the element specifically before a designated sibling.

### 3. What is Event Bubbling? And how does it work?
Answers : Event Bubbling is a mechanism of event propagation in the DOM tree. When an event (such as a click) is triggered on a specific element, the event does not stop there; it "bubbles up" through its ancestors.
How it works:
Target Phase: The event first triggers on the element where the action originated (the target).
Bubbling Phase: The event then triggers on the parent of the target, then the grandparent, and continues upward until it reaches the document and finally the window object.
Default Behavior: By default, almost all event listeners registered using addEventListener are executed during this bubbling phase unless specified otherwise.

### 4. What is Event Delegation in JavaScript? Why is it useful?
Answers : Event Delegation is a design pattern that leverages Event Bubbling. Instead of attaching an event listener to multiple individual child elements, a single listener is attached to a common parent element.
Why it is useful:
Memory Management: Attaching a single listener to a parent container is far more efficient for memory than attaching hundreds of listeners to individual child nodes (e.g., list items in a large menu).
Dynamic Content: If new child elements are added to the DOM after the initial page load (via JavaScript), the delegated listener on the parent will automatically handle their events without needing to manually bind new listeners.
Cleaner Code: It centralizes event-handling logic, making the code easier to maintain and debug.

### 5. What is the difference between preventDefault() and stopPropagation() methods?
Answers : Both methods are used to control the lifecycle of an event, but they serve different technical purposes:
preventDefault(): This method instructs the browser to cancel its default action associated with the event. For example, it prevents a form from refreshing the page upon submission or prevents a hyperlink from navigating to a new URL. The event still continues to bubble up the DOM.
stopPropagation(): This method prevents the event from propagating further through the DOM tree. It ensures that once the event is handled by a specific element, no parent or ancestor elements are notified of the event. The browser's default actions (like a link click) will still occur.
Summary: preventDefault() stops the browser's behavior, while stopPropagation() stops the event's movement through the DOM.