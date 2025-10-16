A **template engine** in Node.js allows you to **generate dynamic HTML** on the server side.  
Instead of hardcoding HTML files, you write **templates** that can use **variables, loops, and conditionals**, making it easier to render data dynamically.

For example:
- You have a list of users in a database.
- Instead of manually writing `<li>` tags for each user, you use a template engine to loop through them and generate HTML dynamically.


1. You set up a **view engine** in your Express app.
2. When a client requests a page (like `/users`), the server:
    - Fetches data (e.g., from a database)
    - Passes it to the template engine
    - The engine renders the HTML with the data injected
    - The server sends that HTML to the browser.


**Common Template Engines**
- **Pug** – uses indentation-based syntax (no closing tags)
- **EJS** – uses plain HTML with embedded JavaScript
- **Handlebars** – uses `{{ }}` style placeholders


---
#### Pug

Pug is a **high-performance**, **whitespace-sensitive** template engine that compiles to HTML.  
It’s known for its **clean, minimal syntax**.

**Installation**
```
npm install pug
```

**Setup**(Standard/Express)
```
// Standard Setup
const pug = require('pug');

// Compile template.pug, and render a set of data
console.log(pug.renderFile('template.pug', {
  name: 'Timothy'
}));
// "Timothy's Pug source code!"


// Express Setup
const express = require('express');
const app = express();

app.set('view engine', 'pug');   // tell express to use pug
app.set('views', './views');     // where your .pug files live
```

Now Express automatically looks in the `views` folder for `.pug` templates.

**Attributes :**
```
a(href="https://example.com", target="_blank") Visit Example

// Renders as
<a href="https://example.com" target="_blank">Visit Example</a>

---------------------------------------------------------------

// Javascript Expression
- var link = "https://github.com"
a(href=link) GitHub

---------------------------------------------------------------

// Boolean Expression
input(type="checkbox", checked)

// Render as
<input type="checkbox" checked>

---------------------------------------------------------------

// Dynamic attributes with conditions
input(type="text", disabled=isDisabled)

// If `isDisabled` is true, the attribute appears; if false, it doesn’t.
```


**Conditionals:**
Pug uses standard JavaScript-style `if`, `else if`, and `else`.

```
- var loggedIn = true

if loggedIn
  h2 Welcome back!
else
  h2 Please log in.
  
  ---------------------------------------------------------------
  
// Nested
  if role === 'admin'
  h2 Hello, Admin!
else if role === 'member'
  h2 Hello, Member!
else
  h2 Hello, Guest!

```


**Iterations :**
You can loop through arrays or objects using `each` or `for`.

```
- var users = ['Alice', 'Bob', 'Charlie']

ul
  each user in users
    li= user
    
---------------------------------------------------------------

// Example w/ Object
- var user = { name: 'Alice', age: 25 }

ul
  each val, key in user
    li #{key}: #{val}
    
// Render as
<ul>
  <li>name: Alice</li>
  <li>age: 25</li>
</ul>
```


**Interpolation:**
Pug lets you inject variables into plain text using `=` or `#{}`.

```
p Hello, #{name}!

or

p= message
```


**Example Pug Code :**
`index.pug`
```
doctype html
html
  head
    title User List
  body
    h1 Users

    ul
      each user in users
        if user.active
          li(class="active") #{user.name} (Active)
        else
          li #{user.name} (Inactive)

    a(href="/add", class="button") Add User
```

`data.js`
```
res.render('users', {
  users: [
    { name: 'Alice', active: true },
    { name: 'Bob', active: false },
    { name: 'Charlie', active: true }
  ]
});
```

`Output HTML`
```
<!DOCTYPE html>
<html>
  <head>
    <title>User List</title>
  </head>
  <body>
    <h1>Users</h1>
    <ul>
      <li class="active">Alice (Active)</li>
      <li>Bob (Inactive)</li>
      <li class="active">Charlie (Active)</li>
    </ul>
    <a href="/add" class="button">Add User</a>
  </body>
</html>

```


**Including Other Templates (Layout / Partial)**
You can include reusable parts like headers or footers.

`layout.pug`
```
doctype html
html
  head
    title= title
  body
    include header
    block content
    include footer
```

`header.pug`
```
header
  h1 Site Header
```

`footer.pug`
```
footer
  p Copyright © 2025
```

`index.pug`
```
extends layout

block content
  p This is the homepage.
```


**CSS Classes and ID :**
```
div.main(id="name") -> <div class="main" id="name"></div>
```



---
#### Javascript Insertion

|Symbol|Purpose|Escapes HTML?|Outputs Value?|
|---|---|---|---|
|`-`|Runs **plain JavaScript** (no output)|N/A|❌ No|
|`=`|Runs JS and **inserts escaped output**|✅ Yes|✅ Yes|
|`!=`|Runs JS and **inserts raw/unescaped output**|❌ No|✅ Yes|


1.  **`-` (Plain JavaScript Code)**
`-` tells Pug to **execute a JavaScript statement**, but **don’t print anything**.
You use this for logic, loops, or variable definitions.

```
- var name = 'Matt'
- var items = ['apple', 'banana', 'cherry']

ul
  each item in items
    li= item
```

The `- var` lines run code, but don’t appear in the output.  
The list items **do** appear, because of the `=` sign on the `li`.


2.  **`=` (Output Escaped JavaScript Expression)**
`=` means: “evaluate this expression and **output the result**,” but **escape any HTML** for safety (to prevent injection).

```
- var userInput = "<b>Matt</b>"
p= userInput
```


3. **`!=` (Output Unescaped JavaScript Expression)**
`!=` also outputs the result of an expression, but **without escaping HTML**.

```
- var userInput = "<b>Matt</b>"
p!= userInput
```
