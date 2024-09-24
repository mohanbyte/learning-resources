# Javascript

# What is Variable

  **Variable** is named storage used to hold data that can be change later during program execution. think variable as container which is used to store data like number, string and
  object. with the help of variable we can create dynamic programs which is used to store, modify and retrieve the data.

# Types of variables in Javascript.

  In Javascript there are three different types to create variables `var`, `let` and `const`. `<br>`

1. **`var` (Variable Declaration)**

   - **Scope**: `var` keyword has **function scope**. This means variable declared with `var` keyword are accesible throughout the function that declared in or globally if not in                         function
   - **Hoisting** : `var` keyword hoisted top of their scope. this means variable moves to the top of their scope but not initialized.
   - **Re-declaration**: variable declared with `var` keyword can be redeclared within same scope.
     ```javascript
         var x = 5;
         var x = 10; // No error, x is now 10

     ```
2. **`let` (Block Scope)**

   - **Scope**: `let` keyword has block scope. This means variable declared with `let` keyword are accesible within the block they are declared.
   - **Hoisting**: `let` keyword hoisted top of their scope but not initialized. This means accesing the variable before declaration will give reference error.
   - **Re-declaration**: variable declared with `let` keyword cannot be re-declared within same scope.
   - **Example**
     ```javascript
         let y = 5;
         y = 10; // Allowed, y is now 10
         let y = 15; // Error: Identifier 'y' has already been declared

     ```
3. **`const` (constant Variable)**

   - **Scope**: `const` keyword has block scope. This means variable declared with `const` keyword are accesible within the block they are declared.
   - **Hoisting**: `const` keyword hoisted top of their scope but not initialized. This means accesing the variable before declaration will give reference error.
   - **Re-declaration and Re-assignment**: variable declared with `const` keyword cannot be re-declared or re-assigned after initial assignment. however for the `objects` and for the        `arrays` content still be modified.
   - **Example**

   ```javascript
        const z = 5;
        z = 10; // Error: Assignment to constant variable.
        const obj = { key: "value" };
        obj.key = "newValue"; // Allowed, modifying the object property
   ```

# Scope in Javscript

1. **Global Scope**: any variable declared outside function or block has global scope. This means that variable are accesible anywhere in code.
2. **Function Scope**: varibale declared with `var` keyword inside function has function scope. This means that variable is accesible in only that function.
3. **Block Scope**: variable declared using `let` and `const` keyword in block `{}` has block scope. This means variable is accesible within only that block.

# Hoisting

  Hoisting is default behaviour of javascript to move the declaration top of their scope. `var` keyword is hoisted and initialized with `undefined`. `let` and `const` keyword hoisted     but not initialized.

# Shadowing

  The variable can be `shadowed` if variable with same name declared in different scope. if variable declared in inner block (close to execution context) will shadow the variable
  declared in outer block.

# Best practices

- use `const` and `let` keyword to avoid scope and hoisting issue.
- use `const` keyword if value is not gonna change and `let` if value gonna change.
- use meaningful variable name to enhace code readability.
- follow consistent naming convention, like camelCase

# Pseudocode for Using Variables

```javascript
      // Declare a global variable using var
      var globalVar = "I'm global";

      // Function to demonstrate function-scoped variable
      function demonstrateVar() {
        var functionScopedVar = "I'm function-scoped"; 
        console.log(functionScopedVar); // Outputs: I'm function-scoped
      }

      // Block to demonstrate block-scoped variables
      if (condition) {
        let blockScopedLet = "I'm block-scoped";
        const blockScopedConst = "I'm also block-scoped";
  
        console.log(blockScopedLet); // Outputs: I'm block-scoped
        console.log(blockScopedConst); // Outputs: I'm also block-scoped
      }

      // Hoisting example
      console.log(hoistedVar); // Outputs: undefined
      var hoistedVar = "I'm hoisted";

      // Trying to access block-scoped variable outside the block
      console.log(blockScopedLet); // Error: blockScopedLet is not defined
```

# Data Types

1. **Primitive Data Types** `<br>`
   Primitive data types are the most basic data type and represents single value. They are immutable in nature, means once value is assigned it can't be changed.
   Primitive Data Types has following sub types;

   1. **Number**: Number represents both integer and floating point numbers. example, `42` and `3.14` Javascript doesn't distinguish between Integer and Floating-Point numbers they           both treated as Number.
   2. **String**: Strings are the sequence of characters. Strings are used to store text and are enclosed in single quotes `''`, double quotes `""` or backticks ``. example `"Hello"`
   3. **Boolean**: Boolean represent logical entity value `true` or `false`.
   4. **Undefined**: when variable is declared without initialiaztion it's automically assigned `undefined` value.
   5. **Null**: Null is intentional absence of value. it is explicitly assigned to indicate that varibale has no value.
   6. **Symbol**: Symbol is unique and immutable value. it is oftnely used as object property keys to avoid same property name collision. example, `Symbol('unique')`.
   7. **bigInt**: Represents integers with arbitrary precision, useful for handling very large integers. Example: `1234567890123456789012345678901234567890n`.

   **Notes** `<br>`

   1. **Type Coercion With `null` and `undefined`** `<br>`

   - using `undefined` with number result is in `NaN` value. example 5+`undefined` will return `NaN`.
   - `null` is treated as `0` in arithmetic operation. example 5+`null` will return `5`.

   2. **BigInt and Number Interaction**: `<br>`

   - `BigInt` cannot be directly mixed with `number` in arithmetic operation. `5n + 1` is valid but will throw `TypeError`.

   3. **String Conversion** `<br>`

   - when concatenating `number` and `string`, The `number` is converted to `string` example `5 + '5'` will return `55`.

   4. **Symbol Uniqueness** `<br>`

   - Symbols are unique and can't be replicated. Even if we create symbol with same description it will not be equal to original symbol.
2. **Non-Primitive Data Types** `<br>`
   Non-Primitive data types are mutable in nature. strored as reference. operations can change original value.

   1. **Objects** `<br>`
      In Javascript, object is a collection of properties, where each property is key-value pair. object can hold multiple data types, including function and other objects.

      - Creating an Object

        ```javascript

           const person = {
           name: 'Alice',
           age: 30,
           greet() {
             return `Hello, my name is ${this.name}`;
           }
          };

        ```
      - Accessing and Modifying Object

        ```javascript
          console.log(person.name); // Alice
          person.age = 31;
          console.log(person['age']); // 31

        ```
      - Adding New Properties

        ```javascript
           person.job = 'Engineer';
        ```
      - Deleting Properties

        ```javascript
           delete person.job;
        ```
   2. **Built In Objects** `<br>`
      Javascript provides several built in projects as following:

      - **Object**: The base object from which all objects inherit. `<br>`
        ```javascript
           const obj = new Object();
        ```
      - **Array**: For storing ordered collections.
        ```javascript
           const numbers = [1, 2, 3];
        ```
      - **String**: For manipulating text.
        ```javascript
          const str = 'Hello';
        ```
      - **Number**: For Numeric Operations.
        ```javascript
           const num = 123;
        ```
      - **Boolean**: For logical values.
        ```javascript
           const flag = true;
        ```
      - **Date**: For working with dates and times.
        ```javascript
           const date = new Date();
        ```
      - **RegExp**: for pattern matching in string.
        ```javascript
           const pattern = /ab+c/;
        ```
      - **Error**: For handling errors.
        ```javascript
           const error = new Error('Something went wrong');
        ```
   3. **Prototypal Inheritance** `<br>`
      Prototypal Inheritance allows objects to innherit properties from other objects. every object has prototype from which it inherits methods and properties.

      - Prototype Chain:
        Every object in JavaScript has a prototype. When you access a property or method on an object, JavaScript first looks at the object itself. If it doesn’t find the property,            it looks up the prototype chain, starting from the object's prototype and continuing up the chain until it reaches Object.prototype (which is the end of the chain).

        ```javascript
           function Animal(name) {
             this.name = name;
           }

           Animal.prototype.speak = function() {
                console.log(`${this.name} makes a noise.`);
           };

           const dog = new Animal('Rex');
           dog.speak(); // Rex makes a noise.
        ```
      - Inheriting from Prototypes:

        ```javascript
           function Dog(name, breed) {
              Animal.call(this, name);
              this.breed = breed;
           }

           Dog.prototype = Object.create(Animal.prototype);
           Dog.prototype.constructor = Dog;

           Dog.prototype.bark = function() {
              console.log(`${this.name} barks.`);
           };

           const myDog = new Dog('Buddy', 'Golden Retriever');
           myDog.speak(); // Buddy makes a noise.
           myDog.bark(); // Buddy barks.

        ```
   4. **Object Prototype** `<br>`
      Prototype of an object is another object from which it inherits properties. this allows to create shared properties and methods.

      - Accessing Prototype

        ```javascript
           const obj = {};
           console.log(Object.getPrototypeOf(obj)); // Logs the prototype of obj
        ```
      - **Setting Prototype**

        ```javascript
           const proto = { greet: 'Hello' };
           const obj = Object.create(proto);
           console.log(obj.greet); // Hello
        ```
      - **Prototype Property**

        ```javascript
           function Person(name) {
              this.name = name;
           }

           Person.prototype.sayHello = function() {
             return `Hello, ${this.name}`;
           };

           const person = new Person('Alice');
           console.log(person.sayHello()); // Hello, Alice

        ```

# `typeof` Operator

   `typeof` operator is used to determine type of variable or expression. it returns string representig type of operand. typeof is useful for debugging and type checking in javascript.

```javascript
      // Primitive types
      let num: number = 42;
      let str: string = 'Hello';
      let bool: boolean = true;
      let undef: undefined;
      let sym: symbol = Symbol('id');
      let big: bigint = 1234567890123456789012345678901234567890n;
  
      // Object types
      let obj: object = { name: 'Alice' };
      let arr: object = [1, 2, 3];
      let func: Function = function() {};
      let nothing: null = null;
  
      // Type checks
      console.log(typeof num); // "number"
      console.log(typeof str); // "string"
      console.log(typeof bool); // "boolean"
      console.log(typeof undef); // "undefined"
      console.log(typeof sym); // "symbol"
      console.log(typeof big); // "bigint"
      console.log(typeof obj); // "object"
      console.log(typeof arr); // "object"
      console.log(typeof func); // "function"
      console.log(typeof nothing); // "object"
```

  **Notes** `<br>`

1. Arrays `<br>`
   `typeof` [1,2,3] return `object` not `array`. To check if variable is an array use `Array.isArray()`.
2. `null` `<br>`
   `typeof` null is `object`.
3. Function `<br>`
   `typeof` function is `function` but technically it is an array.
4. Undefined `<br>`
   variables that are not initialized return `undefined`.
5. Symbol and bigInt `<br>`
   `typeof` Symbols returns `Symbol` and `typeof` bigInt return `bigInt`.

```javascript
Let a= 10;

let b= new Number(10); // returns a number object ; actual value in b.valueOf(); - can get toFixed()

a===b //false; number , object

a==b // true

<!---------------------------------/>
let a=9 , b =10;

let c = (a, b);

console.log(c);//10
```

## Advanced

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


# JavaScript Interview Questions and Answers by Experience Level

## Junior Level

### JavaScript Basics

1. Q: What is the difference between `let`, `const`, and `var`?
   A:

   - `var`: Function-scoped or globally-scoped, can be redeclared and updated.
   - `let`: Block-scoped, can be updated but not redeclared within its scope.
   - `const`: Block-scoped, cannot be updated or redeclared. For objects and arrays, the reference can't be changed, but properties can be modified.
2. Q: Explain the concept of hoisting in JavaScript.
   A: Hoisting is JavaScript's default behavior of moving declarations to the top of their scope before code execution. Variables declared with `var` are hoisted and initialized with `undefined`, while `let` and `const` are hoisted but not initialized (temporal dead zone). Function declarations are fully hoisted.
3. Q: What is the difference between `==` and `===`?
   A:

   - `==` (loose equality): Compares values after type coercion.
   - `===` (strict equality): Compares both value and type without coercion.
     Example: `1 == '1'` is true, but `1 === '1'` is false.
4. Q: How does the `this` keyword work in JavaScript?
   A: `this` refers to the object that is executing the current function. Its value depends on how the function is called:

   - In a method, `this` refers to the object the method was called on.
   - In a regular function, `this` refers to the global object (or `undefined` in strict mode).
   - In an arrow function, `this` retains the value of the enclosing lexical context.
5. Q: What are closures and how are they used?
   A: A closure is a function that has access to variables in its outer (enclosing) lexical scope, even after the outer function has returned. Closures are used for data privacy, creating function factories, and in module patterns.

### DOM Manipulation

6. Q: How do you select elements in the DOM using JavaScript?
   A: Elements can be selected using methods like:

   - `document.getElementById('id')`
   - `document.getElementsByClassName('class')`
   - `document.getElementsByTagName('tag')`
   - `document.querySelector('selector')`
   - `document.querySelectorAll('selector')`
7. Q: What is event delegation and why is it useful?
   A: Event delegation is a technique where you add a single event listener to a parent element instead of adding listeners to multiple child elements. It's useful for improving performance and handling dynamically added elements.
8. Q: Explain the difference between `innerHTML` and `textContent`.
   A:

   - `innerHTML`: Gets or sets the HTML content inside an element. It parses content as HTML and can execute scripts.
   - `textContent`: Gets or sets the text content of an element and all its descendants. It treats the content as plain text and is generally safer and faster than `innerHTML`.

### ES6+ Features

9. Q: What are arrow functions and how do they differ from regular functions?
   A: Arrow functions are a concise way to write function expressions. Key differences:

   - Shorter syntax
   - No binding of `this`
   - Can't be used as constructors
   - Don't have their own `arguments` object
   - Always anonymous
10. Q: Explain destructuring in JavaScript.
    A: Destructuring is a way to extract values from objects or arrays and assign them to variables. Example:

    ```javascript
    const { name, age } = person;  // Object destructuring
    const [first, second] = array; // Array destructuring
    ```
11. Q: What are template literals?
    A: Template literals are string literals that allow embedded expressions and multi-line strings. They are enclosed by backticks (`) and can contain placeholders indicated by `${}`. Example:

    ```javascript
    const name = 'World';
    console.log(`Hello, ${name}!`);
    ```

### Asynchronous JavaScript

12. Q: What is a callback function?
    A: A callback function is a function passed as an argument to another function, to be executed after the first function completes. It's often used in asynchronous operations.
13. Q: Explain the difference between synchronous and asynchronous code.
    A:

    - Synchronous code: Executes line by line, blocking until each operation completes.
    - Asynchronous code: Allows other code to run while waiting for operations to complete, typically using callbacks, promises, or async/await.
14. Q: What is a Promise and how does it work?
    A: A Promise is an object representing the eventual completion or failure of an asynchronous operation. It has three states: pending, fulfilled, or rejected. Promises provide methods like `.then()` and `.catch()` to handle the results or errors of asynchronous operations.

### Frontend Basics

15. Q: What is the box model in CSS?
    A: The box model describes how elements are rendered in CSS. It consists of:

    - Content: The actual content of the element
    - Padding: Space between the content and the border
    - Border: A line around the padding and content
    - Margin: Space outside the border
16. Q: Explain the difference between `display: inline`, `block`, and `inline-block`.
    A:

    - `inline`: Elements flow in-line with text and don't start on a new line. Width and height can't be set.
    - `block`: Elements start on a new line and take up the full width available. Width, height, margins, and padding can be set.
    - `inline-block`: Elements flow in-line but can have width and height set. They don't start on a new line.
17. Q: What is responsive design and how can you implement it?
    A: Responsive design is an approach to web design that makes web pages render well on various devices and window or screen sizes. It can be implemented using:

    - Flexible layouts (using percentages)
    - Media queries
    - Flexible images and media
    - CSS Grid and Flexbox

## Mid-Level

### Advanced JavaScript Concepts

1. Q: Explain prototypal inheritance in JavaScript.
   A: Prototypal inheritance is a method by which an object can inherit properties and methods from another object. In JavaScript, each object has an internal link to another object called its prototype. When trying to access a property that doesn't exist in an object, JavaScript looks for it in the prototype chain.
2. Q: What are higher-order functions?
   A: Higher-order functions are functions that can take other functions as arguments or return functions. They allow for more abstract and reusable code. Examples include `map`, `filter`, and `reduce`.
3. Q: Describe the event loop in JavaScript.
   A: The event loop is a mechanism that allows JavaScript to perform non-blocking operations despite being single-threaded. It continuously checks the call stack and the callback queue. When the call stack is empty, it takes the first event from the queue and pushes it to the call stack, which runs it.
4. Q: What is the difference between `map`, `filter`, and `reduce`?
   A:

   - `map`: Creates a new array with the results of calling a provided function on every element in the array.
   - `filter`: Creates a new array with all elements that pass the test implemented by the provided function.
   - `reduce`: Executes a reducer function on each element of the array, resulting in a single output value.
5. Q: Explain the concept of memoization.
   A: Memoization is an optimization technique that speeds up programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again. It's particularly useful for recursive or computationally expensive functions.

### Frontend Frameworks/Libraries (Angular)

6. Q: What are the key features of Angular?
   A: Key features of Angular include:

   - Component-based architecture
   - TypeScript support
   - Two-way data binding
   - Dependency injection
   - Reactive programming with RxJS
   - Powerful CLI for project scaffolding and management
   - Built-in routing
   - Comprehensive testing utilities
7. Q: Explain the virtual DOM and its benefits.
   A: While Angular doesn't use a virtual DOM, it's important to understand the concept. The virtual DOM is a lightweight copy of the actual DOM. Frameworks that use it (like React) make changes to this virtual representation first, then efficiently update the real DOM. This approach can lead to better performance by minimizing direct manipulation of the DOM.
8. Q: What is state management and why is it important in frontend applications?
   A: State management refers to the management of an application's data flow and storage. It's important because as applications grow, managing state across components becomes complex. In Angular, state management can be handled through services, RxJS, or state management libraries like NgRx. Proper state management ensures data consistency, improves maintainability, and can enhance performance.

### Performance Optimization

9. Q: How can you optimize the performance of a JavaScript application?
   A: Performance optimization techniques include:

   - Minimizing and compressing assets
   - Lazy loading of modules and components
   - Using efficient data structures and algorithms
   - Implementing caching strategies
   - Reducing DOM manipulations
   - Optimizing images and other media
   - Using web workers for CPU-intensive tasks
   - Implementing proper error handling and logging
10. Q: Explain lazy loading and its benefits.
    A: Lazy loading is a technique where you load parts of your application on demand, rather than loading everything upfront. In Angular, this often means loading feature modules only when they're needed. Benefits include faster initial load times, reduced bandwidth usage, and improved performance, especially for large applications.
11. Q: What are service workers and how can they improve performance?
    A: Service workers are scripts that run in the background, separate from a web page. They can intercept network requests, cache resources, and enable offline functionality. They improve performance by:

    - Caching assets for offline use
    - Providing faster load times for repeat visits
    - Enabling background sync and push notifications

### Testing

12. Q: What are unit tests and how do you write them in JavaScript?
    A: Unit tests are automated tests that verify the behavior of individual units of code (usually functions or methods) in isolation. In JavaScript, you can use testing frameworks like Jest or Jasmine. A basic unit test might look like:

    ```javascript
    describe('MyFunction', () => {
      it('should return correct result', () => {
        expect(myFunction(input)).toBe(expectedOutput);
      });
    });
    ```
13. Q: Explain the concept of test-driven development (TDD).
    A: Test-driven development is a software development process where you write tests before writing the actual code. The TDD cycle typically follows these steps:

    1. Write a failing test
    2. Write the minimum amount of code to make the test pass
    3. Refactor the code
       This approach can lead to better code design, fewer bugs, and easier refactoring.

### Build Tools and Module Bundlers

14. Q: What is Webpack and why is it used?
    A: Webpack is a static module bundler for modern JavaScript applications. It's used to:

    - Bundle JavaScript files for usage in a browser
    - Transform, bundle, or package other resources and assets
    - Manage dependencies
    - Optimize the build process
      It helps in creating more efficient and manageable front-end builds.
15. Q: Explain the difference between CommonJS and ES modules.
    A:

    - CommonJS: Used in Node.js, uses `require()` and `module.exports`. Modules are loaded synchronously.
    - ES modules: Native JavaScript module system, uses `import` and `export` statements. Modules are loaded asynchronously and can be statically analyzed.
      ES modules are becoming the standard for browser-based JavaScript.

## Senior Level

### Architecture and Design Patterns

1. Q: Explain the MVC (Model-View-Controller) architecture.
   A: MVC is a software design pattern that separates an application into three interconnected components:

   - Model: Manages data and business logic
   - View: Handles layout and display
   - Controller: Routes commands to the model and view parts
     This separation of concerns allows for more maintainable and scalable applications.
2. Q: What are design patterns and can you give examples of commonly used ones in JavaScript?
   A: Design patterns are reusable solutions to common problems in software design. Examples in JavaScript include:

   - Singleton: Ensures a class has only one instance
   - Factory: Creates objects without specifying the exact class
   - Observer: Defines a subscription mechanism for objects
   - Module: Encapsulates functionality to keep code organized
   - Decorator: Adds new functionality to an object without altering its structure
3. Q: How would you structure a large-scale JavaScript application?
   A: Structuring a large-scale application might involve:

   - Modular architecture (e.g., feature-based modules)
   - Clear separation of concerns
   - Use of design patterns and SOLID principles
   - Consistent coding standards and style guides
   - Proper state management
   - Efficient build and bundling processes
   - Comprehensive testing strategy
   - Clear documentation and code comments

### Advanced Performance Optimization

4. Q: How would you debug performance issues in a JavaScript application?
   A: Debugging performance issues involves:

   - Using browser dev tools (Performance tab, Memory tab)
   - Profiling JavaScript execution
   - Analyzing network requests and load times
   - Identifying memory leaks
   - Using performance monitoring tools (e.g., Lighthouse)
   - Conducting A/B tests for optimizations
5. Q: Explain code splitting and its benefits.
   A: Code splitting is a technique that involves dividing your code into smaller chunks which can be loaded on demand. Benefits include:

   - Faster initial load times
   - Reduced bundle sizes
   - Better resource utilization
   - Improved caching
6. Q: What are Web Workers and how can they improve performance?
   A: Web Workers allow you to run scripts in background threads. They can improve performance by:

   - Offloading heavy computations from the main thread
   - Keeping the UI responsive during intensive tasks
   - Enabling true multi-threading in JavaScript

### Security

7. Q: What are common security vulnerabilities in JavaScript applications and how can they be prevented?
   A: Common vulnerabilities include:

   - Cross-Site Scripting (XSS): Prevent by sanitizing input and using Content Security Policy
   - Cross-Site Request Forgery (CSRF): Use anti-CSRF tokens
   - SQL Injection: Use parameterized queries or ORMs
   - Insecure Direct Object References: Implement proper access controls
   - Using outdated libraries: Regularly update dependencies
8. Q: Explain Cross-Site Scripting (XSS) and how to prevent it.
   A: XSS is an attack where malicious scripts are injected into trusted websites. Prevention methods include:

   - Sanitizing user input
   - Encoding output
   - Using Content Security Policy (CSP) headers
   - Implementing HttpOnly flags on cookies
   - Using frameworks that automatically escape content

### Scalability and Maintainability

9. Q: How do you ensure code quality in a large team?
   A: Ensuring code quality in a large team involves:

   - Establishing coding standards and style guides
   - Implementing automated code linting and formatting
   - Regular code reviews
   - Comprehensive testing (unit, integration, e2e)
   - Continuous Integration/Continuous Deployment (CI/CD)
   - Documentation and knowledge sharing
   - Regular refactoring and tech debt management
10. Q: Explain the importance of code reviews and how you would conduct them.
    A: Code reviews are important for:

    - Ensuring code quality and consistency
    - Knowledge sharing within the team
    - Catching bugs and security issues early
    - Mentoring junior developers
      Conducting effective code reviews involves:
    - Using pull request workflows
    - Setting clear review guidelines
    - Focusing on logic, design, and potential issues
    - Providing constructive feedback
    - Using automated tools to catch style and basic issues
11. Q: What strategies would you use to refactor a large, legacy JavaScript codebase?
    A: Strategies for refactoring include:

    - Identifying and prioritizing areas that need refactoring
    - Adding tests before refactoring to ensure behavior doesn't change
    - Refactoring incrementally, avoiding big bang rewrites
    - Updating to modern JavaScript features and best practices
    - Modularizing the codebase
    - Implementing design patterns where appropriate
    - Continuously monitoring

### Advanced Asynchronous Patterns

12. Q: Explain async/await and how it differs from Promises.
    A: Async/await is a syntactic feature in JavaScript that provides a more readable way to work with Promises:

    - `async` functions always return a Promise
    - `await` can only be used inside an `async` function
    - `await` pauses the execution of the async function until the Promise is resolved

    Differences from Promises:

    - More readable, synchronous-looking code
    - Easier error handling with try/catch
    - Simpler when dealing with multiple asynchronous operations in sequence

    Example:

    ```javascript
    async function fetchData() {
      try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        return data;
      } catch (error) {
        console.error('Error:', error);
      }
    }
    ```
13. Q: What are generators and how can they be used for asynchronous programming?
    A: Generators are functions that can be paused and resumed, allowing them to yield multiple values over time. They are defined using the `function*` syntax and use the `yield` keyword.

    For asynchronous programming, generators can be combined with Promises to create more readable asynchronous code, especially before async/await was introduced. Libraries like co used this approach.

    Example:

    ```javascript
    function* fetchData() {
      try {
        const response = yield fetch('https://api.example.com/data');
        const data = yield response.json();
        return data;
      } catch (error) {
        console.error('Error:', error);
      }
    }

    // Using a generator runner (simplified example)
    function run(generator) {
      const iterator = generator();
      function iterate(iteration) {
        if (iteration.done) return iteration.value;
        const promise = iteration.value;
        return promise.then(x => iterate(iterator.next(x)));
      }
      return iterate(iterator.next());
    }

    run(fetchData).then(data => console.log(data));
    ```

### Backend Concepts (for Full-Stack Roles)

14. Q: Explain RESTful API design principles.
    A: RESTful API design principles include:

    - Statelessness: Each request contains all information needed to process it
    - Client-Server separation: Client and server evolve independently
    - Cacheability: Responses should be cacheable when applicable
    - Uniform interface: Consistent resource identification and manipulation
    - Layered system: Client doesn't know or care about intermediate layers
    - Resource-based: APIs are designed around resources (nouns) not actions
    - Use of standard HTTP methods (GET, POST, PUT, DELETE, etc.)
    - Proper use of HTTP status codes
15. Q: What is server-side rendering and when would you use it?
    A: Server-side rendering (SSR) is the process of rendering web pages on the server and sending the fully rendered page to the client. You would use SSR:

    - To improve initial page load time, especially for content-heavy sites
    - For better SEO, as search engines can easily crawl the fully rendered content
    - To provide a better user experience for users with slower devices or connections
    - When you need to display user-specific content immediately on page load
    - For applications that require social media sharing with rich previews
16. Q: Describe the differences between relational and non-relational databases.
    A:
    Relational Databases:

    - Use structured data in tables with predefined schemas
    - Support complex queries and joins between tables
    - Ensure ACID (Atomicity, Consistency, Isolation, Durability) properties
    - Examples: MySQL, PostgreSQL, Oracle

    Non-Relational (NoSQL) Databases:

    - Can handle unstructured or semi-structured data
    - Often more scalable and better for distributed systems
    - Generally provide more flexible schemas
    - May sacrifice some ACID properties for performance and scalability
    - Examples: MongoDB (document store), Cassandra (wide-column store), Redis (key-value store)

    Choose based on data structure, scalability needs, consistency requirements, and query complexity.
17. Q: What is OAuth and how does it work?
    A: OAuth (Open Authorization) is an open standard for access delegation, commonly used for secure authorization in web applications.

    How it works:

    1. The application requests authorization from the user
    2. User approves the authorization request
    3. The application receives an authorization grant
    4. The application requests an access token from the authorization server
    5. The authorization server issues an access token to the application
    6. The application uses the access token to access protected resources

    OAuth allows users to grant limited access to their resources on one site to another site without sharing their credentials.

### Emerging Technologies

18. Q: What is WebAssembly and how can it be used with JavaScript?
    A: WebAssembly (Wasm) is a binary instruction format for a stack-based virtual machine, designed as a portable target for high-level languages like C, C++, and Rust.

    How it can be used with JavaScript:

    - Wasm modules can be loaded and run from JavaScript
    - It allows computationally intensive tasks to be offloaded from JavaScript
    - Wasm and JavaScript can interoperate, sharing data and calling each other's functions
    - It enables bringing existing codebases and libraries to the web
    - Useful for performance-critical applications like games, video editing, or complex calculations
19. Q: Explain the concept of Jamstack architecture.
    A: Jamstack (JavaScript, APIs, Markup) is an architecture designed to make the web faster, more secure, and easier to scale. Key principles:

    - Pre-rendering: Pages are generated at build time, not on each request
    - Decoupling: Clear separation between frontend and backend services
    - Static-first: Serve static assets from CDNs for better performance
    - JavaScript: Dynamic functionalities are handled by JavaScript in the browser
    - APIs: Server-side operations are abstracted into reusable APIs
    - Markup: Use of static site generators or build tools to produce HTML

    Benefits include improved performance, better security, easier scaling, and improved developer experience.
20. Q: What are your thoughts on the future of JavaScript and web development?
    A: This is an opinion-based question, but some points to consider:

    - Continued evolution of JavaScript (TC39 proposals)
    - Growing importance of TypeScript
    - Increasing use of WebAssembly for performance-critical tasks
    - Serverless and edge computing becoming more prominent
    - Continued focus on performance and user experience (Core Web Vitals)
    - AI and machine learning integration in web applications
    - Progressive Web Apps (PWAs) bridging the gap between web and native apps
    - Increased use of APIs and microservices architecture
    - Growing importance of accessibility and inclusive design
    - Continued evolution of frontend frameworks and build tools

## Additional Technical Questions

### Data Structures and Algorithms

21. Q: Implement a function to flatten a nested array in JavaScript.
    A: Here's one way to implement array flattening:

    ```javascript
    function flattenArray(arr) {
      return arr.reduce((flat, toFlatten) => {
        return flat.concat(Array.isArray(toFlatten) ? flattenArray(toFlatten) : toFlatten);
      }, []);
    }

    // Example usage:
    console.log(flattenArray([1, [2, [3, 4], 5], 6])); // [1, 2, 3, 4, 5, 6]
    ```

    This solution uses recursion and the `reduce` method to flatten nested arrays of any depth.
22. Q: Explain the time complexity of common array operations in JavaScript.
    A: Common array operations and their time complexities:

    - Access by index: O(1)
    - Push/pop (end of array): O(1)
    - Unshift/shift (beginning of array): O(n)
    - Splice: O(n)
    - forEach/map/filter/reduce: O(n)
    - Sort: O(n log n) typically

    It's important to note that these can vary based on the JavaScript engine implementation.

### TypeScript

23. Q: What are generics in TypeScript and when would you use them?
    A: Generics in TypeScript allow you to create reusable components that can work with a variety of types rather than a single one. They're used when you want to create flexible, reusable functions or classes that maintain type safety.

    Example:

    ```typescript
    function identity<T>(arg: T): T {
      return arg;
    }

    let output = identity<string>("myString");
    ```

    You'd use generics when:

    - Creating functions that work with multiple types
    - Building reusable components
    - Writing libraries or frameworks
    - Implementing data structures (like linked lists or binary trees)

### React (for comparison with Angular)

24. Q: Explain the concept of hooks in React and give examples of commonly used hooks.
    A: Hooks in React are functions that let you use state and other React features in functional components. They were introduced to allow stateful logic in functional components without classes.

    Common hooks:

    - `useState`: For adding state to functional components
    - `useEffect`: For side effects in components (similar to lifecycle methods)
    - `useContext`: For consuming context in functional components
    - `useReducer`: For complex state logic
    - `useCallback` and `useMemo`: For optimizing performance

    Example of `useState`:

    ```javascript
    import React, { useState } from 'react';

    function Counter() {
      const [count, setCount] = useState(0);

      return (
        <div>
          <p>You clicked {count} times</p>
          <button onClick={() => setCount(count + 1)}>
            Click me
          </button>
        </div>
      );
    }
    ```

### Node.js

25. Q: Explain the Event Loop in Node.js.
    A: The Event Loop is a mechanism in Node.js that allows it to perform non-blocking I/O operations despite JavaScript being single-threaded. It works by offloading operations to the system kernel whenever possible and using a callback mechanism to handle these operations when they're completed.

    The Event Loop goes through these phases:

    1. Timers: Executes callbacks scheduled by `setTimeout()` and `setInterval()`
    2. Pending callbacks: Executes I/O callbacks deferred to the next loop iteration
    3. Idle, prepare: Used internally
    4. Poll: Retrieves new I/O events; executes I/O related callbacks
    5. Check: Executes `setImmediate()` callbacks
    6. Close callbacks: Executes close event callbacks

    This allows Node.js to handle many concurrent operations efficiently, making it well-suited for I/O-bound applications.

### CSS and HTML

26. Q: Explain the CSS Box Model and how it affects layout.
    A: The CSS Box Model describes how elements are rendered in web pages. It consists of:

    - Content: The actual content of the element
    - Padding: Space between the content and the border
    - Border: A line around the padding and content
    - Margin: Space outside the border

    The box model affects layout by determining the total size of an element:

    - Total width = width + left padding + right padding + left border + right border + left margin + right margin
    - Total height = height + top padding + bottom padding + top border + bottom border + top margin + bottom margin

    The `box-sizing` property can change how the box model is calculated:

    - `content-box` (default): Width and height only apply to the content
    - `border-box`: Width and height include content, padding, and border (but not margin)

    Understanding the box model is crucial for creating precise layouts and managing element sizing in CSS.
