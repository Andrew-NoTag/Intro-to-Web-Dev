# JavaScript Class Exercise

### Thinking like a programmer

How do we apply programming syntax to real world problems?

You need to start thinking like a programmer:

- looking at descriptions of what your program needs to do
- working out what code features are needed to achieve those things
- how to make them work together.

_**The more you code, the better you'll get at it.**_

### Example — Guess the number game

[Here](https://samdear.github.io/GuessNumber/index.html) is an example of what we will bre creating today!

Let's imagine your boss has given you the following brief for creating this game:

    I want you to create a simple "guess the number" type game. It should choose a random number between 1 and 100, then challenge the player to guess the number in 10 turns. After each turn, the player should be told if they are right or wrong, and if they are wrong, whether the guess was too low or too high. It should also tell the player what numbers they previously guessed. The game will end once the player guesses correctly, or once they run out of turns. When the game ends, the player should be given an option to start playing again.

---

### Breakdown

1.  Generate a random number between 1 and 100.

2.  Record the turn number the player is on. Start it on 1.

3.  Provide the player with a way to guess what the number is.

4.  Once a guess has been submitted first record it somewhere so the user can see their previous guesses.

5.  Next, check whether it is the correct number.

6.  If it is correct:

    - Display congratulations message.
    - Stop the player from being able to enter more guesses (this would mess the game up).

    - Display control allowing the player to restart the game.

7.  If it is wrong and the player has turns left:

    - Tell the player they are wrong and whether their guess was too high or too low.
    - Allow them to enter another guess.
    - Increment the turn number by 1.

8.  If it is wrong and the player has no turns left:

    - Tell the player it is game over.
    - Stop the player from being able to enter more guesses (this would mess the game up).
    - Display control allowing the player to restart the game.

9.  Once the game restarts, make sure the game logic and UI are completely reset, then go back to step 1.

Here is the base HTML file you will use:

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />

    <title>Number guessing game</title>

    <style>
      html {
        font-family: sans-serif;
      }

      body {
        width: 50%;
        max-width: 800px;
        min-width: 480px;
        margin: 0 auto;
      }

      .form input[type="number"] {
        width: 200px;
      }

      .lastResult {
        color: white;
        padding: 3px;
      }
    </style>
  </head>

  <body>
    <h1>Number guessing game</h1>

    <p>
      We have selected a random number between 1 and 100. See if you can guess
      it in 10 turns or fewer. We'll tell you if your guess was too high or too
      low.
    </p>

    <div class="form">
      <label for="guessField">Enter a guess: </label>
      <input
        type="number"
        min="1"
        max="100"
        required
        id="guessField"
        class="guessField"
      />
      <input type="submit" value="Submit guess" class="guessSubmit" />
    </div>

    <div class="resultParas">
      <p class="guesses"></p>
      <p class="lastResult"></p>
      <p class="lowOrHi"></p>
    </div>

    <script>
      // Your JavaScript goes here
    </script>
  </body>
</html>
```

For simplicity, we will be doing all our coding internally.

```html
<script>
  // Your JavaScript goes here
</script>
```

### Adding variables to store our data

Let's get started.

First of all, add the following lines inside your `<script>` element:

```js
let randomNumber = Math.floor(Math.random() * 100) + 1;

const guesses = document.querySelector(".guesses");
const lastResult = document.querySelector(".lastResult");
const lowOrHi = document.querySelector(".lowOrHi");

const guessSubmit = document.querySelector(".guessSubmit");
const guessField = document.querySelector(".guessField");

let guessCount = 1;
let resetButton;
```

The `querySelector()` method returns the first child element that matches a specified CSS selector(s) of an element.

_`getElementById()` only works with ID attributes, while `querySelector()` can work with any CSS selector_

This section of the code sets up the `variables` and `constants` we need to store the data our program will use.

    What is the difference between var and const in JavaScript?

`Variables` are basically names for values (such as numbers, or strings of text). You create a variable with the keyword let followed by a name for your variable.

`Constants` are also used to name values, but unlike variables, you can't change the value once set.

In this case, we are using constants to store references to parts of our user interface. The text inside some of these elements might change, but each constant always references the same HTML element that it was initialized with. You create a constant with the keyword const followed by a name for the constant.

You can assign a value to your variable or constant with an equals sign `=` followed by the value you want to give it.

In our example:

The first variable — randomNumber — is assigned a random number between 1 and 100, calculated using a mathematical algorithm.

- The `Math.floor()` method rounds a number DOWN to the nearest integer.

- The `Math.random()` method returns a random floating point number between 0 (inclusive) and 1 (exclusive).

        How are we able to use math, floor, and random without declaring them?

The first three constants are each made to store a reference to the results paragraphs in our HTML, and are used to insert values into the paragraphs later on in the code (note how they are inside a `<div>` element, which is itself used to select all three later on for resetting, when we restart the game):

```html
<div class="resultParas">
  <p class="guesses"></p>
  <p class="lastResult"></p>
  <p class="lowOrHi"></p>
</div>
```

The next two constants store references to the form text input and submit button and are used to control submitting the guess later on.

```html
<label for="guessField">Enter a guess: </label>
<input type="number" id="guessField" class="guessField" />
<input type="submit" value="Submit guess" class="guessSubmit" />
```

Our final two variables store a guess count of 1 (used to keep track of how many guesses the player has had), and a reference to a reset button that doesn't exist yet (but will later).

### Functions

    How do you define a function in JavaScript, and what does the syntax look like?

Next, add the following below your previous JavaScript:

```js
function checkGuess() {
  alert("I am a placeholder");
}
```

    What is the purpose of a function in JavaScript, and why is it useful to use functions in your code?

Functions are reusable blocks of code that you can write once and run again and again, saving the need to keep repeating code all the time.

Here we have defined a function by using the keyword function, followed by a name, with parentheses put after it.

After that, we put two curly braces `{ }`. Inside the curly braces goes all the code that we want to run whenever we call the function.s

When we want to run the code, we type the name of the function followed by the parentheses.

    What is going to happen if we run the function checkGuess()?

Let's try that now.

Go into the developer tools JavaScript console, and enter the following line:

```js
checkGuess();
```

After pressing `Return/Enter`, you should see an alert come up that says I am a placeholder; we have defined a function in our code that creates an alert whenever we call it.

    Why would we want to define a function like checkGuess even though it currently only shows an alert? How might this be useful later?

### Operators

    What is an operator in JavaScript?

JavaScript operators allow us to perform tests, do math, join strings together, and other such things.

| **Operator** | **Description**              |
| ------------ | ---------------------------- |
| **+**        | Addition                     |
| **-**        | Subtraction                  |
| **\***       | Multiplication               |
| **\*\***     | Exponentiation (ES2016)      |
| **/**        | Division                     |
| **%**        | Modulus (Division Remainder) |
| **++**       | Increment                    |
| **--**       | Decrement                    |

There are also some shortcut operators available, called compound assignment operators.

| Operator | Description                                                          |
| -------- | -------------------------------------------------------------------- |
| `=`      | Assignment operator (assigns value on the right to the left operand) |
| `*=`     | Multiplication assignment                                            |
| `/=`     | Division assignment                                                  |
| `%=`     | Remainder (modulo) assignment                                        |
| `+=`     | Addition assignment                                                  |
| `-=`     | Subtraction assignment                                               |
| `<<=`    | Left shift assignment                                                |
| `>>=`    | Right shift assignment                                               |
| `>>>=`   | Unsigned right shift assignment                                      |
| `&=`     | Bitwise AND assignment                                               |
| `^=`     | Bitwise XOR assignment                                               |
| `\|=`    | Bitwise OR assignment                                                |
| `**=`    | Exponentiation assignment                                            |
| `&&=`    | Logical AND assignment                                               |
| `\|\|=`  | Logical OR assignment                                                |
| `??=`    | Nullish coalescing assignment                                        |

For example, if you want to add a new number to an existing one and return the result, you could do this:

```js
let number1 = 1;
number1 += 2;
```

This is equivalent to

```js
let number2 = 1;
number2 = number2 + 2;
```

When we are running `true/false` tests (for example inside conditionals — see below) we use comparison operators.

For example:
| Operator | Name | Example |
|----------|------------------------|-------------------------------------------|
| `===` | Strict equality (is it exactly the same?) | `5 === 2 + 4 // false`<br>`Chris === Bob // false`<br>`5 === 2 + 3 // true`<br>`2 === 2 // false; number versus string` |
| `!==` | Non-equality (is it not the same?) | `5 !== 2 + 4 // true`<br>`Chris !== Bob // true`<br>`5 !== 2 + 3 // false`<br>`2 !== 2 // true; number versus string` |
| `<` | Less than | `6 < 10 // true`<br>`20 < 10 // false` |
| `>` | Greater than | `6 > 10 // false`<br>`20 > 10 // true` |

### Text strings

Strings are used for representing text.

    What is the string we've already used in the code?

```js
function checkGuess() {
  alert("I am a placeholder");
}
```

You can declare strings using double quotes `"` or single quotes `'`, but you must use the same form for the start and end of a single string declaration: you **can't** write `"I am a placeholder'`.

You can also declare strings using backticks **`**.

Strings declared like this are called `template literals` and have some special properties. In particular, you can embed other variables or even expressions in them:

```js
const name = "Mahalia";

const greeting = `Hello ${name}`;
```

This gives you a mechanism to join strings together.

#### Why not use `+`?

##### Readability and Simplicity

- Using `+`: When concatenating multiple strings or variables, the `+` operator can make the code harder to read, especially when you have several values to join.

```js
const name = "Mahalia";
const age = 25;
const greeting = "Hello " + name + ", you are " + age + " years old.";
console.log(greeting); // Output: Hello Mahalia, you are 25 years old.
```

- Using Template Literals: Template literals make it clearer and more readable by embedding variables directly within the string.

```js
const name = "Mahalia";
const age = 25;
const greeting = `Hello ${name}, you are ${age} years old.`;
console.log(greeting); // Output: Hello Mahalia, you are 25 years old.
```

- Why it’s better: The template literal is cleaner, and you don't have to worry about adding spaces or dealing with the complexity of + when you have multiple variables.

### Conditionals

Returning to our `checkGuess()` function, we want it to check whether a player's guess is correct or not, and respond appropriately.

At this point, replace your current `checkGuess()` function with this version instead:

```js
function checkGuess() {
  const userGuess = Number(guessField.value);
  if (guessCount === 1) {
    guesses.textContent = "Previous guesses:";
  }
  guesses.textContent = `${guesses.textContent} ${userGuess}`;

  if (userGuess === randomNumber) {
    lastResult.textContent = "Congratulations! You got it right!";
    lastResult.style.backgroundColor = "green";
    lowOrHi.textContent = "";
    setGameOver();
  } else if (guessCount === 10) {
    lastResult.textContent = "!!!GAME OVER!!!";
    lowOrHi.textContent = "";
    setGameOver();
  } else {
    lastResult.textContent = "Wrong!";
    lastResult.style.backgroundColor = "red";
    if (userGuess < randomNumber) {
      lowOrHi.textContent = "Last guess was too low!";
    } else if (userGuess > randomNumber) {
      lowOrHi.textContent = "Last guess was too high!";
    }
  }

  guessCount++;
  guessField.value = "";
  guessField.focus();
}
```

This is a lot of code — phew! Let's go through each section and explain what it does.

```js
const userGuess = Number(guessField.value);
if (guessCount === 1) {
  guesses.textContent = "Previous guesses:";
}
```

The first line declares a variable called `userGuess` and sets its value to the current value entered inside the text field.

- We also run this value through the built-in `Number()` constructor, just to make sure the value is definitely a number. Since we're not changing this variable, we'll declare it using const.

Next, we encounter our first conditional code block.

- A conditional code block allows you to run code selectively, depending on whether a certain condition is true or not.

It looks a bit like a function, but it isn't.

- The simplest form of conditional block starts with the keyword `if`, then some parentheses, then some curly braces.

- Inside the parentheses, we include a test. If the test returns true, we run the code inside the curly braces.

  - If not, we don't, and move on to the next bit of code.

- In this case, the test is testing whether the guessCount variable is equal to 1 (i.e. whether this is the player's first go or not):

```js
guessCount === 1;
```

- If it is, we make the guesses paragraph's text content equal to Previous guesses:. If not, we don't.

Next, we use a template literal to append the current `userGuess` value onto the end of the guesses paragraph, with a blank space in between.

```js
guesses.textContent = `${guesses.textContent} ${userGuess}`;
```

The next block does a few checks:

The first if (){ } checks whether the user's guess is equal to the randomNumber set at the top of our JavaScript. If it is, the player has guessed correctly and the game is won, so we show the player a congratulations message with a nice green color, clear the contents of the Low/High guess information box, and run a function called `setGameOver()`, which we'll discuss later.

```js
if (userGuess === randomNumber) {
  lastResult.textContent = "Congratulations! You got it right!";
  lastResult.style.backgroundColor = "green";
  lowOrHi.textContent = "";
  setGameOver();
}
```

Now we've chained another test onto the end of the last one using an `else if (){ }` structure.

```js
else if (guessCount === 10) {
          lastResult.textContent = "!!!GAME OVER!!!";
          lowOrHi.textContent = "";
          setGameOver();
        }
```

- This one checks whether this turn is the user's last turn.

If it is, the program does the same thing as in the previous block, except with a game over message instead of a congratulations message.

The final block chained onto the end of this code (the `else { }`) contains code that is only run if neither of the other two tests returns true (i.e. the player didn't guess right, but they have more guesses left).

```js
else {
          lastResult.textContent = "Wrong!";
          lastResult.style.backgroundColor = "red";
          if (userGuess < randomNumber) {
            lowOrHi.textContent = "Last guess was too low!";
          } else if (userGuess > randomNumber) {
            lowOrHi.textContent = "Last guess was too high!";
          }
        }
```

In this case we tell them they are wrong, then we perform another conditional test to check whether the guess was higher or lower than the answer, displaying a further message as appropriate to tell them higher or lower.

The last three lines in the function get us ready for the next guess to be submitted.

```js
guessCount++;
guessField.value = "";
guessField.focus();
```

- We add 1 to the `guessCount` variable so the player uses up their turn (`++` is an increment operation: increase by 1), and empty the value out of the form text field and focus it again, ready for the next guess to be entered.

### Events

    Why won't checkGuess() function do anything?

We haven't called it yet!

Ideally, we want to call it when the "Submit guess" `button` is pressed, and to do this we need to use an event.

Event listeners observe specific events and call event handlers.

- Blocks of code that run in response to an event firing.

Add the following line below your `checkGuess()` function:

```js
guessSubmit.addEventListener("click", checkGuess);
```

Here we are adding an event listener to the guessSubmit button.

This is a method that takes two input values (called `arguments`) — the type of event we are listening out for (in this case click) as a string, and the code we want to run when the event occurs (in this case the checkGuess() function).

_Note: that we don't need to specify the parentheses when writing it inside `addEventListener()`._

Try saving and refreshing your code now, and your example should work — to a point.

The only problem now is that if you guess the correct answer or run out of guesses, the game will break.

    Why?

We've not yet defined the s`etGameOver()` function that is supposed to be run once the game is over.

Let's add our missing code now and complete the example functionality.

### Finishing the game functionality

Let's add that `setGameOver()` function to the bottom of our code:

```js
function setGameOver() {
  guessField.disabled = true;
  guessSubmit.disabled = true;
  resetButton = document.createElement("button");
  resetButton.textContent = "Start new game";
  document.body.append(resetButton);
  resetButton.addEventListener("click", resetGame);
}
```

The first two lines disable the form text input and button by setting their disabled properties to `true`.

```js
guessField.disabled = true;
guessSubmit.disabled = true;
```

This is necessary, because if we didn't, the user could submit more guesses after the game is over, which would mess things up.

The next three lines generate a new `<button>` element, set its text label to "Start new game", and add it to the bottom of our existing HTML.

```js
resetButton = document.createElement("button");
resetButton.textContent = "Start new game";
document.body.append(resetButton);
```

The final line sets an event listener on our new button so that when it is clicked, a function called `resetGame()` is run.

```js
resetButton.addEventListener("click", resetGame);
```

Now we need to define this function too!

Add the following code, again to the bottom of your JavaScript:

```js
function resetGame() {
  guessCount = 1;

  const resetParas = document.querySelectorAll(".resultParas p");
  for (const resetPara of resetParas) {
    resetPara.textContent = "";
  }

  resetButton.parentNode.removeChild(resetButton);

  guessField.disabled = false;
  guessSubmit.disabled = false;
  guessField.value = "";
  guessField.focus();

  lastResult.style.backgroundColor = "white";

  randomNumber = Math.floor(Math.random() * 100) + 1;
}
```

This rather long block of code completely resets everything to how it was at the start of the game, so the player can have another go. It:

- Puts the guessCount back down to 1.

- Empties all the text out of the information paragraphs. We select all paragraphs inside `<div class="resultParas"></div>`, then loop through each one, setting their textContent to `''` (an empty string).

- Removes the reset button from our code.

- Enables the form elements, and empties and focuses the text field, ready for a new guess to be entered.

- Removes the background color from the lastResult paragraph.

- Generates a new random number so that you are not just guessing the same number again!

At this point, you should have a fully working (simple) game — congratulations!

All we have left to do now in this article is to talk about a few other important code features that you've already seen, although you may have not realized it.

### Loops

One part of the above code that we need to take a more detailed look at is the for...of loop.

Loops are a very important concept in programming, which allow you to keep running a piece of code over and over again, until a certain condition is met.

To start with, go to your browser developer tools JavaScript console again, and enter the following:

```js
const fruits = ["apples", "bananas", "cherries"];
for (const fruit of fruits) {
  console.log(fruit);
}
```

What happened? The strings `'apples', 'bananas', 'cherries'` were printed out in your console.

This is because of the loop.

The line `const fruits = ['apples', 'bananas', 'cherries'];` creates an `array`. We will work through a complete Arrays tutorial later in this module, but for now: _an array is a collection of items (in this case strings)._

A `for...of` loop gives you a way to get each item in the array and run some JavaScript on it. The line `for (const fruit of fruits)` says:

1. Get the first item in `fruits`.
2. Set the `fruit` variable to that item, then run the code between the `{}` curly braces.
3. Get the next item in `fruits`, and repeat 2, until you reach the end of `fruits`.

In this case, the code inside the curly braces is writing out fruit to the console.

Now let's look at the loop in our number guessing game — the following can be found inside the `resetGame()` function:

```js
const resetParas = document.querySelectorAll(".resultParas p");
for (const resetPara of resetParas) {
  resetPara.textContent = "";
}
```

This code creates a variable containing a list of all the paragraphs inside `<div class="resultParas">` using the `querySelectorAll()` method, then it loops through each one, removing the text content of each.

### Objects (quick version)

Let's add one more final improvement.

Add the following line just below the `let resetButton;` line near the top of your JavaScript, then save your file:

```js
guessField.focus();
```

This line uses the `focus()` method to automatically put the text cursor into the `<input>` text field as soon as the page loads, meaning that the user can start typing their first guess right away, without having to click the form field first.

It's only a small addition, but it improves usability — giving the user a good visual clue as to what they've got to do to play the game.

In JavaScript, most of the items you will manipulate in your code are `objects`. An `object` is a collection of related functionality stored in a single grouping.

In this particular case, we first created a `guessField` `constant` that stores a reference to the text input form field in our HTML — the following line can be found amongst our declarations near the top of the code:

```js
const guessField = document.querySelector(".guessField");
```

To get this reference, we used the `querySelector()` method of the document object.

Because `guessField` now contains a reference to an `<input>` element, it now has access to a number of properties.

One method available to input elements is `focus()`, so we can now use this line to focus the text input:

```js
guessField.focus();
```

Variables that don't contain references to form elements won't have `focus()` available to them.

For example, the guesses constant contains a reference to a `<p>` element, and the guessCount variable contains a `number`.

_This walkthrough is from [mdn web docs](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/A_first_splash)._
