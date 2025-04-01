# JavaScript Variables

Variables are Containers for Storing Data

JavaScript Variables can be declared in 4 ways:

- Automatically
- Using var
- Using let
- Using const

> It is considered good programming practice to always declare variables before use.

```js
// Example using var
var x = 5;
var y = 6;
var z = x + y;

// Example using let
let x = 5;
let y = 6;
let z = x + y;

// Example using const
const x = 5;
const y = 6;
const z = x + y;

// Mixed Example
const price1 = 5;
const price2 = 6;
let total = price1 + price2;
```

### When to Use `var`, `let`, or `const`?

1. Always declare variables

2. Always use `const` if the value should not be changed

3. Always use `const` if the type should not be changed (Arrays and Objects)

4. Only use `let` if you can't use `const`

5. Only use `var` if you MUST support old browsers.

Just like in algebra, variables hold values and are used in expressions.

## JavaScript Identifiers

All JavaScript variables must be identified with unique names aka `identifiers`.

Identifiers can be short names (like `x` and `y`) or more descriptive names (age, sum, totalVolume).

The general rules for constructing names for variables (unique identifiers) are:

- Names can contain letters, digits, underscores, and dollar signs.
- Names must begin with a letter.
- Names are case sensitive (y and Y are different variables).
- Reserved words (like JavaScript keywords) cannot be used as names.

### The Assignment Operator

In JavaScript, the equal sign (`=`) is an "assignment" operator, not an **"equal to"** operator.

> The "equal to" operator is written like `==` in JavaScript.

### JavaScript Data Types

Strings (text values) are written inside double or single quotes (`"I'm text"`). Numbers are written without quotes.

## Declaring a JavaScript Variable

Creating a variable in JavaScript is called "declaring" a variable.

You declare a JavaScript variable with the `var` or the `let` keyword:

```js
var carName;
// or:
let carName;

// we are both considered "undefined" since we have no value!

// To assign a value to the variable, use the equal sign:

let carName = "Volvo";

// You can also declare multiples in one line
let cat, dog, horse;
```

Lets create a variable called carName and assign the value "Volvo" to it:

```html
<p>Create a variable, assign a value to it, and display it:</p>

<p id="demo"></p>

<script>
  let carName = "Volvo";
  document.getElementById("demo").innerHTML = carName;
</script>
```

### JavaScript Arithmetic

You can do math inside of JavaScript using operators like `=` and `+`:

```js
let x = 5 + 2 + 3;
```

You can also add strings

```js
let x = "John" + " " + "Doe";
```

What do we think will happen if we did this?

```js
let x = "5" + 2 + 3;
```

## JavaScript `let`

- Variables declared with let have Block Scope

- Variables declared with let must be Declared before use

- Variables declared with let cannot be Redeclared in the same scope

```js
// Variables declared inside a { } block cannot be accessed from outside the block:
{
  let x = 2;
}
// x can NOT be used over here

// Variables declared with var inside a { } block can be accessed from outside the block:

{
  var x = 2;
}
// x CAN be used here

// Redeclaring a variable inside a block will not redeclare the variable outside the block:

let x = 10;
// Here x is ?

{
  let x = 2;
  // Here x is ?
}

// Here x is ?
```

## JavaScript `const`

- Variables defined with `const` cannot be Redeclared

- Variables defined with `const` cannot be Reassigned

- Variables defined with `const` have Block Scope

```js
// JavaScript const variables must be assigned a value when they are declared:
const PI = 3.14159265359;

// NOT
const PI;
PI = 3.14159265359;
```

> Always declare a variable with const when you know that the value should not be changed.

### Boolean

The Boolean data type can hold two values: `true` and `false` . There is nothing in between.

This Boolean is used a lot in code, especially expressions that evaluate to a Boolean:

```js
let bool1 = false;
let bool2 = true;
```

In the preceding example, you can see the options we have for the Boolean data type. It is used for situations in which you want to store a true or a false value (which can indicate on/off or yes/no). For example, whether an element is deleted:

```js
let let objectIsDeleted = false;
```

Or, whether the light is on or off:

```js
let lightIsOn = true;
```

These variables suggest respectively that the specified object is not deleted, and that the specific light is on.

### Practice exercise:

Create a variable for your name, another one for your age, and another one for whether you can code JavaScript or not. Log to the console the following sentence, where name , age and true / false are variables:

`Hello, my name is Sam, I am 28 years old and I can code JavaScript: true.`

<!-- ```js
const myName = "Sam";
const myAge = 28;
const coder = true;
const message =
  "Hello, my name is " +
  myName +
  ", I years old and I can code JavaScript: " +
  coder +
  ".";
console.log(message);
``` -->
