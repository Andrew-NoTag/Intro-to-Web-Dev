# What is JavaScript?

JavaScript, every time a web page does more than just sit there and display static information for you to look at, you can bet that JavaScript is probably involved.

![alt text](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/What_is_JavaScript/cake.png)

- HTML: Content
- CSS: Styling
- JavaScript: Interactions

### What can JavaScript do?

JavaScript Can Change HTML Content

One of many JavaScript HTML methods is `getElementById()`.

The example below "finds" an HTML element (with `id="demo"`), and changes the element content (innerHTML) to "Hello JavaScript":

```js
document.getElementById("demo").innerHTML = "Hello JavaScript";
```

### JavaScript Functions and Events

A JavaScript `function` is a block of JavaScript code, that can be executed when "called" for.

For example, a function can be called when an **_event_** occurs, like when the user clicks a button.

You will learn much more about functions and events in the future.

## How do you add JavaScript to your page?

JavaScript is applied to your HTML page in a similar manner to CSS. Whereas CSS uses `<link>` elements to apply external stylesheets and `<style>` elements to apply internal stylesheets to HTML, JavaScript only needs one friend in the world of HTML — the `<script>`

### Internal JavaScript

In HTML, JavaScript code is inserted between `<script>` and `</script>` tags.

```html
<script>
  //   JavaScript code here!
</script>
```

The code in your web documents is generally loaded and executed in the order it appears on the page.

By placing the JavaScript at the bottom, we ensure that all HTML elements are loaded.

So the `<script>` should normally go just before your closing `</body>` tag

### External JavaScript

Similar to CSS first create a new file in the same directory as your sample HTML file. Call it `script.js`

Add the following just before the closing `</head>` tag (that way the browser can start loading the file sooner than when it's at the bottom):

```html
<script type="module" src="script.js"></script>
```

# Let's build a page with all three cake layers!

Starting internally lets begin with a button in html:

```html
<button type="button">Player 1: Chris</button>
```

Now let's add some CSS

```html
<style>
  button {
    font-family: Roboto Mono, monospace;
    font-size: x-large;
    letter-spacing: 1px;
    text-transform: uppercase;
    border: 2px solid limegreen;
    background-color: pink;
    color: maroon;
    box-shadow: 5px 5px 2px darkgreen;
    border-radius: 10px;
    cursor: pointer;
  }
</style>
```

And finally, we can add some JavaScript to implement dynamic behavior...

```html
<script>
  function updateName() {
    const name = prompt("Enter a new name");
    button.textContent = `Player 1: ${name}`;
  }

  const button = document.querySelector("button");

  button.addEventListener("click", updateName);
</script>
```

> Note: Make sure to preview any sites with JavaScript in your browser!

Now let's do the same thing **_externally_**!
