---
layout: post
title: "Functions"
date: 2018-07-28
categories: [blog/javaScript/]
---

 Objects and Functions.

### 1. **Objects as Collections of Name-Value Pairs**
An object is essentially a collection of name-value pairs where each value can be another collection of name-value pairs. This nesting allows for complex data structures to be built using simple building blocks like primitives and other objects.

**Example:**
```javascript
// A basic object with string, number, boolean properties.
let obj = {
  name: "John Doe",
  age: 30,
  isStudent: false // Another nested object!
};

// The `isStudent` property can be another object:
obj.isStudent = {
  university: "Harvard University",
  enrolled: true
};
```

### 2. **Properties Can Be Primitives, Objects, or Functions**
An object’s properties can hold values of different types:

- **Primitives:** Numbers, strings, booleans.
- **Objects:** Nested objects containing more name-value pairs.
- **Functions:** Either as standalone functions or methods attached to an object.

**Example:**
```javascript
// Object with a mix of primitives and nested objects:
let mixedObj = {
  num1: 42,
  str: "Hello, world!",
  otherObject: { 
    propA: [1, 2, 3], // Array is another type!
    funcRef: () => {} // Function reference
  }
};

// Accessing properties:
console.log(mixedObj.num1); // Output: 42
console.log(mixedObj.str);   // Output: "Hello, world!"
console.log(mixedObj.otherObject.propA[0]); // Output: 1

// Functions as object properties (methods):
let objWithMethods = {
  greet: () => { console.log("Hello!"); },
  addNums: (a, b) => a + b
};

objWithMethods.greet(); // Outputs: "Hello!"
```

### 3. **Functions Are Properties of Objects**
In JavaScript, functions are objects and can be assigned as properties of other objects.

**Example:**
```javascript
// Function references:
let obj = {};
obj.addNumbers = (a, b) => a + b;
console.log(obj.addNumbers(2, 3)); // Outputs: 5

// Adding methods dynamically using Object.defineProperty():
Object.defineProperty(obj, 'logMessage', {
  type: 'function',
  normalizer: function(value) { return value.toUpperCase(); }
});

obj.logMessage("Hello"); // Outputs: "HELLO"
```

### 4. **Methods Are Function Properties**
When you attach a function to an object’s property name (like `obj.methodName`), it becomes a method of that object.

**Example:**
```javascript
// Object with methods attached as properties:
let obj = {
  // Method stored in the 'method' property.
  method: () => { console.log("Method called!"); }
};

obj.method(); // Outputs: "Method called!"
```

### 5. **Objects and Their Memory Addresses**
In JavaScript, objects are stored in memory with their own unique addresses (like pointers). They can reference other properties or methods located at different memory locations.

**Example:**
```javascript
// Two separate objects referencing the same string:
let obj1 = { a: "hello" };
let obj2 = { a: "hello" };

console.log(obj1.a === obj2.a); // Outputs: false (they are distinct instances)
```

### 6. **Nested Objects Are Common**
Objects can contain other objects as properties, creating nested structures.

**Example:**
```javascript
// A deeply nested object:
let data = {
  person: {
    name: "Alice",
    age: 30,
    friends: [
      { id: 1, name: "Bob" },
      { id: 2, name: "Charlie" }
    ]
  }
};

console.log(data.friends[0].id); // Outputs: 1
```

### Summary of Key Points:
- Objects in JavaScript are collections of properties that can hold primitives (numbers, strings), other objects, or functions.
- Functions themselves are a type of property and can be stored as methods on an object when accessed using the method name syntax (`obj.methodName`).
- These nested structures allow for complex data organization but remain manageable because each reference is stored in memory with its own address.

By understanding how properties (including primitives, objects, and functions) relate to one another within a JavaScript object, you can build more sophisticated programs that leverage these relationships.