# **JavaScript Fundamentals & Important Concepts**

---

## **1. Basic Syntax and Operations**

### **Variables**

```javascript
var name = "John"; // Global or function-scoped
let age = 30; // Block-scoped
const country = "USA"; // Block-scoped, cannot be reassigned
```

### **Data Types**

```javascript
let str = "Hello"; // String
let num = 100; // Number
let isBoolean = true; // Boolean
let nothing = null; // Null
let notDefined; // Undefined
let obj = { key: "value" }; // Object
```

### **Operators**

```javascript
let sum = 10 + 5; // Arithmetic operator
let isEqual = 10 == "10"; // true (loose equality)
let isStrictEqual = 10 === "10"; // false (strict equality)
let andCondition = true && false; // Logical AND
```

### **Conditional Statements**

```javascript
if (age >= 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}

switch (country) {
  case "USA":
    console.log("You're from the USA.");
    break;
  case "India":
    console.log("You're from India.");
    break;
  default:
    console.log("Unknown country.");
}
```

### **Loops**

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}

while (age < 35) {
  age++;
}

for (let key in obj) {
  console.log(key, obj[key]); // Iterates over object keys
}

for (let value of [1, 2, 3]) {
  console.log(value); // Iterates over array values
}
```

---

## **2. Functions**

### **Function Declaration**

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```

### **Function Expressions**

```javascript
const greet = function (name) {
  return `Hello, ${name}!`;
};
```

### **Arrow Functions**

```javascript
const greet = (name) => `Hello, ${name}!`;
```

### **Callback Functions**

```javascript
function sayHello(callback) {
  callback("Hello!");
}

sayHello((message) => console.log(message)); // Passing a function as an argument
```

### **IIFE (Immediately Invoked Function Expression)**

```javascript
(function () {
  console.log("This function runs immediately!");
})();
```

### Anonymous Functions

An anonymous function is simply a function that does  ****not have a name**** . Unlike named functions, which are declared with a name for easy reference, anonymous functions are usually created for specific tasks and are often assigned to variables or used as arguments for other functions.

In JavaScript, you normally use the ****function keyword followed by a name**** to declare a function. However, in an anonymous function, the name is  ****omitted**** . These functions are often used in situations where you don’t need to reuse the function outside its immediate context.

### ****Syntax****

The below-enlightened syntax illustrates the declaration of an anonymous function using the normal declaration:

```
function() {
    // Function Body
 }
```

We may also declare an anonymous function using the arrow function technique which is shown below:

```
( () => {
    // Function Body...
} )();
```

---

## **3. Objects**

### **Object Literals**

```javascript
let person = {
  name: "Alice",
  age: 25,
  greet: function () {
    console.log(`Hello, I'm ${this.name}`);
  },
};
person.greet();
```

### **Accessing Properties**

```javascript
console.log(person.name); // Dot notation
console.log(person["age"]); // Bracket notation
```

### **Object Methods**

```javascript
person.greet = function () {
  console.log(`Hi, my name is ${this.name}`);
};
person.greet();
```

### **`this` Keyword**

```javascript
const user = {
  name: "Sam",
  showThis: function () {
    console.log(this); // Points to the object 'user'
  },
};
user.showThis();
```

---

## **4. Arrays**

### **Array Creation**

```javascript
let numbers = [1, 2, 3];
```

### **Array Methods**

```javascript
numbers.push(4); // [1, 2, 3, 4]
numbers.pop(); // [1, 2, 3]
numbers.splice(1, 1); // Removes 1 element at index 1: [1, 3]
```

### **Array Iteration**

```javascript
numbers.forEach((num) => console.log(num)); // Iterating using forEach

let doubled = numbers.map((num) => num * 2); // Transforming each item
```

---

## **5. Scope**

### **Global Scope**

```javascript
var globalVar = "I'm global!";
```

### **Local/Function Scope**

```javascript
function myFunction() {
  var localVar = "I'm local!";
  console.log(localVar); // Accessible here
}
console.log(localVar); // Not accessible here
```

### **Block Scope (`let`, `const`)**

```javascript
if (true) {
  let blockScoped = "I'm block-scoped!";
  console.log(blockScoped); // Accessible here
}
console.log(blockScoped); // Not accessible here
```

### **Closures**

```javascript
function outerFunction() {
  let outerVar = "I'm outside!";

  return function innerFunction() {
    console.log(outerVar); // Inner function retains access to outerVar
  };
}
const closureExample = outerFunction();
closureExample();
```

---

## **6. Hoisting**

### **Variable Hoisting**

```javascript
console.log(x); // undefined, due to hoisting
var x = 5;

console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
```

### **Function Hoisting**

```javascript
sayHello(); // Works due to hoisting
function sayHello() {
  console.log("Hello!");
}
```

---

## **7. Asynchronous JavaScript**

### **Callbacks**

```javascript
function asyncTask(callback) {
  setTimeout(() => {
    console.log("Task completed");
    callback();
  }, 1000);
}

asyncTask(() => console.log("Callback executed"));
```

### **Promises**

```javascript
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 1000);
});

promise
  .then((result) => console.log(result)) // Logs "Success!"
  .catch((error) => console.log(error));
```

### **Async/Await**

```javascript
async function fetchData() {
  let result = await fetch("https://api.example.com/data");
  let data = await result.json();
  console.log(data);
}
```

### **Event Loop & Microtasks**

```javascript
console.log("Start");

setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");

// Order: "Start", "End", "Promise", "Timeout"
```

---

## **8. Event Handling**

```javascript
document.getElementById("myButton").addEventListener("click", () => {
  console.log("Button clicked!");
});
```

---

## **9. Error Handling**

### **`try-catch-finally` Block**

```javascript
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.error(error.message);
} finally {
  console.log("This runs regardless of success or failure");
}
```

---

## **10. DOM Manipulation**

### **Selecting Elements**

```javascript
let element = document.getElementById("myElement");
```

### **Manipulating Elements**

```javascript
element.textContent = "Updated text!";
element.classList.add("new-class");
element.style.color = "red";
```

### **Creating and Appending Elements**

```javascript
let newElement = document.createElement("div");
newElement.textContent = "I'm a new element!";
document.body.appendChild(newElement);
```

---

## **11. Object-Oriented JavaScript**

### **Constructor Functions**

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

Car.prototype.getDetails = function () {
  return `${this.make} ${this.model}`;
};

let myCar = new Car("Toyota", "Corolla");
console.log(myCar.getDetails());
```

### **ES6 Classes**

```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  getDetails() {
    return `${this.make} ${this.model}`;
  }
}

let myCar = new Car("Honda", "Civic");
console.log(myCar.getDetails());
```

---

## **12. ES6+ Features**

### **Let/Const**

```javascript
let mutable = "This can change";
const immutable = "This cannot change";
```

### **Template Literals**

```javascript
let name = "Alice";
console.log(`Hello, ${name}!`);
```

### **Destructuring**

```javascript
let [a, b] = [1, 2];
let { name, age } = { name: "Alice", age: 25 };
```

### **Spread and Rest Operators**

```javascript
let arr = [1, 2, 3];
let newArr = [...arr, 4, 5]; // [1, 2, 3, 4, 5]

function sum(...args) {
  return args.reduce((acc, curr) => acc + curr, 0);
}
```

### **Modules**

```javascript
// In file1.js
export const myVar = 42;

// In file2.js
import { myVar } from "./file1.js";
```

---

## **13. JSON (JavaScript Object Notation)**

### **Parsing JSON**

```javascript
let jsonString = '{"name":"Alice", "age":25}';
let obj = JSON.parse(jsonString);
console.log(obj.name);
```

### **Stringifying JSON**

```javascript
let person = { name: "Alice", age: 25 };
let jsonString = JSON.stringify(person);
console.log(jsonString);
```

---

## **14. Higher-Order Functions**

```javascript
function applyOperation(arr, operation) {
  return arr.map(operation);
}

let result = applyOperation([1, 2, 3], (x) => x * 2);
console.log(result); // [2, 4, 6]
```

---

## **15. Closures**

```javascript
function outer() {
  let counter = 0;
  return function () {
    counter++;
    console.log(counter);
  };
}

const increment = outer();
increment(); // 1
increment(); // 2
```

---

## **16. `this` Keyword**

### **Global Context**

```javascript
console.log(this); // Refers to the global object (window in browsers)
```

### **Object Method Context**

```javascript
let person = {
  name: "Alice",
  greet() {
    console.log(this.name); // Refers to 'person' object
  },
};
person.greet();
```

### **Arrow Functions and `this`**

```javascript
const obj = {
  regularFunction: function () {
    console.log(this); // Refers to obj
  },
  arrowFunction: () => {
    console.log(this); // Refers to the global object, not obj
  },
};
obj.regularFunction();
obj.arrowFunction();
```

---

## **17. Prototypes and Inheritance**

### **Prototype Chain**

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function () {
  console.log(`${this.name} makes a sound`);
};

let dog = new Animal("Dog");
dog.speak(); // Dog makes a sound
console.log(dog.__proto__ === Animal.prototype); // true
```

### **Inheritance in ES5**

```javascript
function Dog(name, breed) {
  Animal.call(this, name); // Inherit properties
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype); // Inherit methods
Dog.prototype.constructor = Dog;

Dog.prototype.speak = function () {
  console.log(`${this.name} barks`);
};

let beagle = new Dog("Snoopy", "Beagle");
beagle.speak(); // Snoopy barks
```

### **ES6 Class Inheritance**

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call parent constructor
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks`);
  }
}

let myDog = new Dog("Max", "Labrador");
myDog.speak(); // Max barks
```

---

## **18. Currying and Partial Application**

### **Currying**

```javascript
function add(a) {
  return function (b) {
    return a + b;
  };
}

let addFive = add(5);
console.log(addFive(3)); // 8
```

### **Partial Application**

```javascript
function multiply(a, b) {
  return a * b;
}

let double = multiply.bind(null, 2); // Partially apply 2 as the first argument
console.log(double(5)); // 10
```

---

## **19. Regular Expressions (RegEx)**

```javascript
let regex = /hello/i; // Case-insensitive match for 'hello'
console.log(regex.test("Hello")); // true
console.log("Hello world".match(regex)); // ['Hello']
```

---

## **20. Memory Management**

### **Garbage Collection**

JavaScript automatically manages memory. It frees memory that is no longer in use via **Garbage Collection**, which works by identifying objects no longer referenced by the program and deallocating the memory they occupy.

---

## **21. Best Practices**

- **Use `let` and `const` over `var`** for block-scoped variables.
- **Keep functions pure** where possible (no side effects).
- **Avoid global variables** to prevent namespace pollution.
- **Use meaningful variable names**.
- **Immutability**: Use `const` for variables that won’t be reassigned.
- **Write modular and reusable code**.

---

## **22. Event Delegation**

**Event delegation** is a technique where you add a single event listener to a parent element to handle events on its child elements. This is useful when dynamically adding or removing elements, as you don't need to attach separate event listeners to each child.

### **Example**

```html
<ul id="parentList">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

<script>
  document.getElementById("parentList").addEventListener("click", function (e) {
    if (e.target && e.target.nodeName === "LI") {
      console.log("List item clicked:", e.target.textContent);
    }
  });
</script>
```

**Explanation:** The event listener is added to the `ul` element (parent). When any `li` element (child) is clicked, it will be handled by the event listener using event delegation.

---

## **23. Event Propagation**

**Event propagation** is how events travel through the DOM tree. It has two main phases:

1. **Capturing Phase** (Event travels down to the target).
2. **Bubbling Phase** (Event bubbles back up from the target).

### **Example**

```html
<div id="outer">
  <div id="inner">Click Me!</div>
</div>

<script>
  document.getElementById("outer").addEventListener(
    "click",
    () => {
      console.log("Outer DIV clicked");
    },
    false
  ); // Bubbling phase

  document.getElementById("inner").addEventListener(
    "click",
    () => {
      console.log("Inner DIV clicked");
    },
    false
  ); // Bubbling phase
</script>
```

**Explanation:** If you click on the `#inner` div, it will first trigger the event on `#inner`, then propagate to the `#outer` div in the **bubbling phase**. Setting the third argument to `true` will instead listen in the **capturing phase**.

---

## **24. Stopping Propagation**

You can stop an event from propagating further by using `stopPropagation()`.

### **Example**

```html
<div id="outer">
  <div id="inner">Click Me!</div>
</div>

<script>
  document.getElementById("outer").addEventListener(
    "click",
    () => {
      console.log("Outer DIV clicked");
    },
    false
  );

  document.getElementById("inner").addEventListener(
    "click",
    (e) => {
      console.log("Inner DIV clicked");
      e.stopPropagation(); // Stops the event from propagating to the outer div
    },
    false
  );
</script>
```

**Explanation:** Clicking the `#inner` div will only log "Inner DIV clicked" because `e.stopPropagation()` prevents the event from bubbling up to `#outer`.

---

## **25. `event.preventDefault()`**

This method prevents the default action associated with an event (such as following a link or submitting a form).

### **Example**

```html
<a href="https://example.com" id="link">Click me</a>

<script>
  document.getElementById("link").addEventListener("click", (e) => {
    e.preventDefault(); // Prevents the default link navigation
    console.log("Link click prevented");
  });
</script>
```

**Explanation:** Clicking the link will no longer navigate to the URL, and instead, it will just log a message in the console.

---

## **26. Throttling and Debouncing**

These techniques optimize performance by controlling how often a function is called.

### **Throttling**

Ensures a function is called at most once every specified interval.

### **Example**

```javascript
function throttle(func, delay) {
  let lastCall = 0;
  return function (...args) {
    const now = new Date().getTime();
    if (now - lastCall < delay) return;
    lastCall = now;
    return func(...args);
  };
}

window.addEventListener(
  "resize",
  throttle(() => {
    console.log("Resized");
  }, 2000)
); // Ensures the resize event is fired at most once every 2 seconds
```

### **Debouncing**

Ensures a function is called after a specified interval of inactivity.

### **Example**

```javascript
function debounce(func, delay) {
  let timeoutId;
  return function (...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => {
      func(...args);
    }, delay);
  };
}

window.addEventListener(
  "scroll",
  debounce(() => {
    console.log("Scrolled");
  }, 1000)
); // Executes the function 1 second after scrolling stops
```

---

## **27. `setTimeout` and `setInterval`**

### **`setTimeout`**

Executes a function once after a delay.

### **Example**

```javascript
setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);
```

### **`setInterval`**

Executes a function repeatedly at a fixed interval.

### **Example**

```javascript
let count = 0;
let intervalId = setInterval(() => {
  console.log(`Interval count: ${++count}`);
  if (count === 5) {
    clearInterval(intervalId); // Stop after 5 iterations
  }
}, 1000);
```

---

## **28. Event Loop**

The **event loop** is the mechanism that handles asynchronous operations in JavaScript. It checks the **call stack** and **message queue** and processes callbacks when the call stack is empty.

### **Example**

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout callback");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise callback");
});

console.log("End");
```

**Output:**

```
Start
End
Promise callback
Timeout callback
```

**Explanation:** The event loop first completes the synchronous code (`Start`, `End`), then processes microtasks (promise callbacks), and finally, the macrotasks (setTimeout callbacks).

---

## **29. Shallow vs Deep Copy**

- **Shallow Copy**: Copies only the first level of an object.
- **Deep Copy**: Copies all nested objects and arrays.

### **Shallow Copy Example**

```javascript
let original = { a: 1, b: { c: 2 } };
let shallowCopy = { ...original };
shallowCopy.b.c = 10;
console.log(original.b.c); // 10 (reference is shared)
```

### **Deep Copy Example**

```javascript
let original = { a: 1, b: { c: 2 } };
let deepCopy = JSON.parse(JSON.stringify(original));
deepCopy.b.c = 10;
console.log(original.b.c); // 2 (reference is not shared)
```

---

These additional concepts cover **event delegation, propagation, throttling, debouncing**, and more, completing the missing parts of JavaScript fundamentals. Let me know if you need further explanations on any topic!

### Advanced Concepts

Here are some **advanced JavaScript concepts** that go beyond the fundamentals mentioned above:

---

## **Javascript  Core**

In JavaScript, the **memory creation** and **execution phase** are part of the execution context lifecycle that takes place during the interpretation of the code. The execution context consists of two key phases:

### 1. **Memory Creation Phase (Creation Phase / Hoisting Phase)**:

In this phase, the JavaScript engine performs the following actions before executing any code:

- **Variable and Function Declarations Hoisting**:

  - All variable declarations (using `var`, but not `let` or `const`) are hoisted, meaning they are registered in memory as `undefined`.
  - Function declarations are hoisted entirely, meaning the function definitions are also stored in memory.
  - Variables declared with `let` and `const` are hoisted but remain in a "temporal dead zone" until the actual line of code where they are defined.
- **Global Object & `this` Initialization**:

  - In a browser, the global execution context will also initialize the global object (`window`) and the `this` keyword, which points to that global object.

  **Example:**

  ```javascript
  console.log(x); // undefined (due to var hoisting)
  console.log(add(2, 3)); // 5 (function is fully hoisted)

  var x = 10;

  function add(a, b) {
    return a + b;
  }
  ```

  - During the creation phase, `x` is hoisted to memory but assigned `undefined`, while `add` is hoisted with its complete function definition.

### 2. **Execution Phase (Code Execution Phase)**:

In this phase, the JavaScript engine executes the code line-by-line:

- **Assigns Values to Variables**:

  - During this phase, variables get their assigned values. If any operation occurs before the assignment, it results in errors or `undefined` values, depending on the declaration type (`var`, `let`, `const`).
- **Executes Function Calls**:

  - As the interpreter encounters function calls, it pushes them onto the call stack and executes their body line-by-line.

  **Example:**

  ```javascript
  console.log(x); // undefined
  x = 10;         // now x is assigned the value 10
  ```

  - After hoisting `var x` as `undefined` during the memory creation phase, the engine assigns `10` to `x` during the execution phase.

### Behavior with `let` and `const`:

- Variables declared with `let` and `const` are hoisted but remain in the **temporal dead zone** until their declaration is encountered in the code.

  ```javascript
  console.log(y); // ReferenceError: Cannot access 'y' before initialization

  let y = 5;
  ```

  Here, `y` is hoisted but cannot be accessed before its initialization, leading to a ReferenceError.

### Summary of the Two Phases:

1. **Memory Creation Phase**:

   - Variables and functions are hoisted into memory.
   - Variables are set to `undefined` (for `var`) or placed in a "temporal dead zone" (for `let` and `const`).
   - Function declarations are hoisted with their definitions.
2. **Execution Phase**:

   - Code is executed line by line, and values are assigned to variables.
   - Function calls are made and their bodies are executed.

These two phases ensure that JavaScript's hoisting and execution work in a predictable way.

## **1. Closures**

A **closure** is a function that remembers its scope even after the outer function has executed. This allows inner functions to access variables from the outer scope.

### **Example**

```javascript
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
```

**Explanation:** The inner function remembers the value of `count` from the `outer` function, even after `outer` has finished executing.

---

## **2. Promises and Async/Await**

### **Promises**

A **promise** is an object representing the eventual completion or failure of an asynchronous operation.

### **Example**

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success!");
  }, 1000);
});

promise.then((message) => {
  console.log(message); // 'Success!' after 1 second
});
```

### **Async/Await**

**Async/Await** simplifies the process of working with promises, making asynchronous code appear synchronous.

### **Example**

```javascript
async function fetchData() {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();
  console.log(data);
}

fetchData();
```

---

## **3. Currying**

**Currying** is a technique where a function is transformed to take arguments one at a time rather than all at once.

### **Example**

```javascript
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    } else {
      return function (...nextArgs) {
        return curried.apply(this, args.concat(nextArgs));
      };
    }
  };
}

const sum = (a, b, c) => a + b + c;
const curriedSum = curry(sum);
console.log(curriedSum(1)(2)(3)); // 6
```

---

## **5. Module Pattern (IIFE)**

**Immediately Invoked Function Expressions (IIFE)** are functions that run immediately after they are defined. They are commonly used to create modules and avoid polluting the global scope.

### **Example**

```javascript
const module = (function () {
  let privateVar = "I am private";

  function privateMethod() {
    console.log(privateVar);
  }

  return {
    publicMethod: function () {
      privateMethod();
    },
  };
})();

module.publicMethod(); // 'I am private'
```

---

## **6. Prototypal Inheritance**

**Prototypal inheritance** allows objects to inherit properties and methods from other objects.

### **Example**

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function () {
  console.log(`${this.name} makes a noise`);
};

function Dog(name) {
  Animal.call(this, name); // Call parent constructor
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

const dog = new Dog("Buddy");
dog.speak(); // 'Buddy makes a noise'
```

---

## **7. Call, Apply, and Bind**

These methods allow you to explicitly set `this` in functions.

### **`call()`**

Calls a function with a given `this` value and arguments provided individually.

### **Example**

```javascript
const obj = { name: "Alice" };
function greet() {
  console.log(`Hello, ${this.name}`);
}

greet.call(obj); // 'Hello, Alice'
```

### **`apply()`**

Calls a function with a given `this` value and arguments provided as an array.

### **Example**

```javascript
function sum(a, b) {
  console.log(a + b);
}

sum.apply(null, [2, 3]); // 5
```

### **`bind()`**

Returns a new function that, when called, has its `this` value set to the provided value.

### **Example**

```javascript
const obj = { name: "Bob" };
const greetBob = greet.bind(obj);
greetBob(); // 'Hello, Bob'
```

---

## **8. Generators**

A **generator** is a special kind of function that can pause its execution and later resume, allowing it to produce a sequence of results over time.

### **Example**

```javascript
function* generatorFunc() {
  yield 1;
  yield 2;
  yield 3;
}

const generator = generatorFunc();
console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
console.log(generator.next().value); // 3
```

---

## **9. Symbol**

**Symbols** are unique and immutable values that can be used as identifiers for object properties.

### **Example**

```javascript
const sym = Symbol("description");
const obj = {
  [sym]: "value",
};

console.log(obj[sym]); // 'value'
```

---

## **10. WeakMap and WeakSet**

**WeakMap** and **WeakSet** allow you to store object keys or values without preventing their garbage collection.

### **WeakMap Example**

```javascript
let obj = {};
let weakMap = new WeakMap();
weakMap.set(obj, "some value");

obj = null; // Now obj can be garbage collected
```

### **WeakSet Example**

```javascript
let obj = {};
let weakSet = new WeakSet();
weakSet.add(obj);

obj = null; // Now obj can be garbage collected
```

---

## **11. Memoization**

**Memoization** is a technique for optimizing functions by caching the results of expensive function calls.

### **Example**

```javascript
function memoize(fn) {
  const cache = {};
  return function (...args) {
    const key = JSON.stringify(args);
    if (!cache[key]) {
      cache[key] = fn(...args);
    }
    return cache[key];
  };
}

const expensiveFunction = (num) => {
  console.log("Expensive function running...");
  return num * 2;
};

const memoizedFunction = memoize(expensiveFunction);
console.log(memoizedFunction(5)); // Expensive function runs
console.log(memoizedFunction(5)); // Cached result, no re-run
```

## **12. Optional Chaining (`?.`)**

**Optional chaining** allows you to safely access deeply nested object properties without worrying about `null` or `undefined` values, preventing runtime errors.

### **Example**

```javascript
const user = {
  address: {
    street: "Main St",
  },
};

console.log(user?.address?.street); // 'Main St'
console.log(user?.contact?.email); // undefined (no error)
```

---

## **13. Nullish Coalescing Operator (`??`)**

The **nullish coalescing operator (`??`)** provides a way to assign a default value when the left-hand side is `null` or `undefined`, while still allowing other falsy values like `0`, `false`, or `""`.

### **Example**

```javascript
const value = null ?? "Default Value"; // 'Default Value'
const value2 = 0 ?? "Default Value"; // 0 (because 0 is not null or undefined)
```

---

## **14. Destructuring Assignment**

Destructuring allows you to unpack values from arrays or properties from objects into distinct variables.

### **Array Destructuring Example**

```javascript
const [a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2
```

### **Object Destructuring Example**

```javascript
const user = { name: "John", age: 30 };
const { name, age } = user;
console.log(name); // 'John'
console.log(age); // 30
```

---

## **15. Spread Operator (`...`)**

The **spread operator (`...`)** allows you to expand arrays or objects. It's used for merging, copying, or passing elements.

### **Example**

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 }; // { a: 1, b: 2, c: 3 }
```

---

## **16. Dynamic Imports**

**Dynamic imports** allow you to load modules asynchronously when needed, improving performance for large applications.

### **Example**

```javascript
async function loadModule() {
  const module = await import("./someModule.js");
  module.someFunction();
}
```

---

## **17. BigInt**

**BigInt** is a built-in object that allows you to work with large integers, exceeding the `Number.MAX_SAFE_INTEGER` limit.

### **Example**

```javascript
const bigInt = 1234567890123456789012345678901234567890n;
console.log(bigInt + 10n); // 1234567890123456789012345678901234567900n
```

---

## **18. Functional Programming Concepts**

JavaScript supports **functional programming**, and understanding core functional concepts can be valuable:

- **Pure Functions**: Functions without side effects that always return the same result given the same input.
- **Immutability**: Avoid changing existing data. Instead, create new versions of data.
- **Map, Filter, Reduce**: Core functional methods for working with arrays.

### **Example (Map, Filter, Reduce)**

```javascript
const numbers = [1, 2, 3, 4, 5];

// map: transform each value
const doubled = numbers.map((n) => n * 2);

// filter: only keep even numbers
const evens = numbers.filter((n) => n % 2 === 0);

// reduce: sum all values
const sum = numbers.reduce((total, num) => total + num, 0);
```

---

## **19. Proxy and Reflect**

**Proxy** is used to create a custom handler for object operations like reading, writing, and deleting properties. **Reflect** provides default behavior for those operations.

### **Example**

```javascript
const person = {
  name: "Alice",
  age: 25,
};

const handler = {
  get: (target, prop) => {
    return prop in target ? target[prop] : `Property "${prop}" does not exist.`;
  },
};

const proxyPerson = new Proxy(person, handler);
console.log(proxyPerson.name); // 'Alice'
console.log(proxyPerson.height); // 'Property "height" does not exist.'
```

---

## **20. Tail Call Optimization**

**Tail call optimization (TCO)** is a feature of modern JavaScript engines that optimizes recursive function calls to prevent stack overflow and improve performance.

### **Example**

```javascript
function factorial(n, acc = 1) {
  if (n === 1) return acc;
  return factorial(n - 1, n * acc); // Tail call
}
console.log(factorial(5)); // 120
```

---

## **21. Set and Map**

- **Set** is a collection of unique values.
- **Map** is a collection of key-value pairs, where keys can be any data type.

### **Set Example**

```javascript
const set = new Set([1, 2, 3, 3, 4]);
console.log(set); // Set { 1, 2, 3, 4 }
```

### **Map Example**

```javascript
const map = new Map();
map.set("name", "John");
console.log(map.get("name")); // 'John'
```

---

## **22. Decorators**

**Decorators** are a stage-2 JavaScript proposal, often used in frameworks like Angular. They allow you to modify the behavior of classes or methods.

### **Example**

```javascript
function logMethod(target, key, descriptor) {
  const original = descriptor.value;
  descriptor.value = function (...args) {
    console.log(`Method ${key} called with arguments: ${args}`);
    return original.apply(this, args);
  };
  return descriptor;
}

class Person {
  @logMethod
  sayHello(name) {
    return `Hello, ${name}`;
  }
}

const p = new Person();
p.sayHello("Alice"); // Logs: Method sayHello called with arguments: Alice
```

---

## **23. WeakRef and FinalizationRegistry**

These are advanced memory management tools to create weak references and register callbacks for objects when they are garbage collected.

### **WeakRef Example**

```javascript
let obj = { name: "example" };
let weakRef = new WeakRef(obj);

obj = null; // Object can now be garbage collected
console.log(weakRef.deref()); // Might return undefined if garbage collected
```

---

## By adding these concepts, the list becomes well-rounded for developers who want to deepen their understanding of modern JavaScript, its paradigms, and advanced usage patterns. Let me know if you'd like further explanation on any of these!
