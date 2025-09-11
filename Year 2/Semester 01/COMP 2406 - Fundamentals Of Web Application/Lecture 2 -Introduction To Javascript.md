


#### Code Bits

Run JS from Node : `Node my_file.js`
Script in HTML: `<script> ...Javascript here... </script>`
Script externally: `<script src="01-ex1-helloworld.js"></script>`

**Values for False**
1. false (the Boolean value)  
2. 0 (the number 0)  
3. “” (the empty string)  
4. null  
5. undefined  
6. NaN


---
#### Summary

**Variables**
- `var` – function scoped (old, avoid).
- `let` – block scoped (preferred for reassignable values).
- `const` – block scoped, cannot be reassigned.
```
let x = 10;
const y = 20;
```

**Data Types**
- Primitive: `string`, `number`, `boolean`, `null`, `undefined`, `bigint`, `symbol`
- Objects: `{}`, arrays `[]`, functions `function(){}`
```
typeof 42; // "number"
typeof "hi"; // "string"
```

**Operators**
- Arithmetic: `+ - * / % **`
- Assignment: `= += -= *= /=`
- Comparison: `== != === !== > < >= <=`
- Logical: `&& || !`
- Ternary: `condition ? val1 : val2`

**Control Flow**
```
if (x > 10) {
  console.log("big");
} else if (x === 10) {
  console.log("equal");
} else {
  console.log("small");
}

switch (day) {
  case "Mon": console.log("Start"); break;
  default: console.log("Other");
}
```

**Loops**
```
for (let i=0; i<5; i++) { console.log(i); }
while (i < 5) { i++; }
do { i++; } while (i < 5);

for (let item of array) { console.log(item); }
for (let key in obj) { console.log(obj[key]); }
```

**Functions**
```
function add(a, b) { return a+b; }        // normal
const sub = (a,b) => a-b;                 // arrow function
(function(){ console.log("IIFE"); })();   // immediately invoked
```

**Objects**
```
let person = {
  name: "Alice",
  age: 25,
  greet() { console.log("Hi " + this.name); }
};

console.log(person.name);
person.greet();

// Destructuring
const {name, age} = person;
```

**Arrays**
```
let arr = [1,2,3];
arr.push(4);
arr.pop();
arr.shift();
arr.unshift(0);

arr.forEach(x => console.log(x));
let newArr = arr.map(x => x*2);
let evens = arr.filter(x => x%2===0);
let sum = arr.reduce((a,b)=>a+b,0);
```

**DOM Manipulation**
```
document.getElementById("id");
document.querySelector(".class");
document.querySelectorAll("div");

let el = document.createElement("p");
el.textContent = "Hello";
document.body.appendChild(el);
```

**Events**
```
button.addEventListener("click", () => alert("Clicked!"));
```

**Classes**
```
class Animal {
  constructor(name) { this.name = name; }
  speak() { console.log(this.name + " makes a sound"); }
}
class Dog extends Animal {
  speak() { console.log(this.name + " barks"); }
}
let d = new Dog("Rex");
d.speak();
```

**Asynchronous JS**
Callbacks
Promises
```
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

Async/await
```
async function getData() {
  try {
    let res = await fetch(url);
    let data = await res.json();
    console.log(data);
  } catch(err) {
    console.error(err);
  }
}
```

**JSON**
```
let obj = {x:1, y:2};
let str = JSON.stringify(obj);
let back = JSON.parse(str);
```
