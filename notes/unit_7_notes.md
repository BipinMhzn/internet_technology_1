# Unit 7: Advanced Topics on JavaScript

**Course:** Internet Technology (CMP 173)
**Program:** BCSIT, Pokhara University
**Duration:** 7 Hours

---

## Table of Contents

- [7.1 Scope and Closures](#71-scope-and-closures)
- [7.2 Error Handling and Debugging](#72-error-handling-and-debugging)
- [7.3 DOM Manipulation](#73-dom-manipulation)
- [7.4 Asynchronous JavaScript](#74-asynchronous-javascript)
- [7.5 JSON and AJAX](#75-json-and-ajax)
- [7.6 ES6 and Modern JavaScript](#76-es6-and-modern-javascript)
- [7.7 JavaScript Libraries](#77-javascript-libraries)
- [Practice Exercises](#practice-exercises)
- [References](#references)

---

## Learning Objectives

After completing this unit, students will be able to:

- Grasp the intricacies of scope, variable visibility, and the concept of closures
- Manage errors using try-catch blocks, exceptions, and employ debugging techniques
- Manipulate the Document Object Model (DOM) to interact with HTML elements and handle events
- Master asynchronous programming, including callback functions, promises, and async/await
- Work with JSON data and make AJAX requests using fetch API or XMLHttpRequest
- Explore ES6 features like arrow functions, template literals, let and const keywords, and destructuring assignments
- Understand modern JavaScript concepts, such as modules and import/export functionality
- Gain exposure to popular JavaScript libraries/frameworks like React, Angular, or Vue.js for building web applications
- Elevate JavaScript skills to enable dynamic and interactive web development

---

## 7.1 Scope and Closures

### What is Scope?

Scope determines the accessibility (visibility) of variables in different parts of your code. It defines where variables can be accessed or referenced.

### Types of Scope

#### 1. Global Scope

Variables declared outside any function or block have global scope and can be accessed from anywhere in the code.

```javascript
// Global scope
var globalVar = "I'm global";
let globalLet = "I'm also global";
const globalConst = "I'm global too";

function showGlobal() {
    console.log(globalVar);   // Accessible
    console.log(globalLet);   // Accessible
    console.log(globalConst); // Accessible
}

showGlobal();
console.log(globalVar);  // Accessible everywhere
```

> **Warning:** Avoid excessive use of global variables as they can cause naming conflicts and make code harder to maintain.

#### 2. Function Scope (Local Scope)

Variables declared inside a function are only accessible within that function.

```javascript
function myFunction() {
    // Function scope
    var functionVar = "I'm function-scoped";
    let functionLet = "I'm also function-scoped";

    console.log(functionVar);  // Accessible
    console.log(functionLet);  // Accessible
}

myFunction();
// console.log(functionVar);  // Error: not defined
// console.log(functionLet);  // Error: not defined
```

#### 3. Block Scope (ES6)

Variables declared with `let` and `const` inside a block `{}` are only accessible within that block.

```javascript
if (true) {
    // Block scope
    var blockVar = "I'm NOT block-scoped (var)";
    let blockLet = "I'm block-scoped (let)";
    const blockConst = "I'm block-scoped (const)";

    console.log(blockLet);    // Accessible
    console.log(blockConst);  // Accessible
}

console.log(blockVar);    // Accessible (var ignores block scope)
// console.log(blockLet);    // Error: not defined
// console.log(blockConst);  // Error: not defined
```

### Scope Chain

When a variable is used, JavaScript looks for it in the current scope, then moves up to outer scopes until it finds the variable or reaches global scope.

```javascript
let global = "Global";

function outer() {
    let outerVar = "Outer";

    function inner() {
        let innerVar = "Inner";

        // Can access all variables in the scope chain
        console.log(innerVar);  // "Inner"
        console.log(outerVar);  // "Outer"
        console.log(global);    // "Global"
    }

    inner();
    // console.log(innerVar);  // Error: not defined
}

outer();
```

### Variable Hoisting

JavaScript moves variable declarations to the top of their scope during compilation.

```javascript
// What you write:
console.log(x);  // undefined (not an error!)
var x = 5;
console.log(x);  // 5

// What JavaScript sees:
var x;           // Declaration hoisted
console.log(x);  // undefined
x = 5;           // Assignment stays in place
console.log(x);  // 5

// let and const are NOT hoisted the same way
// console.log(y);  // Error: Cannot access 'y' before initialization
let y = 10;
```

### Temporal Dead Zone (TDZ)

The period between entering a scope and the variable being declared where `let` and `const` variables cannot be accessed.

```javascript
{
    // TDZ starts
    // console.log(myVar);  // Error: Cannot access before initialization
    // TDZ ends
    let myVar = "Hello";
    console.log(myVar);     // "Hello"
}
```

---

### Closures

A closure is a function that remembers and can access variables from its outer (enclosing) scope even after the outer function has finished executing.

#### Basic Closure Example

```javascript
function outerFunction() {
    let outerVariable = "I'm from outer function";

    function innerFunction() {
        // innerFunction has access to outerVariable
        console.log(outerVariable);
    }

    return innerFunction;
}

const myClosure = outerFunction();
myClosure();  // "I'm from outer function"
// outerVariable is still accessible even though outerFunction has completed
```

#### Practical Closure Examples

**1. Counter with Private State:**
```javascript
function createCounter() {
    let count = 0;  // Private variable

    return {
        increment: function() {
            count++;
            return count;
        },
        decrement: function() {
            count--;
            return count;
        },
        getCount: function() {
            return count;
        }
    };
}

const counter = createCounter();
console.log(counter.increment());  // 1
console.log(counter.increment());  // 2
console.log(counter.decrement());  // 1
console.log(counter.getCount());   // 1
// console.log(count);  // Error: count is not defined (private)
```

**2. Function Factory:**
```javascript
function multiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = multiplier(2);
const triple = multiplier(3);

console.log(double(5));  // 10
console.log(triple(5));  // 15
```

**3. Data Privacy / Encapsulation:**
```javascript
function createBankAccount(initialBalance) {
    let balance = initialBalance;  // Private

    return {
        deposit: function(amount) {
            if (amount > 0) {
                balance += amount;
                return `Deposited: $${amount}. New balance: $${balance}`;
            }
            return "Invalid amount";
        },
        withdraw: function(amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                return `Withdrawn: $${amount}. New balance: $${balance}`;
            }
            return "Invalid amount or insufficient funds";
        },
        getBalance: function() {
            return `Balance: $${balance}`;
        }
    };
}

const account = createBankAccount(100);
console.log(account.deposit(50));    // "Deposited: $50. New balance: $150"
console.log(account.withdraw(30));   // "Withdrawn: $30. New balance: $120"
console.log(account.getBalance());   // "Balance: $120"
// balance variable is not directly accessible
```

**4. Loop with Closures (Common Pitfall and Solution):**
```javascript
// Problem: All callbacks share the same 'i'
for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);  // Prints: 3, 3, 3
    }, 1000);
}

// Solution 1: Use let (block-scoped)
for (let i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);  // Prints: 0, 1, 2
    }, 1000);
}

// Solution 2: Use closure with IIFE
for (var i = 0; i < 3; i++) {
    (function(j) {
        setTimeout(function() {
            console.log(j);  // Prints: 0, 1, 2
        }, 1000);
    })(i);
}
```

### Scope and Closure Summary

| Concept | Description |
|---------|-------------|
| **Global Scope** | Variables accessible everywhere |
| **Function Scope** | Variables accessible only within the function |
| **Block Scope** | Variables (`let`/`const`) accessible only within the block |
| **Scope Chain** | Nested functions can access outer variables |
| **Hoisting** | Variable declarations moved to top of scope |
| **Closure** | Function retaining access to outer scope variables |

---

## 7.2 Error Handling and Debugging

### Types of Errors

#### 1. Syntax Errors

Errors in the code structure that prevent the script from running.

```javascript
// Missing closing parenthesis
// console.log("Hello";  // SyntaxError

// Missing quotes
// let name = Hello;  // SyntaxError
```

#### 2. Runtime Errors (Exceptions)

Errors that occur during script execution.

```javascript
// Calling undefined function
// nonExistentFunction();  // ReferenceError

// Accessing property of undefined
let obj;
// console.log(obj.property);  // TypeError
```

#### 3. Logical Errors

Code runs but produces incorrect results.

```javascript
// Intended to calculate average
function wrongAverage(a, b) {
    return a + b / 2;  // Wrong: should be (a + b) / 2
}

console.log(wrongAverage(10, 20));  // 20 (wrong, should be 15)
```

### Common Error Types

| Error Type | Description |
|------------|-------------|
| **SyntaxError** | Invalid JavaScript syntax |
| **ReferenceError** | Reference to undeclared variable |
| **TypeError** | Value is not of expected type |
| **RangeError** | Number out of valid range |
| **URIError** | Invalid use of URI functions |
| **EvalError** | Error related to eval() function |

---

### try...catch Statement

Handle errors gracefully without crashing the program.

```javascript
try {
    // Code that might throw an error
    let result = riskyOperation();
    console.log(result);
} catch (error) {
    // Code to handle the error
    console.log("An error occurred:", error.message);
}
```

#### Error Object Properties

```javascript
try {
    undefinedFunction();
} catch (error) {
    console.log(error.name);     // "ReferenceError"
    console.log(error.message);  // "undefinedFunction is not defined"
    console.log(error.stack);    // Stack trace (useful for debugging)
}
```

### try...catch...finally

The `finally` block always executes, regardless of whether an error occurred.

```javascript
function readFile() {
    let file = null;

    try {
        file = openFile("data.txt");
        processFile(file);
    } catch (error) {
        console.log("Error processing file:", error.message);
    } finally {
        // Always runs - cleanup code
        if (file) {
            closeFile(file);
        }
        console.log("Cleanup complete");
    }
}
```

**Practical Example:**
```javascript
function divideNumbers(a, b) {
    try {
        if (b === 0) {
            throw new Error("Cannot divide by zero");
        }
        return a / b;
    } catch (error) {
        console.log("Error:", error.message);
        return null;
    } finally {
        console.log("Division operation attempted");
    }
}

console.log(divideNumbers(10, 2));   // 5, "Division operation attempted"
console.log(divideNumbers(10, 0));   // null, Error message, "Division operation attempted"
```

### throw Statement

Create custom errors using the `throw` statement.

```javascript
function validateAge(age) {
    if (typeof age !== "number") {
        throw new TypeError("Age must be a number");
    }
    if (age < 0) {
        throw new RangeError("Age cannot be negative");
    }
    if (age < 18) {
        throw new Error("Must be 18 or older");
    }
    return "Age is valid";
}

try {
    console.log(validateAge(15));
} catch (error) {
    console.log(`${error.name}: ${error.message}`);
    // "Error: Must be 18 or older"
}
```

### Custom Error Classes

Create specialized error types for better error handling.

```javascript
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = "ValidationError";
    }
}

class DatabaseError extends Error {
    constructor(message) {
        super(message);
        this.name = "DatabaseError";
    }
}

function saveUser(user) {
    if (!user.name) {
        throw new ValidationError("Name is required");
    }
    if (!user.email) {
        throw new ValidationError("Email is required");
    }

    // Simulate database error
    throw new DatabaseError("Connection failed");
}

try {
    saveUser({ name: "John" });
} catch (error) {
    if (error instanceof ValidationError) {
        console.log("Validation failed:", error.message);
    } else if (error instanceof DatabaseError) {
        console.log("Database error:", error.message);
    } else {
        console.log("Unknown error:", error.message);
    }
}
```

---

### Debugging Techniques

#### 1. Console Methods

```javascript
// Basic logging
console.log("Regular message");
console.info("Information");
console.warn("Warning message");
console.error("Error message");

// Logging objects
let user = { name: "John", age: 30 };
console.log(user);
console.table(user);  // Display as table

// Logging arrays
let numbers = [1, 2, 3, 4, 5];
console.table(numbers);

// Grouping logs
console.group("User Details");
console.log("Name: John");
console.log("Age: 30");
console.groupEnd();

// Timing code execution
console.time("Loop");
for (let i = 0; i < 1000000; i++) { }
console.timeEnd("Loop");  // "Loop: 5.123ms"

// Counting occurrences
function processItem() {
    console.count("processItem called");
}
processItem();  // "processItem called: 1"
processItem();  // "processItem called: 2"

// Assertions
console.assert(1 === 2, "1 is not equal to 2");  // Shows error

// Stack trace
console.trace("Trace message");

// Clear console
console.clear();
```

#### 2. debugger Statement

Pauses code execution at the specified point (when DevTools is open).

```javascript
function calculateTotal(items) {
    let total = 0;

    for (let item of items) {
        debugger;  // Execution pauses here
        total += item.price * item.quantity;
    }

    return total;
}
```

#### 3. Browser DevTools

**Key Features:**
- **Elements Panel:** Inspect and modify HTML/CSS
- **Console Panel:** Execute JavaScript, view logs
- **Sources Panel:** Set breakpoints, step through code
- **Network Panel:** Monitor HTTP requests
- **Application Panel:** View storage, cookies, cache

**Breakpoint Types:**
- Line breakpoints
- Conditional breakpoints
- DOM breakpoints
- XHR breakpoints
- Event listener breakpoints

#### 4. Debugging Best Practices

```javascript
// 1. Use descriptive variable names
let userAge = 25;  // Good
let x = 25;        // Bad

// 2. Add meaningful logs
console.log(`Processing user: ${user.name}, ID: ${user.id}`);

// 3. Check variable types
console.log(typeof variable);
console.log(Array.isArray(variable));

// 4. Validate function inputs
function processData(data) {
    console.log("Input:", data);
    console.log("Type:", typeof data);

    if (!data) {
        console.error("No data provided");
        return;
    }
    // Process data...
}

// 5. Use try-catch for risky operations
try {
    JSON.parse(invalidJSON);
} catch (e) {
    console.error("JSON parsing failed:", e.message);
}
```

---

## 7.3 DOM Manipulation

### What is the DOM?

The Document Object Model (DOM) is a programming interface for HTML documents. It represents the page as a tree structure where each node is an object representing a part of the document.

```
document
└── html
    ├── head
    │   └── title
    └── body
        ├── h1
        ├── p
        └── div
            └── span
```

### Selecting Elements

#### 1. getElementById()

Select a single element by its ID.

```javascript
let element = document.getElementById("myId");
console.log(element);
```

```html
<div id="myId">Hello World</div>
```

#### 2. getElementsByClassName()

Select all elements with a specific class (returns HTMLCollection).

```javascript
let elements = document.getElementsByClassName("myClass");
console.log(elements);        // HTMLCollection
console.log(elements[0]);     // First element
console.log(elements.length); // Number of elements

// Iterate
for (let element of elements) {
    console.log(element);
}
```

#### 3. getElementsByTagName()

Select all elements with a specific tag (returns HTMLCollection).

```javascript
let paragraphs = document.getElementsByTagName("p");
let divs = document.getElementsByTagName("div");
```

#### 4. querySelector()

Select the first element matching a CSS selector.

```javascript
// By ID
let byId = document.querySelector("#myId");

// By class
let byClass = document.querySelector(".myClass");

// By tag
let byTag = document.querySelector("p");

// By attribute
let byAttr = document.querySelector("[data-id='123']");

// Complex selectors
let nested = document.querySelector("div.container > p.intro");
let pseudo = document.querySelector("li:first-child");
```

#### 5. querySelectorAll()

Select all elements matching a CSS selector (returns NodeList).

```javascript
let allParagraphs = document.querySelectorAll("p");
let allButtons = document.querySelectorAll(".btn");
let allListItems = document.querySelectorAll("ul > li");

// Iterate with forEach
allParagraphs.forEach(function(p) {
    console.log(p.textContent);
});

// Convert to array
let array = Array.from(allParagraphs);
```

### Selector Methods Comparison

| Method | Returns | Live? | Use Case |
|--------|---------|-------|----------|
| `getElementById()` | Single element | No | Select by unique ID |
| `getElementsByClassName()` | HTMLCollection | Yes | Select by class name |
| `getElementsByTagName()` | HTMLCollection | Yes | Select by tag name |
| `querySelector()` | Single element | No | Select first match with CSS selector |
| `querySelectorAll()` | NodeList | No | Select all matches with CSS selector |

> **Note:** "Live" collections automatically update when the DOM changes.

---

### Modifying Elements

#### 1. Changing Content

```javascript
let element = document.getElementById("demo");

// innerHTML - includes HTML tags
element.innerHTML = "<strong>Bold text</strong>";

// textContent - plain text only (safer)
element.textContent = "Plain text";

// innerText - visible text only (respects CSS)
element.innerText = "Visible text";
```

**innerHTML vs textContent:**
```javascript
let div = document.getElementById("myDiv");

// innerHTML (can be security risk - XSS)
div.innerHTML = "<script>alert('XSS')</script>";  // Dangerous!

// textContent (safe - escapes HTML)
div.textContent = "<script>alert('XSS')</script>";  // Displays as text
```

#### 2. Changing Attributes

```javascript
let img = document.querySelector("img");

// Get attribute
let src = img.getAttribute("src");

// Set attribute
img.setAttribute("src", "new-image.jpg");
img.setAttribute("alt", "Description");

// Remove attribute
img.removeAttribute("title");

// Check if attribute exists
if (img.hasAttribute("alt")) {
    console.log("Alt text exists");
}

// Direct property access (for standard attributes)
img.src = "another-image.jpg";
img.alt = "Another description";
img.id = "mainImage";
```

#### 3. Changing Styles

```javascript
let element = document.getElementById("myElement");

// Individual style properties (camelCase)
element.style.color = "red";
element.style.backgroundColor = "yellow";
element.style.fontSize = "20px";
element.style.marginTop = "10px";
element.style.display = "none";

// Multiple styles at once
element.style.cssText = "color: red; background-color: yellow; font-size: 20px;";

// Get computed styles
let styles = window.getComputedStyle(element);
console.log(styles.color);
console.log(styles.fontSize);
```

#### 4. Changing Classes

```javascript
let element = document.getElementById("myElement");

// classList methods (modern and preferred)
element.classList.add("active");
element.classList.remove("inactive");
element.classList.toggle("visible");      // Add if missing, remove if present
element.classList.replace("old", "new");
element.classList.contains("active");     // Returns true/false

// Add multiple classes
element.classList.add("class1", "class2", "class3");

// className property (replaces all classes)
element.className = "newClass";
element.className = "class1 class2";
```

---

### Creating and Inserting Elements

#### 1. Creating Elements

```javascript
// Create element
let newDiv = document.createElement("div");
let newParagraph = document.createElement("p");
let newSpan = document.createElement("span");

// Add content
newDiv.textContent = "I'm a new div";
newDiv.innerHTML = "<strong>Bold content</strong>";

// Add attributes
newDiv.id = "newDiv";
newDiv.className = "container";
newDiv.setAttribute("data-id", "123");

// Add styles
newDiv.style.color = "blue";
newDiv.style.padding = "10px";
```

#### 2. Inserting Elements

```javascript
let parent = document.getElementById("container");
let newElement = document.createElement("p");
newElement.textContent = "New paragraph";

// appendChild - add as last child
parent.appendChild(newElement);

// insertBefore - insert before a reference element
let reference = document.getElementById("reference");
parent.insertBefore(newElement, reference);

// Modern methods (ES6+)
// insertAdjacentElement(position, element)
// Positions: 'beforebegin', 'afterbegin', 'beforeend', 'afterend'

let target = document.getElementById("target");

target.insertAdjacentElement('beforebegin', newElement);  // Before target
target.insertAdjacentElement('afterbegin', newElement);   // First child
target.insertAdjacentElement('beforeend', newElement);    // Last child
target.insertAdjacentElement('afterend', newElement);     // After target

// insertAdjacentHTML - insert HTML string
target.insertAdjacentHTML('beforeend', '<p>New HTML</p>');

// insertAdjacentText - insert text
target.insertAdjacentText('beforeend', 'New text');
```

**Visual representation of positions:**
```html
<!-- beforebegin -->
<div id="target">
    <!-- afterbegin -->
    Existing content
    <!-- beforeend -->
</div>
<!-- afterend -->
```

#### 3. Cloning Elements

```javascript
let original = document.getElementById("original");

// Shallow clone (element only)
let shallowClone = original.cloneNode(false);

// Deep clone (element and all descendants)
let deepClone = original.cloneNode(true);

document.body.appendChild(deepClone);
```

#### 4. Removing Elements

```javascript
let element = document.getElementById("toRemove");

// Modern method
element.remove();

// Older method (using parent)
let parent = element.parentNode;
parent.removeChild(element);

// Remove all children
let container = document.getElementById("container");
container.innerHTML = "";  // Quick but destroys event listeners

// Better: remove children one by one
while (container.firstChild) {
    container.removeChild(container.firstChild);
}
```

---

### Traversing the DOM

```javascript
let element = document.getElementById("myElement");

// Parent
let parent = element.parentNode;
let parentElement = element.parentElement;

// Children
let children = element.childNodes;       // All nodes (including text)
let childElements = element.children;    // Element nodes only
let firstChild = element.firstChild;     // First node
let firstElement = element.firstElementChild;  // First element
let lastChild = element.lastChild;
let lastElement = element.lastElementChild;

// Siblings
let nextSibling = element.nextSibling;           // Next node
let nextElement = element.nextElementSibling;    // Next element
let prevSibling = element.previousSibling;
let prevElement = element.previousElementSibling;

// Closest ancestor matching selector
let closestDiv = element.closest("div");
let closestContainer = element.closest(".container");
```

---

### Event Handling

Events are actions that happen in the browser (clicks, key presses, page load, etc.).

#### 1. Inline Event Handlers (Not Recommended)

```html
<button onclick="handleClick()">Click Me</button>
<script>
    function handleClick() {
        alert("Clicked!");
    }
</script>
```

#### 2. DOM Property Event Handlers

```javascript
let button = document.getElementById("myButton");

button.onclick = function() {
    alert("Clicked!");
};

// Limitation: can only attach one handler
button.onclick = function() {
    alert("New handler - previous one is replaced!");
};
```

#### 3. addEventListener() (Recommended)

```javascript
let button = document.getElementById("myButton");

// Basic syntax
button.addEventListener("click", function() {
    alert("Clicked!");
});

// Named function (useful for removing)
function handleClick() {
    alert("Clicked!");
}
button.addEventListener("click", handleClick);

// Arrow function
button.addEventListener("click", () => {
    alert("Clicked!");
});

// Multiple handlers on same event
button.addEventListener("click", function() {
    console.log("Handler 1");
});
button.addEventListener("click", function() {
    console.log("Handler 2");
});
// Both handlers execute

// Remove event listener
button.removeEventListener("click", handleClick);
```

#### 4. The Event Object

```javascript
button.addEventListener("click", function(event) {
    // Event properties
    console.log(event.type);        // "click"
    console.log(event.target);      // Element that triggered event
    console.log(event.currentTarget); // Element with the listener
    console.log(event.timeStamp);   // When event occurred

    // Mouse event properties
    console.log(event.clientX);     // X coordinate in viewport
    console.log(event.clientY);     // Y coordinate in viewport
    console.log(event.pageX);       // X coordinate in document
    console.log(event.pageY);       // Y coordinate in document
    console.log(event.button);      // Which mouse button

    // Keyboard event properties
    console.log(event.key);         // Key pressed
    console.log(event.code);        // Physical key code
    console.log(event.ctrlKey);     // Ctrl held?
    console.log(event.shiftKey);    // Shift held?
    console.log(event.altKey);      // Alt held?

    // Prevent default behavior
    event.preventDefault();

    // Stop event propagation
    event.stopPropagation();
});
```

#### 5. Common Events

**Mouse Events:**
```javascript
element.addEventListener("click", handler);       // Single click
element.addEventListener("dblclick", handler);    // Double click
element.addEventListener("mousedown", handler);   // Mouse button pressed
element.addEventListener("mouseup", handler);     // Mouse button released
element.addEventListener("mousemove", handler);   // Mouse moved
element.addEventListener("mouseenter", handler);  // Mouse enters element
element.addEventListener("mouseleave", handler);  // Mouse leaves element
element.addEventListener("mouseover", handler);   // Mouse over (bubbles)
element.addEventListener("mouseout", handler);    // Mouse out (bubbles)
element.addEventListener("contextmenu", handler); // Right-click
```

**Keyboard Events:**
```javascript
document.addEventListener("keydown", function(e) {
    console.log("Key pressed:", e.key);
});
document.addEventListener("keyup", function(e) {
    console.log("Key released:", e.key);
});
document.addEventListener("keypress", function(e) {
    console.log("Key pressed (deprecated):", e.key);
});
```

**Form Events:**
```javascript
form.addEventListener("submit", function(e) {
    e.preventDefault();  // Prevent form submission
    console.log("Form submitted");
});

input.addEventListener("focus", function() {
    console.log("Input focused");
});
input.addEventListener("blur", function() {
    console.log("Input lost focus");
});
input.addEventListener("input", function(e) {
    console.log("Value changed:", e.target.value);
});
input.addEventListener("change", function(e) {
    console.log("Value changed (on blur):", e.target.value);
});
```

**Window/Document Events:**
```javascript
window.addEventListener("load", function() {
    console.log("Page fully loaded");
});
document.addEventListener("DOMContentLoaded", function() {
    console.log("DOM ready");
});
window.addEventListener("resize", function() {
    console.log("Window resized");
});
window.addEventListener("scroll", function() {
    console.log("Page scrolled");
});
```

#### 6. Event Propagation

Events propagate through the DOM in three phases:
1. **Capturing Phase:** Event travels from root to target
2. **Target Phase:** Event reaches the target element
3. **Bubbling Phase:** Event bubbles up from target to root

```javascript
// Bubbling (default)
parent.addEventListener("click", function() {
    console.log("Parent clicked");
});
child.addEventListener("click", function() {
    console.log("Child clicked");
});
// Clicking child: "Child clicked", then "Parent clicked"

// Capturing (third parameter: true)
parent.addEventListener("click", function() {
    console.log("Parent clicked");
}, true);

// Stop propagation
child.addEventListener("click", function(e) {
    e.stopPropagation();
    console.log("Child clicked - propagation stopped");
});
```

#### 7. Event Delegation

Handle events on multiple elements using a single listener on a parent.

```javascript
// Instead of adding listeners to each list item:
let list = document.getElementById("myList");

list.addEventListener("click", function(e) {
    if (e.target.tagName === "LI") {
        console.log("Clicked:", e.target.textContent);
        e.target.classList.toggle("selected");
    }
});

// Works for dynamically added items too!
let newItem = document.createElement("li");
newItem.textContent = "New Item";
list.appendChild(newItem);  // Click handler already works
```

---

### DOM Manipulation Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
    <style>
        .highlight { background-color: yellow; }
        .completed { text-decoration: line-through; }
    </style>
</head>
<body>
    <h1 id="title">Todo List</h1>
    <input type="text" id="todoInput" placeholder="Enter todo">
    <button id="addBtn">Add</button>
    <ul id="todoList"></ul>

    <script>
        const input = document.getElementById("todoInput");
        const addBtn = document.getElementById("addBtn");
        const list = document.getElementById("todoList");

        // Add todo
        addBtn.addEventListener("click", function() {
            const text = input.value.trim();
            if (text) {
                const li = document.createElement("li");
                li.textContent = text;

                // Add delete button
                const deleteBtn = document.createElement("button");
                deleteBtn.textContent = "Delete";
                deleteBtn.style.marginLeft = "10px";
                li.appendChild(deleteBtn);

                list.appendChild(li);
                input.value = "";
            }
        });

        // Event delegation for list
        list.addEventListener("click", function(e) {
            if (e.target.tagName === "LI") {
                e.target.classList.toggle("completed");
            }
            if (e.target.tagName === "BUTTON") {
                e.target.parentElement.remove();
            }
        });

        // Add on Enter key
        input.addEventListener("keypress", function(e) {
            if (e.key === "Enter") {
                addBtn.click();
            }
        });
    </script>
</body>
</html>
```

---

## 7.4 Asynchronous JavaScript

### Synchronous vs Asynchronous

**Synchronous:** Code executes line by line, each line waits for the previous one to complete.

```javascript
console.log("First");
console.log("Second");
console.log("Third");
// Output: First, Second, Third (in order)
```

**Asynchronous:** Code can execute without waiting for previous operations to complete.

```javascript
console.log("First");
setTimeout(() => console.log("Second"), 1000);
console.log("Third");
// Output: First, Third, Second (Third appears before Second)
```

### Why Asynchronous Programming?

- Network requests (fetching data from servers)
- File operations
- Timers and intervals
- User interactions
- Database queries

Without asynchronous programming, the browser would freeze while waiting for slow operations.

---

### Callback Functions

A callback is a function passed as an argument to another function, to be executed later.

```javascript
// Simple callback
function greet(name, callback) {
    console.log("Hello, " + name);
    callback();
}

greet("John", function() {
    console.log("Greeting complete!");
});

// Asynchronous callback
function fetchData(callback) {
    setTimeout(function() {
        const data = { name: "John", age: 30 };
        callback(data);
    }, 2000);
}

console.log("Fetching data...");
fetchData(function(data) {
    console.log("Data received:", data);
});
console.log("Request sent");

// Output:
// Fetching data...
// Request sent
// (after 2 seconds) Data received: { name: "John", age: 30 }
```

#### Callback Hell (Pyramid of Doom)

Nested callbacks become difficult to read and maintain.

```javascript
// Callback hell example
getUser(userId, function(user) {
    getOrders(user.id, function(orders) {
        getOrderDetails(orders[0].id, function(details) {
            getShippingInfo(details.shippingId, function(shipping) {
                console.log("Shipping info:", shipping);
            }, function(error) {
                console.log("Error:", error);
            });
        }, function(error) {
            console.log("Error:", error);
        });
    }, function(error) {
        console.log("Error:", error);
    });
}, function(error) {
    console.log("Error:", error);
});
```

---

### Promises

A Promise is an object representing the eventual completion or failure of an asynchronous operation.

#### Promise States

1. **Pending:** Initial state, neither fulfilled nor rejected
2. **Fulfilled:** Operation completed successfully
3. **Rejected:** Operation failed

#### Creating a Promise

```javascript
const myPromise = new Promise(function(resolve, reject) {
    // Asynchronous operation
    setTimeout(function() {
        const success = true;

        if (success) {
            resolve("Operation successful!");  // Fulfilled
        } else {
            reject("Operation failed!");       // Rejected
        }
    }, 2000);
});
```

#### Consuming a Promise

```javascript
myPromise
    .then(function(result) {
        console.log("Success:", result);
    })
    .catch(function(error) {
        console.log("Error:", error);
    })
    .finally(function() {
        console.log("Promise completed");  // Always runs
    });
```

#### Promise Chaining

```javascript
function fetchUser(userId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve({ id: userId, name: "John" });
        }, 1000);
    });
}

function fetchOrders(user) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve([{ id: 1, item: "Book" }, { id: 2, item: "Pen" }]);
        }, 1000);
    });
}

function fetchOrderDetails(orderId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve({ orderId: orderId, total: 50 });
        }, 1000);
    });
}

// Chained promises (much cleaner than callbacks)
fetchUser(123)
    .then(user => {
        console.log("User:", user);
        return fetchOrders(user);
    })
    .then(orders => {
        console.log("Orders:", orders);
        return fetchOrderDetails(orders[0].id);
    })
    .then(details => {
        console.log("Details:", details);
    })
    .catch(error => {
        console.log("Error:", error);
    });
```

#### Promise Static Methods

```javascript
// Promise.all - wait for all promises
const promise1 = fetch("/api/users");
const promise2 = fetch("/api/posts");
const promise3 = fetch("/api/comments");

Promise.all([promise1, promise2, promise3])
    .then(([users, posts, comments]) => {
        console.log("All data loaded");
    })
    .catch(error => {
        console.log("One or more requests failed");
    });

// Promise.allSettled - wait for all, regardless of success/failure
Promise.allSettled([promise1, promise2, promise3])
    .then(results => {
        results.forEach(result => {
            if (result.status === "fulfilled") {
                console.log("Success:", result.value);
            } else {
                console.log("Failed:", result.reason);
            }
        });
    });

// Promise.race - first promise to settle
Promise.race([promise1, promise2, promise3])
    .then(firstResult => {
        console.log("First completed:", firstResult);
    });

// Promise.any - first promise to fulfill
Promise.any([promise1, promise2, promise3])
    .then(firstSuccess => {
        console.log("First success:", firstSuccess);
    })
    .catch(error => {
        console.log("All promises rejected");
    });

// Promise.resolve / Promise.reject
const resolved = Promise.resolve("Immediate value");
const rejected = Promise.reject("Immediate error");
```

---

### Async/Await

Async/await is syntactic sugar over promises, making asynchronous code look synchronous.

#### Basic Syntax

```javascript
// Async function declaration
async function fetchData() {
    // await pauses execution until promise resolves
    const response = await fetch("/api/data");
    const data = await response.json();
    return data;
}

// Arrow function
const fetchData = async () => {
    const response = await fetch("/api/data");
    return response.json();
};
```

#### Error Handling with try/catch

```javascript
async function fetchUser(userId) {
    try {
        const response = await fetch(`/api/users/${userId}`);

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        const user = await response.json();
        return user;
    } catch (error) {
        console.log("Error fetching user:", error.message);
        throw error;  // Re-throw if needed
    }
}

// Usage
async function main() {
    try {
        const user = await fetchUser(123);
        console.log("User:", user);
    } catch (error) {
        console.log("Failed:", error);
    }
}

main();
```

#### Sequential vs Parallel Execution

```javascript
// Sequential (one after another)
async function sequential() {
    const user = await fetchUser(1);      // Wait
    const posts = await fetchPosts(1);    // Then wait
    const comments = await fetchComments(1);  // Then wait

    return { user, posts, comments };
}

// Parallel (all at once)
async function parallel() {
    const [user, posts, comments] = await Promise.all([
        fetchUser(1),
        fetchPosts(1),
        fetchComments(1)
    ]);

    return { user, posts, comments };
}
```

#### Async/Await with Loops

```javascript
const userIds = [1, 2, 3, 4, 5];

// Sequential processing
async function processSequential() {
    for (const id of userIds) {
        const user = await fetchUser(id);
        console.log(user);
    }
}

// Parallel processing
async function processParallel() {
    const promises = userIds.map(id => fetchUser(id));
    const users = await Promise.all(promises);
    users.forEach(user => console.log(user));
}
```

#### Complete Async/Await Example

```javascript
// Simulated API functions
function delay(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function fetchUser(id) {
    await delay(1000);
    return { id, name: "User " + id };
}

async function fetchUserPosts(userId) {
    await delay(1000);
    return [
        { id: 1, title: "Post 1", userId },
        { id: 2, title: "Post 2", userId }
    ];
}

async function fetchPostComments(postId) {
    await delay(500);
    return [
        { id: 1, text: "Comment 1", postId },
        { id: 2, text: "Comment 2", postId }
    ];
}

// Main function using async/await
async function getUserData(userId) {
    console.log("Fetching user data...");

    try {
        // Get user
        const user = await fetchUser(userId);
        console.log("User:", user);

        // Get user's posts
        const posts = await fetchUserPosts(user.id);
        console.log("Posts:", posts);

        // Get comments for all posts (parallel)
        const commentsPromises = posts.map(post =>
            fetchPostComments(post.id)
        );
        const allComments = await Promise.all(commentsPromises);
        console.log("Comments:", allComments.flat());

        return {
            user,
            posts,
            comments: allComments.flat()
        };
    } catch (error) {
        console.error("Error:", error);
        throw error;
    }
}

// Execute
getUserData(1).then(data => {
    console.log("Complete data:", data);
});
```

---

## 7.5 JSON and AJAX

### What is JSON?

JSON (JavaScript Object Notation) is a lightweight data-interchange format that is easy for humans to read and write, and easy for machines to parse and generate.

#### JSON Syntax Rules

- Data is in name/value pairs
- Data is separated by commas
- Curly braces `{}` hold objects
- Square brackets `[]` hold arrays
- Strings must be in double quotes

```json
{
    "name": "John Doe",
    "age": 30,
    "isStudent": false,
    "courses": ["JavaScript", "HTML", "CSS"],
    "address": {
        "city": "Kathmandu",
        "country": "Nepal"
    },
    "spouse": null
}
```

#### JSON Data Types

| Type | Example |
|------|---------|
| String | `"Hello"` |
| Number | `42`, `3.14` |
| Boolean | `true`, `false` |
| Null | `null` |
| Array | `[1, 2, 3]` |
| Object | `{"key": "value"}` |

> **Note:** JSON does not support functions, undefined, or comments.

### Working with JSON in JavaScript

#### JSON.stringify()

Convert JavaScript object to JSON string.

```javascript
const user = {
    name: "John",
    age: 30,
    hobbies: ["reading", "gaming"],
    isActive: true
};

// Basic stringification
const jsonString = JSON.stringify(user);
console.log(jsonString);
// '{"name":"John","age":30,"hobbies":["reading","gaming"],"isActive":true}'

// Pretty print with indentation
const prettyJson = JSON.stringify(user, null, 2);
console.log(prettyJson);
/*
{
  "name": "John",
  "age": 30,
  "hobbies": [
    "reading",
    "gaming"
  ],
  "isActive": true
}
*/

// With replacer function (filter/transform)
const filtered = JSON.stringify(user, ["name", "age"]);
console.log(filtered);  // '{"name":"John","age":30}'

// With replacer function
const transformed = JSON.stringify(user, (key, value) => {
    if (typeof value === "string") {
        return value.toUpperCase();
    }
    return value;
});
```

#### JSON.parse()

Convert JSON string to JavaScript object.

```javascript
const jsonString = '{"name":"John","age":30,"isActive":true}';

// Basic parsing
const user = JSON.parse(jsonString);
console.log(user.name);  // "John"
console.log(user.age);   // 30

// With reviver function (transform values)
const jsonWithDate = '{"name":"John","birthDate":"1990-05-15"}';
const userWithDate = JSON.parse(jsonWithDate, (key, value) => {
    if (key === "birthDate") {
        return new Date(value);
    }
    return value;
});
console.log(userWithDate.birthDate);  // Date object

// Error handling
try {
    const invalid = JSON.parse("invalid json");
} catch (error) {
    console.log("JSON parsing error:", error.message);
}
```

#### Deep Clone with JSON

```javascript
const original = {
    name: "John",
    address: {
        city: "Kathmandu",
        country: "Nepal"
    }
};

// Deep clone (works for JSON-compatible data)
const clone = JSON.parse(JSON.stringify(original));

clone.address.city = "Pokhara";
console.log(original.address.city);  // "Kathmandu" (unchanged)
console.log(clone.address.city);     // "Pokhara"
```

---

### AJAX (Asynchronous JavaScript and XML)

AJAX allows web pages to exchange data with servers without reloading the page.

### XMLHttpRequest (Traditional Method)

```javascript
// GET request
function getData() {
    const xhr = new XMLHttpRequest();

    xhr.open("GET", "https://api.example.com/users", true);

    xhr.onreadystatechange = function() {
        if (xhr.readyState === 4) {  // Request complete
            if (xhr.status === 200) {  // Success
                const data = JSON.parse(xhr.responseText);
                console.log("Data:", data);
            } else {
                console.log("Error:", xhr.status);
            }
        }
    };

    xhr.onerror = function() {
        console.log("Network error");
    };

    xhr.send();
}

// POST request
function postData(userData) {
    const xhr = new XMLHttpRequest();

    xhr.open("POST", "https://api.example.com/users", true);
    xhr.setRequestHeader("Content-Type", "application/json");

    xhr.onload = function() {
        if (xhr.status === 201) {
            console.log("User created:", JSON.parse(xhr.responseText));
        } else {
            console.log("Error:", xhr.status);
        }
    };

    xhr.send(JSON.stringify(userData));
}

postData({ name: "John", email: "john@example.com" });
```

#### XMLHttpRequest States

| readyState | State | Description |
|------------|-------|-------------|
| 0 | UNSENT | Request not initialized |
| 1 | OPENED | Connection established |
| 2 | HEADERS_RECEIVED | Request received |
| 3 | LOADING | Processing request |
| 4 | DONE | Request finished |

---

### Fetch API (Modern Method)

The Fetch API provides a cleaner, promise-based way to make HTTP requests.

#### Basic GET Request

```javascript
fetch("https://api.example.com/users")
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log("Users:", data);
    })
    .catch(error => {
        console.log("Error:", error);
    });
```

#### GET with Async/Await

```javascript
async function getUsers() {
    try {
        const response = await fetch("https://api.example.com/users");

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        const users = await response.json();
        console.log("Users:", users);
        return users;
    } catch (error) {
        console.log("Error:", error);
    }
}

getUsers();
```

#### POST Request

```javascript
async function createUser(userData) {
    try {
        const response = await fetch("https://api.example.com/users", {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify(userData)
        });

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        const newUser = await response.json();
        console.log("Created user:", newUser);
        return newUser;
    } catch (error) {
        console.log("Error:", error);
    }
}

createUser({
    name: "John Doe",
    email: "john@example.com"
});
```

#### Other HTTP Methods

```javascript
// PUT - Update entire resource
async function updateUser(id, userData) {
    const response = await fetch(`https://api.example.com/users/${id}`, {
        method: "PUT",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(userData)
    });
    return response.json();
}

// PATCH - Partial update
async function patchUser(id, updates) {
    const response = await fetch(`https://api.example.com/users/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(updates)
    });
    return response.json();
}

// DELETE
async function deleteUser(id) {
    const response = await fetch(`https://api.example.com/users/${id}`, {
        method: "DELETE"
    });
    return response.ok;
}
```

#### Fetch Options

```javascript
const response = await fetch(url, {
    method: "POST",                           // HTTP method
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer token123"
    },
    body: JSON.stringify(data),               // Request body
    mode: "cors",                             // cors, no-cors, same-origin
    cache: "no-cache",                        // default, no-cache, reload, force-cache
    credentials: "same-origin",               // include, same-origin, omit
    redirect: "follow",                       // manual, follow, error
    referrerPolicy: "no-referrer"             // Referrer policy
});
```

#### Response Object

```javascript
const response = await fetch(url);

// Response properties
console.log(response.ok);           // true if status 200-299
console.log(response.status);       // HTTP status code (200, 404, etc.)
console.log(response.statusText);   // Status message
console.log(response.headers);      // Response headers
console.log(response.url);          // Final URL

// Reading response body (can only read once!)
const json = await response.json();    // Parse as JSON
const text = await response.text();    // Parse as text
const blob = await response.blob();    // Parse as Blob
const formData = await response.formData();  // Parse as FormData
const buffer = await response.arrayBuffer(); // Parse as ArrayBuffer
```

#### Working with Headers

```javascript
// Reading response headers
const response = await fetch(url);
console.log(response.headers.get("Content-Type"));
console.log(response.headers.get("Date"));

// Iterate headers
for (let [key, value] of response.headers) {
    console.log(`${key}: ${value}`);
}

// Creating request headers
const headers = new Headers();
headers.append("Content-Type", "application/json");
headers.append("Authorization", "Bearer token");

fetch(url, { headers });
```

#### Complete AJAX Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>AJAX Example</title>
</head>
<body>
    <h1>User List</h1>
    <button id="loadUsers">Load Users</button>
    <div id="userList"></div>

    <h2>Add User</h2>
    <input type="text" id="userName" placeholder="Name">
    <input type="email" id="userEmail" placeholder="Email">
    <button id="addUser">Add User</button>

    <script>
        const API_URL = "https://jsonplaceholder.typicode.com/users";
        const userList = document.getElementById("userList");

        // Load users
        document.getElementById("loadUsers").addEventListener("click", async () => {
            userList.innerHTML = "Loading...";

            try {
                const response = await fetch(API_URL);
                const users = await response.json();

                userList.innerHTML = users.map(user => `
                    <div style="border: 1px solid #ccc; padding: 10px; margin: 5px;">
                        <strong>${user.name}</strong><br>
                        Email: ${user.email}<br>
                        City: ${user.address.city}
                    </div>
                `).join("");
            } catch (error) {
                userList.innerHTML = "Error loading users: " + error.message;
            }
        });

        // Add user
        document.getElementById("addUser").addEventListener("click", async () => {
            const name = document.getElementById("userName").value;
            const email = document.getElementById("userEmail").value;

            if (!name || !email) {
                alert("Please fill in all fields");
                return;
            }

            try {
                const response = await fetch(API_URL, {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({ name, email })
                });

                const newUser = await response.json();
                alert(`User created with ID: ${newUser.id}`);

                // Clear inputs
                document.getElementById("userName").value = "";
                document.getElementById("userEmail").value = "";
            } catch (error) {
                alert("Error creating user: " + error.message);
            }
        });
    </script>
</body>
</html>
```

---

## 7.6 ES6 and Modern JavaScript

ES6 (ECMAScript 2015) introduced many new features that made JavaScript more powerful and easier to write.

### 1. let and const

Block-scoped variable declarations.

```javascript
// let - reassignable, block-scoped
let count = 0;
count = 1;  // OK

// const - not reassignable, block-scoped
const PI = 3.14159;
// PI = 3.14;  // Error!

// const with objects/arrays (reference is constant, not value)
const user = { name: "John" };
user.name = "Jane";  // OK - modifying property
// user = {};  // Error - can't reassign

const numbers = [1, 2, 3];
numbers.push(4);  // OK - modifying array
// numbers = [];  // Error - can't reassign
```

### 2. Arrow Functions

Shorter syntax for function expressions.

```javascript
// Traditional function
function add(a, b) {
    return a + b;
}

// Arrow function
const add = (a, b) => {
    return a + b;
};

// Implicit return (single expression)
const add = (a, b) => a + b;

// Single parameter (parentheses optional)
const square = x => x * x;

// No parameters
const greet = () => "Hello!";

// Returning object (wrap in parentheses)
const createUser = (name, age) => ({ name, age });

// Arrow functions and 'this'
const obj = {
    name: "John",
    // Traditional - has own 'this'
    traditionalGreet: function() {
        console.log("Hello, " + this.name);
    },
    // Arrow - inherits 'this' from parent scope
    arrowGreet: () => {
        console.log("Hello, " + this.name);  // 'this' is not obj!
    }
};
```

### 3. Template Literals

String interpolation and multi-line strings.

```javascript
const name = "John";
const age = 30;

// String interpolation
const message = `Hello, ${name}! You are ${age} years old.`;

// Multi-line strings
const html = `
    <div class="user">
        <h2>${name}</h2>
        <p>Age: ${age}</p>
    </div>
`;

// Expressions in templates
const price = 100;
const tax = 0.1;
console.log(`Total: $${price * (1 + tax)}`);  // "Total: $110"

// Tagged templates
function highlight(strings, ...values) {
    return strings.reduce((result, str, i) => {
        return `${result}${str}<mark>${values[i] || ""}</mark>`;
    }, "");
}

const highlighted = highlight`Hello ${name}, you are ${age}!`;
```

### 4. Destructuring

Extract values from arrays and objects.

```javascript
// Array destructuring
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;
console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]

// Skip elements
const [a, , c] = numbers;  // a=1, c=3

// Default values
const [x = 0, y = 0] = [1];  // x=1, y=0

// Swapping variables
let m = 1, n = 2;
[m, n] = [n, m];  // m=2, n=1

// Object destructuring
const user = {
    name: "John",
    age: 30,
    city: "Kathmandu"
};

const { name, age, city } = user;
console.log(name);  // "John"

// Rename variables
const { name: userName, age: userAge } = user;
console.log(userName);  // "John"

// Default values
const { name, country = "Nepal" } = user;

// Nested destructuring
const person = {
    name: "John",
    address: {
        city: "Kathmandu",
        zip: "44600"
    }
};
const { address: { city, zip } } = person;

// Function parameter destructuring
function greet({ name, age }) {
    console.log(`Hello ${name}, you are ${age}`);
}
greet(user);
```

### 5. Spread Operator (...)

Expand iterables into individual elements.

```javascript
// Array spread
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];  // [1, 2, 3, 4, 5, 6]

// Copy array
const copy = [...arr1];

// Add elements
const extended = [0, ...arr1, 4];  // [0, 1, 2, 3, 4]

// Object spread
const user = { name: "John", age: 30 };
const userWithCity = { ...user, city: "Kathmandu" };

// Merge objects
const defaults = { theme: "light", lang: "en" };
const settings = { theme: "dark" };
const merged = { ...defaults, ...settings };  // { theme: "dark", lang: "en" }

// Function arguments
const numbers = [1, 2, 3];
console.log(Math.max(...numbers));  // 3
```

### 6. Rest Parameters

Collect remaining arguments into an array.

```javascript
// Rest parameters
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3));        // 6
console.log(sum(1, 2, 3, 4, 5));  // 15

// Combine with regular parameters
function greet(greeting, ...names) {
    names.forEach(name => {
        console.log(`${greeting}, ${name}!`);
    });
}

greet("Hello", "John", "Jane", "Bob");
```

### 7. Default Parameters

Set default values for function parameters.

```javascript
function greet(name = "Guest", greeting = "Hello") {
    return `${greeting}, ${name}!`;
}

console.log(greet());              // "Hello, Guest!"
console.log(greet("John"));        // "Hello, John!"
console.log(greet("John", "Hi"));  // "Hi, John!"

// Default with destructuring
function createUser({ name = "Anonymous", age = 0 } = {}) {
    return { name, age };
}

console.log(createUser());                    // { name: "Anonymous", age: 0 }
console.log(createUser({ name: "John" }));    // { name: "John", age: 0 }
```

### 8. Enhanced Object Literals

Shorter syntax for object properties and methods.

```javascript
const name = "John";
const age = 30;

// Shorthand property names
const user = { name, age };  // Same as { name: name, age: age }

// Shorthand methods
const calculator = {
    add(a, b) {
        return a + b;
    },
    subtract(a, b) {
        return a - b;
    }
};

// Computed property names
const propName = "dynamicKey";
const obj = {
    [propName]: "value",
    ["key" + 1]: "value1"
};
console.log(obj.dynamicKey);  // "value"
console.log(obj.key1);        // "value1"
```

### 9. Classes

Modern syntax for constructor functions and prototypes.

```javascript
class Person {
    // Constructor
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    // Instance method
    greet() {
        return `Hello, I'm ${this.name}`;
    }

    // Getter
    get info() {
        return `${this.name}, ${this.age} years old`;
    }

    // Setter
    set info(value) {
        [this.name, this.age] = value.split(", ");
    }

    // Static method
    static createAnonymous() {
        return new Person("Anonymous", 0);
    }
}

const person = new Person("John", 30);
console.log(person.greet());  // "Hello, I'm John"
console.log(person.info);     // "John, 30 years old"

// Static method
const anon = Person.createAnonymous();

// Inheritance
class Student extends Person {
    constructor(name, age, grade) {
        super(name, age);  // Call parent constructor
        this.grade = grade;
    }

    greet() {
        return `${super.greet()}, I'm in grade ${this.grade}`;
    }

    study() {
        return `${this.name} is studying`;
    }
}

const student = new Student("Jane", 15, 10);
console.log(student.greet());  // "Hello, I'm Jane, I'm in grade 10"
console.log(student.study());  // "Jane is studying"
```

### 10. Modules (Import/Export)

Organize code into reusable modules.

**math.js (exporting):**
```javascript
// Named exports
export const PI = 3.14159;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

// Default export (one per module)
export default class Calculator {
    add(a, b) { return a + b; }
    subtract(a, b) { return a - b; }
}
```

**main.js (importing):**
```javascript
// Import named exports
import { PI, add, subtract } from './math.js';

// Import with alias
import { add as sum } from './math.js';

// Import all named exports
import * as math from './math.js';
console.log(math.PI);
console.log(math.add(1, 2));

// Import default export
import Calculator from './math.js';

// Import both default and named
import Calculator, { PI, add } from './math.js';

// Dynamic import (returns Promise)
async function loadModule() {
    const math = await import('./math.js');
    console.log(math.add(1, 2));
}
```

**HTML (using modules):**
```html
<script type="module" src="main.js"></script>
```

### 11. Other ES6+ Features

```javascript
// for...of loop
const array = [1, 2, 3];
for (const value of array) {
    console.log(value);
}

// Map
const map = new Map();
map.set("key1", "value1");
map.set("key2", "value2");
console.log(map.get("key1"));  // "value1"
console.log(map.size);          // 2

// Set
const set = new Set([1, 2, 2, 3, 3]);
console.log(set);  // Set { 1, 2, 3 }
set.add(4);
set.has(2);  // true
set.delete(1);

// Symbol
const sym = Symbol("description");
const obj = {
    [sym]: "value"
};

// Optional chaining (?.)
const user = { address: { city: "Kathmandu" } };
console.log(user?.address?.city);    // "Kathmandu"
console.log(user?.contact?.phone);   // undefined (no error)

// Nullish coalescing (??)
const value = null ?? "default";  // "default"
const zero = 0 ?? "default";      // 0

// Array methods
const nums = [1, 2, 3, 4, 5];
nums.find(n => n > 3);      // 4
nums.findIndex(n => n > 3); // 3
nums.includes(3);            // true
[1, [2, [3]]].flat(2);      // [1, 2, 3]
```

---

## 7.7 JavaScript Libraries

JavaScript libraries and frameworks help developers build applications more efficiently by providing pre-written code for common tasks.

### jQuery

jQuery is a fast, small, and feature-rich JavaScript library that simplifies HTML document traversal, event handling, and AJAX.

#### Including jQuery

```html
<!-- From CDN -->
<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>

<!-- Or download and include locally -->
<script src="js/jquery.min.js"></script>
```

#### jQuery Basics

```javascript
// Document ready
$(document).ready(function() {
    // Code runs when DOM is ready
});

// Shorthand
$(function() {
    // Same as above
});

// Selecting elements
$("p")           // All paragraphs
$(".class")      // By class
$("#id")         // By ID
$("div.intro")   // div with class intro
$("ul li:first") // First li in ul
```

#### DOM Manipulation with jQuery

```javascript
// Get/Set content
$("#demo").html();              // Get HTML
$("#demo").html("<b>Bold</b>"); // Set HTML
$("#demo").text();              // Get text
$("#demo").text("Hello");       // Set text

// Get/Set attributes
$("img").attr("src");                    // Get attribute
$("img").attr("src", "new-image.jpg");   // Set attribute
$("input").val();                        // Get value
$("input").val("New value");             // Set value

// CSS
$("p").css("color");                     // Get CSS property
$("p").css("color", "red");              // Set CSS property
$("p").css({                              // Set multiple
    "color": "red",
    "font-size": "20px"
});

// Classes
$("p").addClass("highlight");
$("p").removeClass("highlight");
$("p").toggleClass("highlight");
$("p").hasClass("highlight");

// Show/Hide
$("p").hide();
$("p").show();
$("p").toggle();
$("p").fadeIn();
$("p").fadeOut();
$("p").slideUp();
$("p").slideDown();
```

#### Events with jQuery

```javascript
// Click
$("button").click(function() {
    alert("Clicked!");
});

// Other events
$("input").focus(function() { });
$("input").blur(function() { });
$("input").change(function() { });
$("form").submit(function(e) {
    e.preventDefault();
});

// Event delegation
$("ul").on("click", "li", function() {
    $(this).toggleClass("selected");
});

// Multiple events
$("p").on({
    mouseenter: function() {
        $(this).css("background-color", "yellow");
    },
    mouseleave: function() {
        $(this).css("background-color", "white");
    }
});
```

#### AJAX with jQuery

```javascript
// GET request
$.get("https://api.example.com/data", function(data) {
    console.log(data);
});

// POST request
$.post("https://api.example.com/users", {
    name: "John",
    email: "john@example.com"
}, function(response) {
    console.log(response);
});

// Full AJAX
$.ajax({
    url: "https://api.example.com/data",
    method: "GET",
    dataType: "json",
    success: function(data) {
        console.log("Success:", data);
    },
    error: function(xhr, status, error) {
        console.log("Error:", error);
    },
    complete: function() {
        console.log("Request complete");
    }
});

// Load HTML into element
$("#result").load("content.html");

// getJSON
$.getJSON("https://api.example.com/data", function(data) {
    console.log(data);
});
```

#### jQuery Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>jQuery Example</title>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
    <style>
        .highlight { background-color: yellow; }
        .item { padding: 10px; margin: 5px; border: 1px solid #ccc; }
    </style>
</head>
<body>
    <h1>Todo List</h1>
    <input type="text" id="todoInput" placeholder="Enter task">
    <button id="addBtn">Add</button>
    <ul id="todoList"></ul>

    <script>
        $(function() {
            // Add task
            $("#addBtn").click(function() {
                const task = $("#todoInput").val().trim();
                if (task) {
                    const li = $("<li>").addClass("item")
                        .html(`${task} <button class="deleteBtn">Delete</button>`);
                    $("#todoList").append(li);
                    $("#todoInput").val("");
                }
            });

            // Add on Enter
            $("#todoInput").keypress(function(e) {
                if (e.which === 13) {
                    $("#addBtn").click();
                }
            });

            // Delete task (event delegation)
            $("#todoList").on("click", ".deleteBtn", function() {
                $(this).parent().fadeOut(function() {
                    $(this).remove();
                });
            });

            // Toggle highlight
            $("#todoList").on("click", "li", function(e) {
                if (!$(e.target).is("button")) {
                    $(this).toggleClass("highlight");
                }
            });
        });
    </script>
</body>
</html>
```

---

### Introduction to Modern Frameworks

Modern JavaScript frameworks provide structured ways to build complex web applications.

#### React

A library for building user interfaces using components.

```javascript
// React component
function Welcome(props) {
    return <h1>Hello, {props.name}!</h1>;
}

// Using state (Hooks)
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}
```

**Key Features:**
- Component-based architecture
- Virtual DOM for efficient updates
- JSX syntax
- One-way data flow
- Large ecosystem (React Router, Redux)

#### Angular

A full-featured framework for building large-scale applications.

```typescript
// Angular component
import { Component } from '@angular/core';

@Component({
    selector: 'app-hello',
    template: `
        <h1>Hello, {{ name }}!</h1>
        <button (click)="sayHello()">Click me</button>
    `
})
export class HelloComponent {
    name = 'World';

    sayHello() {
        alert(`Hello, ${this.name}!`);
    }
}
```

**Key Features:**
- Full MVC framework
- TypeScript-based
- Two-way data binding
- Dependency injection
- CLI for development

#### Vue.js

A progressive framework that's easy to learn and integrate.

```javascript
// Vue component
const app = Vue.createApp({
    data() {
        return {
            message: 'Hello Vue!',
            count: 0
        }
    },
    methods: {
        increment() {
            this.count++;
        }
    },
    template: `
        <div>
            <h1>{{ message }}</h1>
            <p>Count: {{ count }}</p>
            <button @click="increment">Increment</button>
        </div>
    `
});

app.mount('#app');
```

**Key Features:**
- Easy to learn
- Virtual DOM
- Component-based
- Two-way data binding
- Single-file components

### Framework Comparison

| Feature | React | Angular | Vue.js |
|---------|-------|---------|--------|
| **Type** | Library | Framework | Framework |
| **Language** | JavaScript/JSX | TypeScript | JavaScript |
| **Data Binding** | One-way | Two-way | Two-way |
| **DOM** | Virtual | Incremental | Virtual |
| **Learning Curve** | Moderate | Steep | Easy |
| **Size** | Small | Large | Small |
| **Best For** | UI components | Enterprise apps | Beginners, SPAs |

### When to Use What?

| Scenario | Recommendation |
|----------|----------------|
| Simple DOM manipulation | Vanilla JS or jQuery |
| Small interactive features | jQuery or Vue.js |
| Large single-page application | React, Angular, or Vue.js |
| Enterprise application | Angular |
| Component library | React |
| Quick prototyping | Vue.js |

---

## Summary

### Key Topics Covered

| # | Topic | Description |
|---|-------|-------------|
| 1 | **Scope and Closures** | Variable visibility, scope chain, closures for data privacy |
| 2 | **Error Handling** | try-catch-finally, throw, custom errors, debugging techniques |
| 3 | **DOM Manipulation** | Selecting, modifying, creating elements; event handling |
| 4 | **Asynchronous JavaScript** | Callbacks, Promises, async/await |
| 5 | **JSON and AJAX** | JSON parsing/stringify, fetch API, XMLHttpRequest |
| 6 | **ES6+ Features** | let/const, arrow functions, destructuring, classes, modules |
| 7 | **JavaScript Libraries** | jQuery basics, introduction to React, Angular, Vue.js |

---

## Practice Exercises

### Exercise 1: Closure Counter

Create a counter using closures with increment, decrement, and reset methods.

```javascript
function createCounter(initialValue = 0) {
    // Your code here
}

const counter = createCounter(10);
console.log(counter.increment()); // 11
console.log(counter.increment()); // 12
console.log(counter.decrement()); // 11
console.log(counter.reset());     // 10
```

### Exercise 2: Error Handling

Write a function that validates user input and throws appropriate errors.

```javascript
function validateUser(user) {
    // Validate: name (required, string), age (required, number, 0-120), email (required, valid format)
    // Throw appropriate errors for each validation failure
}

// Test with try-catch
try {
    validateUser({ name: "", age: -5, email: "invalid" });
} catch (error) {
    console.log(error.message);
}
```

### Exercise 3: DOM Todo List

Create a complete todo list with:
- Add new tasks
- Mark tasks as complete
- Delete tasks
- Filter tasks (all, active, completed)
- Store tasks in localStorage

```html
<!-- Your HTML and JavaScript here -->
```

### Exercise 4: Fetch API

Create functions to interact with a REST API.

```javascript
const API_URL = "https://jsonplaceholder.typicode.com";

// Implement these async functions:
async function getUsers() { }
async function getUserById(id) { }
async function createUser(userData) { }
async function updateUser(id, userData) { }
async function deleteUser(id) { }

// Test your functions
```

### Exercise 5: ES6 Refactoring

Refactor this code using ES6 features:

```javascript
// Before (ES5)
var people = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 },
    { name: "Bob", age: 35 }
];

function getNames(people) {
    var names = [];
    for (var i = 0; i < people.length; i++) {
        names.push(people[i].name);
    }
    return names;
}

function getAdults(people) {
    var adults = [];
    for (var i = 0; i < people.length; i++) {
        if (people[i].age >= 18) {
            adults.push(people[i]);
        }
    }
    return adults;
}

function createGreeting(name, greeting) {
    if (greeting === undefined) {
        greeting = "Hello";
    }
    return greeting + ", " + name + "!";
}

// Refactor using: const/let, arrow functions, destructuring,
// template literals, array methods (map, filter), default parameters
```

### Exercise 6: Promise Chain

Create a sequence of promises that simulate:
1. User login (1 second)
2. Fetch user profile (1 second)
3. Fetch user posts (1 second)
4. Display all data

```javascript
// Implement using both Promise chains and async/await
```

### Exercise 7: jQuery Image Gallery

Create an image gallery using jQuery with:
- Thumbnail grid
- Modal popup on click
- Previous/Next navigation
- Fade transitions

```html
<!-- Your HTML, CSS, and jQuery code here -->
```

---

## References

1. **Robbins, J. N.** (2018). *Learning Web Design: A Beginner's Guide to HTML, CSS, JavaScript, and Web Graphics*. O'Reilly Media.

2. **MDN Web Docs - JavaScript Guide:**
   [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)

3. **JavaScript.info - The Modern JavaScript Tutorial:**
   [https://javascript.info/](https://javascript.info/)

4. **W3Schools JavaScript Tutorial:**
   [https://www.w3schools.com/js/](https://www.w3schools.com/js/)

5. **Eloquent JavaScript (Free Online Book):**
   [https://eloquentjavascript.net/](https://eloquentjavascript.net/)

6. **jQuery Documentation:**
   [https://api.jquery.com/](https://api.jquery.com/)

7. **React Documentation:**
   [https://react.dev/](https://react.dev/)

8. **Angular Documentation:**
   [https://angular.io/docs](https://angular.io/docs)

9. **Vue.js Documentation:**
   [https://vuejs.org/guide/](https://vuejs.org/guide/)

---

## Tips for Success

1. **Practice Regularly:** Work on small projects incorporating these advanced concepts
2. **Debug Effectively:** Learn to use browser DevTools proficiently
3. **Understand Async:** Asynchronous programming is crucial for modern web development
4. **Read Documentation:** Get comfortable with MDN and official library docs
5. **Build Projects:** Apply concepts by building real applications
6. **Stay Updated:** JavaScript evolves constantly; keep learning new features
7. **Use Version Control:** Learn Git for managing your code

---

**End of Unit 7 Notes**

*Prepared for BCSIT First Year, Semester I*
*Internet Technology (CMP 173)*
*Pokhara University*