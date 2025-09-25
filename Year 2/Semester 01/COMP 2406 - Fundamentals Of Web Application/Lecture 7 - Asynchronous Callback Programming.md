Asynchronous programming is a technique that enables your program to start a potentially long-running task and still be able to be responsive to other events while that task runs, rather than having to wait until that task has finished. Once that task has finished, your program is presented with the result.


---
#### The Issue with Synchronous Code

```
console.log("Start");
const data = fetchData(); // Imagine this takes 3 seconds
console.log("Data:", data);
console.log("End");
```
- `fetchData()` blocks everything until it returns.
- The user interface (UI) becomes unresponsive during that time.


---
#### Callbacks

The earliest way to handle async tasks.
```
console.log("Start");

setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);

console.log("End");
```
- `setTimeout` doesn’t block; the code continues.
- Callback functions run later when the task completes.
- **Problem:** Deeply nested callbacks → “callback hell”.


---
#### Promises

A more structured way to handle async operations.
```
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success!");
  }, 2000);
});

promise
  .then(result => {
    console.log(result); // "Success!"
  })
  .catch(error => {
    console.error(error);
  });
```

Promise represents a value that may be available now, later, or never.
	`.then()` handles success.
	`.catch()` handles errors.
	`.finally()` runs regardless of success or failure.
	`resolve` and `reject` are **functions**, that the executor calls when the operation succeeds or fails.

**Executor:**
- The function passed to `new Promise()`
- **Purpose:** Start the async operation and tell the Promise whether it succeeded (`resolve`) or failed (`reject`).
- **Runs immediately**; it’s not async itself (only the operations inside it can be async


---
#### Async Await

Syntactic sugar over Promises. Makes async code look synchronous.
```
async function fetchData() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

fetchData();
```
- `async` function always returns a Promise.
- `await` pauses **inside the async function** until the Promise resolves.
- Error handling is easier with `try/catch`.


---
#### Event Loop

The secret sauce behind async in JS:
- **Call stack:** Runs functions.
- **Web APIs / Node APIs:** Handle timers, HTTP requests, etc.
- **Callback queue / Microtask queue:** Where async results go.
- **Event loop:** Picks tasks from the queue when the call stack is empty.

This is why your async code runs _after_ synchronous code, even if the timer is 0 ms.


---
#### Common Async Patterns

- **AJAX / Fetch:** Fetch data from server.
- **Timers:** `setTimeout`, `setInterval`.
- **Promises:** Any operation that will complete in the future.
- **Async Iteration:** `for await (const item of asyncIterable)`.
- **Web Workers:** Run heavy tasks in separate threads.


---


