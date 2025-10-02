#### Asynchronous JavaScript

JavaScript is **single-threaded**, meaning it can only do one thing at a time. But many operations are **slow** (HTTP requests, reading files, timers).

To avoid **blocking the main thread**, JavaScript uses **asynchronous patterns**:
- **Callbacks** – old-school way
- **Promises** – modern approach
- **Async/Await** – syntactic sugar over promises



---
#### Promises

A **Promise** is an object representing the **eventual completion or failure** of an asynchronous operation.

**Promise Syntax**
```
const myPromise = new Promise((resolve, reject) => {
    // do async work
    setTimeout(() => {
        const success = true;
        if (success) resolve("Success!");
        else reject("Failure!");
    }, 1000);
});
```
- `resolve(value)` → operation succeeded, value passed to `.then()`
- `reject(error)` → operation failed, error passed to `.catch()`


**Using Promises**
```
myPromise
  .then(result => {
      console.log(result); // "Success!"
      return "Next step";  // can chain another promise
  })
  .then(next => console.log(next))
  .catch(err => console.error(err));
```

**Key points:**
- `.then()` is called when the promise **resolves**.
- `.catch()` handles **any rejection** in the chain.
- Promises can be **chained**, avoiding nested callbacks.


**Parallel** (start both at same time):
```
const [a, b] = await Promise.all([fetchA(), fetchB()]);
```
`Promise.all()` resolves when **all promises** complete, useful for fetching multiple resources at once.