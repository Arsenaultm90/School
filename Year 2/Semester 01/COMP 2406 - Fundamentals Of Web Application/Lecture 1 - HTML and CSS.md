**HTML Basic Structure**
```
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is HTML</p>
  </body>
</html>
```

**Common Tags**
- **Headings**: `<h1>` … `<h6>`
- **Text**: `<p>`, `<span>`, `<br>`, `<hr>`
- **Formatting**: `<b>`, `<i>`, `<strong>`, `<em>`, `<u>`
- **Links**: `<a href="url" target="_blank">Link</a>`
- **Images**: `<img src="img.jpg" alt="desc">`
- **Semantic Elements**: `<header>`, `<nav>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<main>`

**Attributes**
- `id`, `class` → for styling / JS
- `src`, `href`, `alt`, `title`
- `style` → inline CSS
- Boolean: `checked`, `disabled`, `required`


---
#### CSS

**Syntax**
```
selector {
  property: value;
}
```

**Selectors**
- Tag: `p {}`
- Class: `.class {}`
- ID: `#id {}`
- Descendant: `div p {}`
- Child: `div > p {}`
- Pseudo-class: `a:hover {}`
- Pseudo-element: `p::first-line {}`
- Attribute: `input[type="text"] {}`

**Colors**
- Names: `red`
- Hex: `#ff0000`
- RGB: `rgb(255,0,0)`
- RGBA: `rgba(255,0,0,0.5)`
- HSL: `hsl(0,100%,50%)`

**Text & Fonts**
```
p {
  color: blue;
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: bold;
  text-align: center;
  text-decoration: underline;
}
```

**Box Model**
```
div {
  width: 200px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

**Display & Position**
- `display: block | inline | inline-block | flex | grid | none`
- Position: `static | relative | absolute | fixed | sticky`

```
.box {
  position: absolute;
  top: 20px;
  left: 30px;
}
```

**Flexbox**
```
.container {
  display: flex;
  justify-content: space-between; /* main axis */
  align-items: center;            /* cross axis */
}
```

**Grid**
```
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 10px;
}
```

**Backgounds**
```
div {
  background-color: lightblue;
  background-image: url("bg.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}
```

**Transitions & Animation**
```
.box {
  transition: all 0.5s;
}
.box:hover {
  transform: scale(1.2);
}

@keyframes slide {
  from { left: 0; }
  to { left: 100px; }
}
.box {
  animation: slide 2s infinite;
}
```

**Responsive Design**
```
@media (max-width: 600px) {
  body { font-size: 14px; }
}
```

**CSS Variables**
```
:root { --main-color: blue; }
h1 { color: var(--main-color); }
```
