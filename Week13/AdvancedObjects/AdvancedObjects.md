# Advanced Objects

### Object Building

Let's get started with the following code:

HTML

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Bouncing balls</title>
    <link rel="stylesheet" href="style.css" />
  </head>

  <body>
    <h1>bouncing balls</h1>
    <canvas></canvas>

    <script src="main.js"></script>
  </body>
</html>
```

CSS

```css
html,
body {
  margin: 0;
}

html {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  height: 100%;
}

body {
  overflow: hidden;
  height: inherit;
}

h1 {
  font-size: 2rem;
  letter-spacing: -1px;
  position: absolute;
  margin: 0;
  top: -4px;
  right: 5px;

  color: transparent;
  text-shadow: 0 0 4px white;
}
```

JS

```js
// setup canvas

const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");

const width = (canvas.width = window.innerWidth);
const height = (canvas.height = window.innerHeight);

// function to generate random number

function random(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

// function to generate random color

function randomRGB() {
  return `rgb(${random(0, 255)},${random(0, 255)},${random(0, 255)})`;
}
```

This script gets a reference to the `<canvas>` element, then calls the `getContext()` method on it to give us a context on which we can start to draw.

```js
const width = (canvas.width = window.innerWidth);
const height = (canvas.height = window.innerHeight);
```

These are equal to the width and height of the browser viewport (the area which the webpage appears on — this can be gotten from the Window.innerWidth and Window.innerHeight properties).

We have two helper functions:

```js
function random(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function randomRGB() {
  return `rgb(${random(0, 255)} ${random(0, 255)} ${random(0, 255)})`;
}
```

The `random()` function takes two numbers as arguments, and returns a random number in the range between the two. The `randomRGB()` function generates a random color represented as an rgb() string.

We will need a `class` for our balls:

```js
class Ball {
  constructor(x, y, velX, velY, color, size) {
    this.x = x;
    this.y = y;
    this.velX = velX;
    this.velY = velY;
    this.color = color;
    this.size = size;
  }
}
```

### What is a class? What isn't it?

A JavaScript class is not an object. It is a template for JavaScript objects.

### What this Code Does

This code defines a `Ball` class that represents a ball object in a 2D space, likely for an animation or game. The class has properties for:

- Position (x and y coordinates)
- Velocity (velX and velY for movement in each direction)
- Appearance (color and size)

### What JavaScript Classes Are

Classes in JavaScript are templates for creating objects. They were introduced to provide a cleaner, more familiar syntax for object-oriented programming.

A class acts as a blueprint that defines:

- What properties (data) an object will have
- What methods (functions) can operate on that data

Key Parts of a Class

1. `class` Keyword
   `class Ball { ... }` declares a new class named "Ball".
2. Constructor Method
   ```js
   constructor(x, y, velX, velY, color, size) {
   // code here
   }
   ```
   The constructor is a special method that:

- Runs automatically when you create a new instance of the class using new Ball()
- Takes parameters that can be used to initialize the object
- Uses the this keyword to reference the new object being created

3. `this` Keyword
   `this.x = x` assigns the parameter value to a property of the object. `this` refers to the specific instance of the object being created.

So to reiterate this class only contains a constructor, in which we can initialize the properties each ball needs in order to function in our program:

- x and y coordinates — the horizontal and vertical coordinates where the ball starts on the screen. This can range between 0 (top left hand corner) to the width and height of the browser viewport (bottom right-hand corner).
- horizontal and vertical velocity (velX and velY) — each ball is given a horizontal and vertical velocity; in real terms these values are regularly added to the x/y coordinate values when we animate the balls, to move them by this much on each frame.
- color — each ball gets a color.
- size — each ball gets a size — this is its radius, in pixels.

This handles the properties, but what about the methods? We want to get our balls to actually do something in our program.

Next we have to draw() the ball.

```js
class Ball {
  // …
  draw() {
    ctx.beginPath();
    ctx.fillStyle = this.color;
    ctx.arc(this.x, this.y, this.size, 0, 2 * Math.PI);
    ctx.fill();
  }
}
```

- First, we use beginPath() to state that we want to draw a shape on the paper.

- Next, we use fillStyle to define what color we want the shape to be — we set it to our ball's color property.

- Next, we use the arc() method to trace an arc shape on the paper. Its parameters are:

      - The x and y position of the arc's center — we are specifying the ball's x and y properties.
      - The radius of the arc — in this case, the ball's size property.
      - The last two parameters specify the start and end number of degrees around the circle that the arc is drawn between. Here we specify 0 degrees, and 2 * PI, which is the equivalent of 360 degrees in radians (annoyingly, you have to specify this in radians). That gives us a complete circle. If you had specified only 1 * PI, you'd get a semi-circle (180 degrees).

  - Last of all, we use the fill() method, which basically states "finish drawing the path we started with beginPath(), and fill the area it takes up with the color we specified earlier in fillStyle."

Type in the following to create a new ball instance:

```js
const testBall = new Ball(50, 100, 4, 4, "blue", 10);
```

Try calling its members:

```js
testBall.x;
testBall.size;
testBall.color;
testBall.draw();
```

When you enter the last line, you should see the ball draw itself somewhere on the canvas.

Now if we want to move the ball we need to update it's data.

```js
class Ball {
  // …
  update() {
    if (this.x + this.size >= width) {
      this.velX = -this.velX;
    }

    if (this.x - this.size <= 0) {
      this.velX = -this.velX;
    }

    if (this.y + this.size >= height) {
      this.velY = -this.velY;
    }

    if (this.y - this.size <= 0) {
      this.velY = -this.velY;
    }

    this.x += this.velX;
    this.y += this.velY;
  }
}
```

In the four cases, we are checking to see:

- if the x coordinate is greater than the width of the canvas (the ball is going off the right edge).
- if the x coordinate is smaller than 0 (the ball is going off the left edge).
- if the y coordinate is greater than the height of the canvas (the ball is going off the bottom edge).
- if the y coordinate is smaller than 0 (the ball is going off the top edge).

### Animation time

We need to create somewhere to store the balls.

```js
const balls = [];

while (balls.length < 25) {
  const size = random(10, 20);
  const ball = new Ball(
    // ball position always drawn at least one ball width
    // away from the edge of the canvas, to avoid drawing errors
    random(0 + size, width - size),
    random(0 + size, height - size),
    random(-7, 7),
    random(-7, 7),
    randomRGB(),
    size
  );

  balls.push(ball);
}
```

Next, add the following to the bottom of your code:

```js
function loop() {
  ctx.fillStyle = "rgb(0 0 0 / 25%)";
  ctx.fillRect(0, 0, width, height);

  for (const ball of balls) {
    ball.draw();
    ball.update();
  }

  requestAnimationFrame(loop);
}
```

`requestAnimationFrame()` method — when this method is repeatedly run and passed the same function name, it runs that function a set number of times per second to create a smooth animation.

This is generally done recursively — which means that the function is calling itself every time it runs, so it runs over and over again.

Finally let's run the function:

```js
loop();
```

In class exercise:

Add an extra feature to the bouncing balls.

- Stop all bouncing when user clicks the canvas
- Add background music
- Change colors on click

If you finish adding another feature feel free to do the mdn web docs challenge for the bouncing balls.

[Challenge: Adding features to our bouncing balls demo](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Advanced_JavaScript_objects/Adding_bouncing_balls_features)
