# CSS 2D Transforms

CSS transforms allow you to move, rotate, scale, and skew elements.

| Function       | Description                                                               |
| -------------- | ------------------------------------------------------------------------- |
| `matrix()`     | Defines a 2D transformation, using a matrix of six values                 |
| `translate()`  | Defines a 2D translation, moving the element along the X- and the Y-axis  |
| `translateX()` | Defines a 2D translation, moving the element along the X-axis             |
| `translateY()` | Defines a 2D translation, moving the element along the Y-axis             |
| `scale()`      | Defines a 2D scale transformation, scaling the element's width and height |
| `scaleX()`     | Defines a 2D scale transformation, scaling the element's width            |
| `scaleY()`     | Defines a 2D scale transformation, scaling the element's height           |
| `rotate()`     | Defines a 2D rotation, the angle is specified in the parameter            |
| `skew()`       | Defines a 2D skew transformation along the X- and the Y-axis              |
| `skewX()`      | Defines a 2D skew transformation along the X-axis                         |
| `skewY()`      | Defines a 2D skew transformation along the Y-axis                         |

### CSS 2D Transforms Functions

With the CSS transform property you can use the following 2D transformation functions:

translate()
rotate()
scaleX()
scaleY()
scale()
skewX()
skewY()
skew()
matrix()

### translate()

The `translate()` function moves an element from its current position (according to the parameters given for the X-axis and the Y-axis).

The following example moves the `<div>` element 50 pixels to the right, and 100 pixels down from its current position:

```css
div {
  transform: translate(50px, 100px);
}
```

### rotate()

The `rotate()` function rotates an element clockwise or counter-clockwise according to a given degree.

The following example rotates the `<div>` element clockwise with 20 degrees:

```css
div {
  transform: rotate(20deg);
}
```

Using negative values will rotate the element counter-clockwise.

### scale()

The `scale()` function increases or decreases the size of an element (according to the parameters given for the width and height).

The following example increases the `<div>` element to be two times of its original width, and three times of its original height:

```css
div {
  transform: scale(2, 3);
}
```

The `scaleX()` function increases or decreases the width of an element.

The `scaleY()` function increases or decreases the height of an element.

### skew()

The `skew()` function skews an element along the X and Y-axis by the given angles.

```css
div {
  transform: skew(20deg, 10deg);
}
```

### matrix()

The `matrix()` function combines all the 2D transform functions into one.

The `matrix()` function take six parameters, containing mathematic functions, which allows you to rotate, scale, move (translate), and skew elements.

The parameters are as follow: matrix(scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY())

```css
div {
  transform: matrix(1, -0.3, 0, 1, 0, 0);
}
```

> ### Try activating one of these transformations on hover!

```css
.className:hover {
  transform: rotate(45deg);
}
```

# CSS 3D Transforms

CSS also supports 3D transformations.

### CSS 3D Transforms Functions

With the CSS `transform` property you can use the following 3D transformation functions:

| Function    | Description                                            |
| ----------- | ------------------------------------------------------ |
| `rotateX()` | Rotates an element around its X-axis at a given degree |
| `rotateY()` | Rotates an element around its Y-axis at a given degree |
| `rotateZ()` | Rotates an element around its Z-axis at a given degree |

# CSS Transitions

CSS transitions allows you to change property values smoothly, over a given duration.

| Property                     | Description                                                                            |
| ---------------------------- | -------------------------------------------------------------------------------------- |
| `transition`                 | A shorthand property for setting the four transition properties into a single property |
| `transition-delay`           | Specifies a delay (in seconds) for the transition effect                               |
| `transition-duration`        | Specifies how many seconds or milliseconds a transition effect takes to complete       |
| `transition-property`        | Specifies the name of the CSS property the transition effect is for                    |
| `transition-timing-function` | Specifies the speed curve of the transition effect                                     |

## How to Use CSS Transitions?

To create a transition effect, you must specify two things:

- The CSS property you want to add an effect to
- The duration of the effect

Note: If the duration part is not specified, the transition will have no effect, because the default value is 0.

The following example shows a 100px \* 100px red `<div>` element. The `<div>` element has also specified a transition effect for the width property, with a duration of 2 seconds:

```css
div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s;
}
```

The transition effect will start when the specified CSS property (width) changes value.

Now, let us specify a new value for the width property when a user mouses over the `<div>` element:

```css
div:hover {
  width: 300px;
}
```

Notice that when the cursor mouses out of the element, it will gradually change back to its original style.

### Change Several Property Values

The following example adds a transition effect for both the width and height property, with a duration of 2 seconds for the width and 4 seconds for the height:

```css
div {
  transition: width 2s, height 4s;
}
```

Go to [W3Schools Transitions page](https://www.w3schools.com/css/css3_transitions.asp) to look deeper into different transition properties.

> To learn how to use CSS for animatiing look through [W3Schools Animations page](https://www.w3schools.com/css/css3_animations.asp).
