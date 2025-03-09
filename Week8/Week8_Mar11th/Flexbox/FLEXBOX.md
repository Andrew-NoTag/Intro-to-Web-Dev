# What is CSS Flexbox?

Flexbox is short for the Flexible Box Layout module.

Flexbox is a layout method for arranging items in rows or columns.

Flexbox makes it easier to design a flexible responsive layout structure, without using float or positioning.

## CSS Flexbox Components

A flexbox always consists of:

- a Flex Container - the parent (container) `<div>` element

- Flex Items - the items inside the container `<div>`

### A Flex Container with Three Flex Items

To start using CSS Flexbox, you need to first define a flex container.

The flex container becomes flexible by setting the display property to flex.

```html
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

```css
.flex-container {
  display: flex;
}
```

### The CSS Flex Container

The CSS properties we use for the flex container are:

- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

### The CSS flex-direction Property

The `flex-direction` property specifies the display-direction of flex items in the flex container.

The `flex-direction` property can have one of the following values:

- `row`
- `column`
- `row-reverse`
- `column-reverse`

### Example

The row value is the default value, and it displays the flex items horizontally (from left to right):

```css
.flex-container {
  display: flex;
  flex-direction: row;
}
```

The `column` value displays the flex items vertically (from top to bottom).

The `row-reverse` value displays the flex items horizontally (but from right to left).

The `column-reverse` value displays the flex items vertically (but from bottom to top).

## The CSS flex-wrap Property

The `flex-wrap` property specifies whether the flex items should wrap or not, if there is not enough room for them on one flex line.

The `flex-wrap` property can have one of the following values:

- `nowrap`
- `wrap`
- `wrap-reverse`

### Example

The `nowrap` value specifies that the flex items will not wrap (this is default):

```css
.flex-container {
  display: flex;
  flex-wrap: nowrap;
}
```

The `wrap` value specifies that the flex items will wrap if necessary.

The `wrap-reverse` value specifies that the flex items will wrap if necessary, in reverse order:

### The CSS flex-flow Property

The `flex-flow` property is a shorthand property for setting both the `flex-direction` and `flex-wrap` properties.

```css
.flex-container {
  display: flex;
  flex-flow: row wrap;
}
```

### The CSS justify-content Property

The `justify-content` property is used to align the flex items when they do not use all available space on the main-axis (horizontally).

The `justify-content` property can have one of the following values:

- `center`
- `flex-start`
- `flex-end`
- `space-around`
- `space-between`
- `space-evenly`

### The CSS align-items Property

The `align-items` property is used to align the flex items when they do not use all available space on the cross-axis (vertically).

The `align-items` property can have one of the following values:

- `center`
- `flex-start`
- `flex-end`
- `stretch`
- `baseline`
- `normal`

In the following examples we use a 200 pixels high container, to better demonstrate the `align-items` property.

```css
.flex-container {
  display: flex;
  height: 200px;
  align-items: center;
}
```

The `center` value positions the flex items in the middle of the container.

The `flex-start` value positions the flex items at the top of the container.

The `flex-end` value positions the flex items at the bottom of the container.

The `stretch` value stretches the flex items to fill the container (this is equal to "normal" which is default).

The `baseline` value positions the flex items at the baseline of the container:

### The CSS align-content Property

The `align-content` property is used to align the flex lines.

The `align-content` property is similar to align-items, but instead of aligning flex items, it aligns the flex lines.

The `align-content` property can have one of the following values:

- `center`
- `stretch`
- `flex-start`
- `flex-end`
- `space-around`
- `space-between`
- `space-evenly`

In the following examples we use a 600 pixels high container, with the flex-wrap property set to wrap, to better demonstrate the align-content property.

#### Example

With `center`, the flex lines are packed toward the center of the container:

```CSS
.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: center;
}
```

With `stretch`, the flex lines stretch to take up the remaining space of the container (this is default).

With `flex-start`, the flex lines are packed toward the start of the container.

With `flex-end`, the flex lines are packed toward the end of the container.

With `space-between`, the space between the flex lines are equal, but the first item is flush with the start edge of the container, and the last item is flush with the end edge of the container.

With `space-around`, the space between the flex lines are equal, but the space before the first item and after the last item is set to half of the space between the flex lines.

With `space-evenly`, the flex lines are evenly distributed in the flex container, with equal space on top, bottom and between.

### How do we center an element in a flex container?

Set both the `justify-content` and `align-items` properties to center, and the flex item will be perfectly centered

```css
.flex-container {
  display: flex;
  height: 300px;
  justify-content: center;
  align-items: center;
}
```

# CSS Responsive Flexbox

You know now we can use media queries to create different layouts for different screen sizes and devices.

For example, if you want to create a two-column layout for most screen sizes, and a one-column layout for small screen sizes (such as phones and tablets), you can change the `flex-direction` from `row` to `column` at a specific breakpoint

```css
.flex-container {
  display: flex;
  flex-direction: row;
}

/* Responsive layout - makes a one column layout instead of a two-column layout */
@media (max-width: 800px) {
  .flex-container {
    flex-direction: column;
  }
}
```

## In class exercise

In groups of two play the following game: [Flexbox Froggy](https://flexboxfroggy.com/)!

First group to finish get to choose which day they present their midterm!
