# Javascript

Here are the interview questions with detailed answers:

### 1. **Explain event delegation and how it works in JavaScript.**

   **Answer:**
   Event delegation is a technique where you attach a single event listener to a parent element instead of multiple listeners to individual child elements. The event listener listens for an event that bubbles up from the children, allowing you to handle events dynamically even for elements added later.

```js
   document.getElementById('parent').addEventListener('click', function (event) {
       if (event.target && event.target.matches('button.classname')) {
           console.log('Button clicked!');
       }
   });
```

### 2. **What are closures in JavaScript, and how would you use them?**

   **Answer:**
   A closure is a function that retains access to its lexical scope, even when the function is executed outside of its original scope.

```js
   function outer() {
       let count = 0;
       return function increment() {
           count++;
           return count;
       };
   }
   const counter = outer();
   console.log(counter()); // 1
   console.log(counter()); // 2
```

### 3. **What is the difference between `var`, `let`, and `const`?**

   **Answer:**

- `var`: Function-scoped, can be re-declared, and is hoisted.
- `let`: Block-scoped, cannot be re-declared, but can be updated.
- `const`: Block-scoped, cannot be re-declared or updated, but objects and arrays defined with `const` can be mutated.

### 4. **How does JavaScript handle asynchronous code?**

   **Answer:**
   JavaScript uses the event loop to handle asynchronous code. Promises and async/await are mechanisms to manage async operations. Microtasks (e.g., promise callbacks) are handled before macrotasks (e.g., `setTimeout`). The event loop constantly checks the call stack and pushes callbacks from the task queue onto the stack when it's empty.

### 5. **What are promises, and how do they differ from async/await?**

   **Answer:**
   Promises represent a value that may be available now, or in the future, or never. They have three states: `pending`, `fulfilled`, and `rejected`.

- Async/await is syntactic sugar over promises that make asynchronous code look synchronous.

```js
   // Using Promises
   fetchData().then(data => console.log(data)).catch(error => console.error(error));

   // Using async/await
   async function getData() {
       try {
           const data = await fetchData();
           console.log(data);
       } catch (error) {
           console.error(error);
       }
   }
```

### 6. **Explain the concept of "hoisting."**

   **Answer:**
   Hoisting in JavaScript means that variable and function declarations are moved to the top of their scope during the compile phase, but not their initializations.

```js
   console.log(x); // undefined (due to hoisting)
   var x = 5;

   console.log(y); // ReferenceError: Cannot access 'y' before initialization
   let y = 10;
```

### 7. **What are modules in JavaScript?**

   **Answer:**
   Modules allow you to organize code into reusable pieces. `import` and `export` are used to share functions, objects, or variables between files. Tree shaking is a feature in module bundlers (like Webpack) that removes unused code, improving performance.

### 8. **Explain prototypal inheritance.**

   **Answer:**
   In JavaScript, objects can inherit properties and methods from another object via the prototype chain. Every object in JavaScript has a hidden `[[Prototype]]` property, which refers to its parent object.

```js
   function Person(name) {
       this.name = name;
   }
   Person.prototype.sayHello = function () {
       console.log(`Hello, my name is ${this.name}`);
   };

   const person = new Person('Alice');
   person.sayHello(); // "Hello, my name is Alice"
```

### 9. **Explain `bind()`, `call()`, and `apply()`.**

   **Answer:**

- `bind()`: Returns a new function with `this` bound to a specific object.
- `call()`: Invokes a function with a specific `this` context and arguments passed individually.
- `apply()`: Similar to `call()`, but arguments are passed as an array.

```js
   function greet(greeting) {
       console.log(`${greeting}, ${this.name}`);
   }

   const person = { name: 'John' };
   greet.call(person, 'Hello'); // "Hello, John"
   greet.apply(person, ['Hi']); // "Hi, John"
   const boundGreet = greet.bind(person);
   boundGreet('Hey'); // "Hey, John"
```

### 10. **How does the garbage collector work in JavaScript?**

   **Answer:**
   The JavaScript garbage collector works by automatically identifying and reclaiming memory that is no longer accessible or used by the program. It typically uses algorithms like Mark-and-Sweep to detect memory that can be freed.

### 11. **Explain deep vs. shallow cloning.**

   **Answer:**

- **Shallow cloning** copies the reference of an object (e.g., using `Object.assign()` or spread operator), so changes to nested objects affect the original.
- **Deep cloning** creates a true copy of all objects, including nested objects, without shared references.

```js
   const shallowClone = Object.assign({}, obj);
   const deepClone = JSON.parse(JSON.stringify(obj));
```

### 12. **Explain the `this` keyword.**

   **Answer:**
   `this` refers to the object that is currently executing the function. In global scope, it refers to the `window` object in browsers. In object methods, `this` refers to the object itself.

```js
   const obj = {
       name: 'John',
       sayHello() {
           console.log(this.name);
       }
   };
   obj.sayHello(); // "John"
```

### 13. **What are generators in JavaScript?**

   **Answer:**
   Generators are functions that can be paused and resumed. They are declared using `function*` and yield values one at a time.

```js
   function* generator() {
       yield 1;
       yield 2;
       yield 3;
   }
   const gen = generator();
   console.log(gen.next().value); // 1
```

### 14. **What is the virtual DOM?**

   **Answer:**
   The virtual DOM is a lightweight, in-memory representation of the actual DOM. It allows React (or other libraries) to perform efficient updates by comparing the virtual DOM with the real DOM (diffing) and only applying the necessary changes.

### 15. **How would you handle state management in an SPA without libraries?**

   **Answer:**
   You can manage state using JavaScript objects and custom events. You can store the state in a central object and trigger updates via events when the state changes.

```js
   const state = { count: 0 };
   const increment = () => { state.count++; render(); };
```

### 16. **How do web workers improve performance?**

   **Answer:**
   Web workers run JavaScript code in background threads, allowing the main thread (UI) to remain responsive. However, they cannot directly manipulate the DOM.

### 17. **How do you debug a memory leak in JavaScript?**

   **Answer:**
   Use browser DevTools (Memory tab) to record heap snapshots and look for detached DOM elements, event listeners, or closures holding onto memory unnecessarily.
