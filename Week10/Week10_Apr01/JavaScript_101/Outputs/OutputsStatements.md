## Outputs

JavaScript does not have any built in display functions.

It does however have a few useful built in functions to help us see our data, check our functions, or check for errors. Today will will be using:

- `.innerHTML` – change the text between the opening and closing tags of an HTML element of our choosing.

```
document.getElementById("output").innerHTML = "I just changed the content of this div using JavaScript";
```

- `alert();` – displays a pop up window with the data we pass in to the ()

```
alert(“Hello World!”);
```

- `console.log();` – logs data to the javascript console (we can access this with Google Developer Tools or Firebug)

```
console.log(“this is my first console log!”);
```

### Using `innerHTML`

To access an HTML element, you can use the `document.getElementById(id)` method.

Use the `id` attribute to identify the HTML element.

Then use the `innerHTML` property to change the HTML content of the HTML element:

```html
<p id="demo"></p>

<script>
  document.getElementById("demo").innerHTML = "Hello Howdy!";
</script>
```

#### Note

> Use `innerHTML` when you want to change an HTML element.

> Use `innerText` when you only want to change the plain text.

### Using `alert`

You can use an alert box to display data:

```html
<script>
  alert(5 + 6);
</script>
```

### Using `console.log()`

For debugging purposes, you can call the console.log() method in the browser to display data.

```html
<script>
  console.log("woohoo");
</script>
```

## Statements

We have these variables:

```js
let x, y, z;
x = 5;
y = 6;
z = x + y;
```

Using these variables we can create programming instructions or **_statements_**.

JavaScript statements are composed of: Values, Operators, Expressions, Keywords, and Comments.

```html
<p id="demo"></p>

<script>
  let x, y, z;
  x = 5;
  y = 6;
  z = x + y;

  document.getElementById("demo").innerHTML = "The value of z is " + z + ".";
</script>
```

This statement tells the browser to write "Hello Dolly." inside an HTML element with id="demo":

```js
document.getElementById("demo").innerHTML = "Hello Dolly.";
```

### Semicolons `;`

Semicolons separate JavaScript statements.

Add a semicolon at the end of each executable statement:

```js
let a;
a = 100000;

// as long as separated by semicolons, multiples are allowed on one line
```

### JavaScript Code Blocks

JavaScript statements can be grouped together in code blocks, inside curly brackets `{...}`.

The purpose of code blocks is to define statements to be executed together.

One place you will find statements grouped together in blocks, is in JavaScript functions:

```js
function myFunction() {
  document.getElementById("demo1").innerHTML = "Hello Dolly!";
  document.getElementById("demo2").innerHTML = "How are you?";
}
```

> Note: VS Code has a great extension called "Prettier - Code formatter". I recommend getting it as it makes it easier to keep your code neat.

![Prettier app](https://esbenp.gallerycdn.vsassets.io/extensions/esbenp/prettier-vscode/11.0.0/1723648421534/Microsoft.VisualStudio.Services.Icons.Default)
