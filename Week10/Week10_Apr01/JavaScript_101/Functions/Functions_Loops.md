## Functions

### Syntax

Functions contain the `function` keyword, followed by a function name of your choosing, followed by parenthesis `()` where parameters can be passed into our function. The code for the function to execute is then listed within the curly brackets `{}`:

```js
function myFunctionName(parameter1, parameter2) {
  //javascript statements for this function here
}
```

A JavaScript function is a block of code which performs a particular task.

Functions need to be invoked in order to execute.

This is usually done when a particular event occurs or when it is called within another function. You will see in our demos today that we can’t just simply declare variables and write functions and expect it to execute. ([w3 Schools Functions Explained](https://www.w3schools.com/js/js_functions.asp))

#### Function firing when a button is clicked:

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <script type="text/javascript">
      function sumValues(a, b) {
        var sum = a + b;
        console.log("Your total charges are: " + sum + ".");
      }
    </script>
  </head>
  <body>
    <button onclick="sumValues(7,23.6);">View Total</button>
  </body>
</html>
```

Notice in the above example, we have to attach the function to the onclick event listener. We are passing the numbers 7 and 23.6 in as our two parameters a and b to our function. There are many other event listeners. You can view them here. We could also pass values in from a form or some other user input as variables. Here they are hardcoded in.

#### Functions being called when a page loads:

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <script type="text/javascript">
      function sumValues(a, b) {
        var sum = a + b;
        console.log("Your total charges are: " + sum + ".");
      }
    </script>
  </head>
  <body onload="sumValues(12.2 , 17.74)"></body>
</html>
```

Here we called a function when the body of our HTML page has loaded.

We can also call functions within functions. Sometimes you want many different functions to invoke when the page loads, but you may want to use them separately again later.

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <script type="text/javascript">
      function startMe() {
        sumValues(56.7, 34.6);
      }

      function sumValues(a, b) {
        var sum = a + b;
        console.log("Your total charges are: " + sum + ".");
      }
    </script>
  </head>

  <body onload="startMe();">
    <button onclick="sumValues(235,3756);">Click Me</button>
  </body>
</html>
```

### Boolean Function and Comparisons

Sometimes we need data types to only return TRUE or FALSE. For example, has the user entered all of their data in the form correctly? or is a clickable element displayed in the ON or OFF position? We can do this with JavaScript Boolean function but we usually use Comparisons and Conditionals.

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <script type="text/javascript">
      //This global variable is a boolean. it can only be null, true, or false
      var isOn = true;

      function switchOnOff() {
        if (isOn == true) {
          alert("isOn is set to true. Switching to false now.");
          isOn = false;
        } else {
          alert("isOn is set to false. Switching to true now.");
          isOn = true;
        }
      }
    </script>
  </head>

  <body>
    <button onclick="switchOnOff()">
      Click me Switch the Boolean Variable back and Forth
    </button>
  </body>
</html>
```

## For Loops

Sometimes you need to perform a task/function multiple times. Rather than writing the same statement over and over in a function, we can use use Loops. There are several kinds of loops you can read more about them here. Today we will look at a simple for loop.

```js
for (statement 1; statement 2; statement 3) {
    code block to be executed
}
```

Statement 1 is executed before the loop (the code block) starts. This is usually when we set an intital number for our counter.

Statement 2 defines the condition for running the loop (the code block). As long as the condition is TRUE the code will keep executing. Beware of infinite loops!

Statement 3 is executed each time after the loop (the code block) has been executed. This is usually where we increment our counter.

Here we are passing in the number 25 to our for loop with the parameter n. The code inside our for loop with execute 25 times. Notice how the console.log() stops at 24. That is because the the loop only executes while the number is less than 25.

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <script type="text/javascript">
      function countToN(n) {
        for (var i = 0; i < n; i++) {
          console.log(i);
        }
      }
    </script>
  </head>

  <body>
    <button onclick="countToN(25);">Click Me to Start the Loop</button>
  </body>
</html>
```

You will notice in the above code. The third statement in our for loop is:

```
i++;
```

Using ++ or — we can increment or decrement the value of i by 1. It is shorthand for writing:

```
i = i+1;
```

If we want to increment or decrement by another number it is written like so:

```
i+=2;
j-=10;
```

These larger increments are great for alternating odd and even numbers or doing cool pixel manipulations.

### Practice exercise:

Let's go back to the Output statements we learned about and activate them using buttons. Then decorate the buttons with simple internal CSS.
