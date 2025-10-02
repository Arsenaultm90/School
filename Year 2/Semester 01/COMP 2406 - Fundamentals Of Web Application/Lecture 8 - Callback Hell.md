In JavaScript, a **callback** is a function you pass into another function to run later. This is common in **asynchronous operations** (like reading files, making HTTP requests, or timers).

**Callback hell** happens when you nest many callbacks inside each other, making the code **hard to read, maintain, or debug**.


---
#### Example of Callback Hell

Imagine you want to do these steps **in order**, asynchronously:
1. Get user data
2. Get user’s posts
3. Get comments on the first post

With nested callbacks, it looks like this:
```
getUser(userId, function(user) {
    getPosts(user.id, function(posts) {
        getComments(posts[0].id, function(comments) {
            console.log(comments);
        });
    });
});
```


**Problems here:**
- The code **indents to the right** (“pyramid of doom”).
- Hard to handle errors at each level.
- Difficult to maintain or add extra steps.


**Why Callback Hell Happens**
- **Nesting** callbacks inside callbacks.
- Every new asynchronous operation depends on the previous one.
- Lack of error handling patterns makes it messy.


**Solutions**
a) Named Functions
Instead of anonymous nested callbacks:
```
function handleComments(comments) {
    console.log(comments);
}

function handlePosts(posts) {
    getComments(posts[0].id, handleComments);
}

function handleUser(user) {
    getPosts(user.id, handlePosts);
}

getUser(userId, handleUser);
```
- Reduces indentation.
- Easier to read and debug.

**b) Promises**
Promises let you chain asynchronous operations instead of nesting:
```
getUser(userId)
  .then(user => getPosts(user.id))
  .then(posts => getComments(posts[0].id))
  .then(comments => console.log(comments))
  .catch(err => console.error(err));
```

Benefits:
- **Flatter structure** — no deep nesting.
- **Built-in error handling** with `.catch()`.


**c) Async / Await**
Modern JavaScript allows even cleaner syntax:
```
async function fetchComments() {
    try {
        const user = await getUser(userId);
        const posts = await getPosts(user.id);
        const comments = await getComments(posts[0].id);
        console.log(comments);
    } catch (err) {
        console.error(err);
    }
}

fetchComments();
```
- Looks like **synchronous code**.
- Easy to read, maintain, and debug.
- Still fully asynchronous under the hood.


---
#### Summary

| Problem                   | Solution                   |
| ------------------------- | -------------------------- |
| Deeply nested callbacks   | Use **named functions**    |
| Hard to chain async steps | Use **Promises** (`.then`) |
| Hard to read / debug      | Use **async/await**        |
