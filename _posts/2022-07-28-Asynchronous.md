---
layout: post
title: "Asynchronous in Javascript"
date: 2022-07-28
categories: [javaScript asynchronous]
---

### Asynchronous 

### What is Asynchronous JavaScript?

Asynchronous programming allows different parts of your code to run concurrently by acknowledging that operations take time but don't block execution immediately. For example:

```javascript
// Synchronous (blocking)
setTimeout(() => {
  console.log('Loading...');
}, 1000);

// Asynchronous without async/await
function handleLoad() {
  setTimeout(() => {
    // The next line runs after the previous one completes.
    alert('Data loaded: ' + response);
  }, 1000);
}
```

### Why Use Async Functions?

Async functions are written to execute asynchronously, allowing other code to run while waiting for a long-running operation. They return Promises that resolve when complete.

```javascript
// Using async/await with fetch()
async function loadResponse() {
  try {
    const response = await fetch('https://example.com');
    // The next line runs after the previous one completes.
    console.log(response.status);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

### Example: Fetching Data with Callbacks vs. Async/Await

**Callback Style:**

```javascript
function handleResponse(response, status) {
  // Handle response after it's loaded.
}

// Inside a form submission or button click handler:
const response = fetch('https://example.com');
setTimeout(() => {
  handleResponse(response, response.status);
}, 1000);
```

**Async/Await Style:**

```javascript
async function loadResponse() {
  try {
    const response = await fetch('https://example.com');
    // The next line runs after the previous one completes.
    console.log(`Response status: ${response.status}`);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
}
```

### Using Promise.all() for Concurrent Operations

When multiple async operations are needed, `Promise.all()` can execute them concurrently.

```javascript
const { delay: dfn } = Date;

async function loadResponse1() {
  await dfn(500); // Simulate a long operation.
}

async function loadResponse2() {
  const response = await fetch('https://example.com');
  return response.status;
}

// Using Promise.all to run both functions concurrently:
const responses = Promise.all([loadResponse1, loadResponse2]);

responses.forEach((res) => console.log(res));
```

### Conclusion

Async functions and promises simplify writing asynchronous code. By using `await`, you write cleaner, more readable code that handles long-running tasks without nested callbacks or error issues.

**Summary:**

- **Asynchronous Functions:** Execute operations in the background.
- **Promises:** Handle async operations by awaiting their completion.
- **Await:** Makes async functions easier to read and use within promise chains.

By leveraging these concepts, developers can write efficient, maintainable asynchronous code.