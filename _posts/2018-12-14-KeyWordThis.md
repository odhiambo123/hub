---
layout: post
title: "Keyword - 'This' "
date: 2018-12-14
categories: [javaScript]
---


When a JavaScript function is **invoked** (or run), a new **execution context** is created. Think of this execution context as a temporary workspace specifically for that function call. It's distinct from the function object itself, which lives in memory with properties like its name and the actual code.

-----

### Understanding the Execution Context

The execution context dictates how the function's code will run. Each execution context has:

  * **Variable Environment:** This is where variables declared inside that specific function call "live." It's like a private locker for the function's data.
  * **Reference to its Outer Environment (Lexical Environment):** This is a crucial concept. It remembers where the function was physically written in the code. If the function needs a variable that isn't in its own variable environment, it will look to its outer lexical environment, and then that environment's outer environment, and so on. This process is called **scope chaining**, and it continues until the variable is found or the global environment is reached.
  * **The `this` Keyword:** Every time a new execution context is created, the JavaScript engine automatically provides a special variable called `this`. The value of `this` isn't fixed; it changes depending on **how** the function is invoked. This dynamic behavior can often lead to confusion.

-----

### `this` in Action: Examples

Let's explore how `this` behaves in different scenarios:

#### 1\. Global Context

When you're not inside any function, you're in the **global execution context**. In a browser environment, `this` at this level refers to the **`window` object**.

```javascript
console.log(this); // In a browser, this will log the Window object
```

#### 2\. Simple Function Invocation

When you call a standalone function (not as a method of an object), `this` still points to the **global object** (the `window` object in browsers).

```javascript
function greet() {
  console.log(this);
}

greet(); // Logs the Window object
```

Even if you assign a function expression to a variable and then invoke it, the behavior is the same:

```javascript
var sayHello = function() {
  console.log(this);
};

sayHello(); // Logs the Window object
```

This means if you accidentally try to assign a property using `this` in such a function, you might unintentionally add it to the global object, potentially causing conflicts in your code.

```javascript
function addGlobalProperty() {
  this.myNewVar = "Hello from global!";
}

addGlobalProperty();
console.log(window.myNewVar); // Logs "Hello from global!"
console.log(myNewVar);        // Also logs "Hello from global!"
```

#### 3\. Object Method Invocation

When a function is defined as a **method** of an object and then invoked using dot notation (`object.method()`), `this` inside that method refers to the **object itself** that contains the method.

```javascript
var myObject = {
  name: "My C Object",
  logName: function() {
    console.log(this.name); // 'this' refers to 'myObject'
  }
};

myObject.logName(); // Logs "My C Object"
```

This is incredibly useful because it allows a method to access and modify other properties of the same object it belongs to.

```javascript
var car = {
  make: "Toyota",
  model: "Camry",
  updateModel: function(newModel) {
    this.model = newModel; // 'this' refers to 'car'
    console.log(`Car model updated to: ${this.model}`);
  }
};

car.updateModel("Corolla"); // Logs "Car model updated to: Corolla"
console.log(car.model);     // Logs "Corolla"
```

#### 4\. The "Inner Function" Problem

Here's where it gets tricky and often considered a "quirk" of JavaScript. If you have a function *inside* a method, and you invoke that inner function directly, `this` inside the inner function **reverts to pointing to the global object**, even though it's nested within an object's method.

```javascript
var myComplexObject = {
  id: 123,
  displayId: function() {
    console.log(this.id); // 'this' here is myComplexObject (123)

    var innerFunction = function() {
      // Despite being inside displayId, 'this' here refers to the global object (Window)
      console.log(this.id); // This will likely be undefined or a property of the window object
    };

    innerFunction(); // Invoking the inner function directly
  }
};

myComplexObject.displayId();
```

In this example, `this.id` inside `innerFunction` won't refer to `myComplexObject.id`. Instead, it will look for an `id` property on the `window` object, which usually doesn't exist, resulting in `undefined`. If you were to try `this.newProperty = 'value'` inside `innerFunction`, you would again be inadvertently adding `newProperty` to the global object.

-----

### The `self` Pattern: A Solution to the "Inner Function" Problem

To correctly reference the outer `this` (the object) from an inner function, a common pattern is to capture `this` in a variable *before* the inner function is defined. This variable is often named `self` or `that`.

```javascript
var userProfile = {
  name: "Alice",
  updateName: function(newName) {
    // Capture 'this' (which is userProfile) into 'self'
    var self = this;
    console.log(`Current name (from outer 'this'): ${this.name}`); // Alice

    var changeAndLog = function() {
      self.name = newName; // Use 'self' to access the userProfile object
      console.log(`Name updated to (from 'self'): ${self.name}`); // New Name
    };

    changeAndLog();
  }
};

userProfile.updateName("Bob");
// Expected output:
// Current name (from outer 'this'): Alice
// Name updated to (from 'self'): Bob
```

Here's why this works:

1.  When `updateName` is invoked, its `this` keyword correctly points to `userProfile`.
2.  The line `var self = this;` creates a new variable `self` within `updateName`'s execution context. Since objects are assigned by reference, `self` now *points to the exact same `userProfile` object in memory* that `this` was pointing to.
3.  When `changeAndLog` is invoked, it creates its own execution context. If it tried to use `this`, `this` would point to the global object.
4.  However, `changeAndLog` doesn't find `self` within its own variable environment. Due to the **scope chain**, it looks to its outer lexical environment (where `updateName` lives) and finds the `self` variable there, which is still referencing `userProfile`.

This pattern ensures that you consistently refer to the intended object, avoiding the unexpected behavior of `this` inside nested functions. While newer JavaScript features like **arrow functions** (which we'll explore later) offer a cleaner solution to this specific problem, understanding the `self` pattern is crucial as you'll encounter it frequently in existing JavaScript codebases.

