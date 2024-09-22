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
