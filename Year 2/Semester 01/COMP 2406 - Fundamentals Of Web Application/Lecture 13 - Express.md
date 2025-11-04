**Express** is a lightweight, flexible framework for building web applications and APIs in **Node.js.**
It abstracts away some of the boilerplate of Node’s built-in HTTP module, making it easier to handle routes, requests, responses, and middleware.

**Key features:**
- Routing (mapping URLs to handlers)
- Middleware support (functions that handle requests/responses)
- Template engine support (rendering HTML)
- Easy handling of JSON, URL-encoded data, and static files
- Supports RESTful API design

**Installing:**
```
$npm install express

temp
$npm install express --no-save
```

**Create Express App:**
```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

**Routing:**
```
app.METHOD(PATH, HANDLER)
```
- `app` is an instance of `express`.
- `METHOD` is an [HTTP request method](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods), in lowercase.
- `PATH` is a path on the server.
- `HANDLER` is the function executed when the route is matched.

Example :
```
app.get('/', (req, res) => {
  res.send('Hello World!')
})
```


| Property  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Type     | Default              |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | -------------------- |
| `inflate` | Enables or disables handling deflated (compressed) bodies; when disabled, deflated bodies are rejected.                                                                                                                                                                                                                                                                                                                                                                                                                        | Boolean  | `true`               |
| `limit`   | Controls the maximum request body size. If this is a number, then the value specifies the number of bytes; if it is a string, the value is passed to the [bytes](https://www.npmjs.com/package/bytes) library for parsing.                                                                                                                                                                                                                                                                                                     | Mixed    | `"100kb"`            |
| `reviver` | The `reviver` option is passed directly to `JSON.parse` as the second argument. You can find more information on this argument [in the MDN documentation about JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse#Example.3A_Using_the_reviver_parameter).                                                                                                                                                                                                                | Function | `null`               |
| `strict`  | Enables or disables only accepting arrays and objects; when disabled will accept anything `JSON.parse` accepts.                                                                                                                                                                                                                                                                                                                                                                                                                | Boolean  | `true`               |
| `type`    | This is used to determine what media type the middleware will parse. This option can be a string, array of strings, or a function. If not a function, `type` option is passed directly to the [type-is](https://www.npmjs.org/package/type-is#readme) library and this can be an extension name (like `json`), a mime type (like `application/json`), or a mime type with a wildcard (like `*/*` or `*/json`). If a function, the `type` option is called as `fn(req)` and the request is parsed if it returns a truthy value. | Mixed    | `"application/json"` |
| `verify`  | This option, if supplied, is called as `verify(req, res, buf, encoding)`, where `buf` is a `Buffer` of the raw request body and `encoding` is the encoding of the request. The parsing can be aborted by throwing an error.                                                                                                                                                                                                                                                                                                    | Function | `undefined`          |




---
#### Static Files In Express

To serve static files such as images, CSS files, and JavaScript files, use the `express.static` built-in middleware function in Express.

Function Signature:
```
express.static(root, [options])
```

Example:
```
app.use(express.static('public'));
```

Now, any files in the `public` folder can be accessed directly:
```
public/style.css -> http://localhost:3000/style.css
```


---
#### Template Engines

Express can render dynamic HTML using template engines like **EJS**, **Pug**, or **Handlebars**.

After the view engine is set, you don’t have to specify the engine or load the template engine module in your app; Express loads the module internally, for example:
```
app.set('view engine', 'pug')
```

Then, create a Pug template file named `index.pug` in the `views` directory, with the following content:
```
html
  head
    title= title
  body
    h1= message
```

Create a route to render the `index.pug` file. If the `view engine` property is not set, you must specify the extension of the `view` file. Otherwise, you can omit it.
```
app.get('/', (req, res) => {
  res.render('index', { title: 'Hey', message: 'Hello there!' })
})
```

The view engine cache does not cache the contents of the template’s output, only the underlying template itself. The view is still re-rendered with every request even when the cache is on.