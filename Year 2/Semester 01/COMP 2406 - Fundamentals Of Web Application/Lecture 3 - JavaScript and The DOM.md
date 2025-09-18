#### The Document Object Model

The DOM is a **programming interface for HTML and XML documents**. It represents the page as a structured tree of nodes (elements, attributes, text, etc.).

![[Pasted image 20250916070502.png]]

It defines:
- The HTML elements as **objects**
- The **properties** of all HTML elements
- The **methods** to access all HTML elements
- The **events** for all HTML elements

**Tree Structure**:
- The root node is the `document` object.
- Elements are nodes (`<div>`, `<p>`, `<img>`, etc.).
- Text inside elements is also represented as text nodes.
- Attributes (`id`, `class`, etc.) are nodes attached to element nodes.

JavaScript uses the DOM to **read** and **manipulate** the page. For example:
```
document.getElementById("title").textContent = "Hello DOM!";
```



---
#### Event Propagation

When an event happens (like a click), it doesn’t just stay at the element. It **propagates** through the DOM in phases.

##### **Phases of Event Propagation**
1. **Capturing phase** (rarely used):  
    The event travels _down_ from the root (`document`) toward the target element.
    
2. **Target phase**:  
    The event reaches the element that was actually interacted with.
    
3. **Bubbling phase** (most common):  
    The event then “bubbles up” from the target element back up through its ancestors (parent → grandparent → `document`).

##### **Example**
HTML:
```
<div id="parent">
  <button id="child">Click me</button>
</div>
```

JS:
```
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Child clicked");
});
```

If you click the **button**:
- First: `"Child clicked"` logs (target phase).
- Then: `"Parent clicked"` logs (bubbling phase).

##### Control Propagation
- `event.stopPropagation()` → stops the event from continuing to bubble or capture.
- `event.preventDefault()` → stops the default browser action (e.g., preventing a form submission).



---
#### Code Examples

**Finding HTML Elements**

| Method                                  | Description                   |
| --------------------------------------- | ----------------------------- |
| document.getElementById(_id_)           | Find an element by element id |
| document.getElementsByTagName(_name_)   | Find elements by tag name     |
| document.getElementsByClassName(_name_) | Find elements by class name   |


**Changing HTML Elements**

|Property|Description|
|---|---|
|_element_.innerHTML =  _new html content_|Change the inner HTML of an element|
|_element_._attribute = new value_|Change the attribute value of an HTML element|
|_element_.style._property = new style_|Change the style of an HTML element|
|Method|Description|
|_element_.setAttribute_(attribute, value)_|Change the attribute value of an HTML element|


**Adding and Deleting Elements**

|Method|Description|
|---|---|
|document.createElement(_element_)|Create an HTML element|
|document.removeChild(_element_)|Remove an HTML element|
|document.appendChild(_element_)|Add an HTML element|
|document.replaceChild(_new, old_)|Replace an HTML element|
|document.write(_text_)|Write into the HTML output stream|


**Adding Event Handlers**

|Method|Description|
|---|---|
|document.getElementById(_id_).onclick = function(){_code_}|Adding event handler code to an onclick event|


**Set text on element :**
`document.getElementById("demo").innerHTML = "Hello World!";`

**Change CSS :**
`document.getElementById(id).style.property = new style`

```
<button type="button"  
onclick="document.getElementById('id1').style.color = 'red'">  
Click Me!</button>
```


**Accessing Nodes :**

```
myTitle = document.getElementById("demo").firstChild.nodeValue;

myTitle = document.getElementById("demo").childNodes[0].nodeValue;
```


**Adding or Removing Nodes:**
To add a new element to the HTML DOM, you must create the element (element node) first, and then append it to an existing element.


```
const para = document.createElement("p");
const node = document.createTextNode("This is a new paragraph.");
para.appendChild(node);
const element = document.getElementById("div1");
element.appendChild(para);
```


**Collections**
The `getElementsByTagName()` method returns an `HTMLCollection` object.
An `HTMLCollection` object is an array-like list (collection) of HTML elements.

Example :

```
const myCollection = document.getElementsByTagName("p");
// Access second element : myCollection[1]

myCollection.length // Number of elements in collection

```


