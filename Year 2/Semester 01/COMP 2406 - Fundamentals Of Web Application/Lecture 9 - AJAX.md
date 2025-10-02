#### What is AJAX?

**AJAX** = **Asynchronous JavaScript and XML**

- It’s a technique to **send and receive data from a server without reloading the page**.
- Despite the name, you **don’t have to use XML** — JSON is far more common today.
- It allows your web app to be **dynamic and responsive**, updating parts of the page while leaving the rest intact.

**Example uses:**
- Fetching search results as the user types
- Submitting forms without reloading
- Loading more items in a feed dynamically


---
#### How AJAX Works

AJAX usually involves three key steps:
1. **Create a request** to the server (GET, POST, etc.)
2. **Send the request asynchronously**
3. **Handle the response** once the server replies


---
#### AJAX Using `XMLHttpRequest` (Old Way)

```
const xhr = new XMLHttpRequest();

// 1. Configure the request
xhr.open("GET", "data.json", true); // true = async

// 2. Set up what happens when the response comes back
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        const data = JSON.parse(xhr.responseText);
        console.log(data);
    }
};

// 3. Send the request
xhr.send();
```

**Notes:**
- `readyState === 4` → request finished
- `status === 200` → successful response
- `xhr.responseText` contains the server response as a string


---
#### AJAX Using `fetch()` (Modern Way)

`fetch()` is **simpler and promise-based**, making it easier to avoid callback hell:
```
fetch("data.json")
  .then(response => {
    if (!response.ok) throw new Error("Network error");
    return response.json(); // parse JSON
  })
  .then(data => {
    console.log(data);
  })
  .catch(err => console.error(err));
```

Or using **async/await**:
```
async function getData() {
    try {
        const response = await fetch("data.json");
        if (!response.ok) throw new Error("Network error");
        const data = await response.json();
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}

getData();
```

**Benefits of `fetch`:**
- Cleaner syntax
- Returns a **Promise**, so it integrates easily with `.then()` or `async/await`
- Handles JSON natively


**Example: Updating Page Without Reload**
Imagine a live search bar that queries a server:
```
const searchInput = document.getElementById("search");

searchInput.addEventListener("input", async function() {
    const query = searchInput.value;
    const response = await fetch(`/search?query=${encodeURIComponent(query)}`);
    const results = await response.json();
    
    const resultsDiv = document.getElementById("results");
    resultsDiv.innerHTML = results.map(r => `<p>${r.name}</p>`).join("");
});
```

- Every time the user types, an AJAX request is sent to the server.
- Only the results div is updated — the page doesn’t reload.


---
#### Key Points

|Aspect|Description|
|---|---|
|Asynchronous|Doesn’t block the page while waiting for the server|
|Response format|Can be JSON, XML, HTML, or plain text|
|Old way|`XMLHttpRequest`|
|Modern way|`fetch()` (Promise-based)|
|Error handling|Use `status` or `.catch()` for network errors|
