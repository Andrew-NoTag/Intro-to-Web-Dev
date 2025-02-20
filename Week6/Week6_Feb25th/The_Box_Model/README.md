# The Box Model

_Developed using [MDN Web Docs Tutorial](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model)_.

Everything in CSS has a box around it, and understanding these boxes is key to being able to create more complex layouts with CSS, or to align items with other items.

## Block and inline boxes

In CSS we have several types of boxes that generally fit into the categories of:

- Block boxes
- Inline boxes.

The type refers to how the box behaves in terms of page flow and in relation to other boxes on the page. Boxes have an inner display type and an outer display type.

In general, you can set various values for the display type using the display property, which can have various values.

If a box has a display value of block, then:

- The box will break onto a new line.
- The width and height properties are respected.
- Padding, margin and border will cause other elements to be pushed away from the box.
- If width is not specified, the box will extend in the inline direction to fill the space available in its container.
- In most cases, the box will become as wide as its container, filling up 100% of the space available.

Some HTML elements, such as `<h1>` and `<p>`, use block as their outer display type by default.

```css
.block {
  display: block;
}
```

If a box has a display type of inline, then:

- The box will not break onto a new line.
- The width and height properties will not apply.
- Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
- Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

Some HTML elements, such as `<a>`, `<span>`, `<em>` and `<strong>` use inline as their outer display type by default.

```css
.inline {
  display: inline;
}
```

Block and inline layout is the default way things behave on the web. By default and without any other instruction, the elements inside a box are also laid out in normal flow and behave as block or inline boxes.

## What is the CSS box model?

The CSS box model as a whole applies to block boxes and defines how the different parts of a box — margin, border, padding, and content — work together to create a box that you can see on a page.

There is a standard and an alternate box model. By default, browsers use the standard box model.

Parts of a box
Making up a block box in CSS we have the:

- Content box: The area where your content is displayed; size it using properties like `width` and `height`.
- Padding box: The padding sits around the content as white space; size it using `padding` and related properties.
- Border box: The border box wraps the content and any padding; size it using `border` and related properties.
- Margin box: The margin is the outermost layer, wrapping the content, padding, and border as whitespace between this box and other elements; size it using `margin` and related properties.

![Alt text](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model/box-model.png)

### The standard CSS box model

In the standard box model, if you set width and height property values on a box, these values define the width and height of the content box. Any padding and borders are then added to those dimensions to get the total size taken up by the box (see the image below).

If we assume that a box has the following CSS:

```css
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

The actual space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

![Alt text](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model/standard-box-model.png)

The alternative CSS box model
In the alternative box model, any width is the width of the visible box on the page. The content area width is that width minus the width for the padding and border (see image below). No need to add up the border and padding to get the real size of the box.

To turn on the alternative model for an element, set box-sizing: border-box on it:

```css
.box {
  box-sizing: border-box;
}
```

Now, the actual space taken up by the box will be 350px in the inline direction and 150px in the block direction.

![Alt text](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model/alternate-box-model.png)

To use the alternative box model for all of your elements (which is a common choice among developers), set the box-sizing property on the `<html>` element and set all other elements to inherit that value:

```css
html {
  box-sizing: border-box;
}
```

## Use browser DevTools to view the box model

Your browser developer tools can make understanding the box model far easier — they can show you the size of the element plus its margin, padding, and border.

Inspecting an element in this way is a great way to find out if your box is really the size you think it is!

![Alt](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model/box-model-devtools.png)

## Margins, padding, and borders

You've already seen the margin, padding, and border properties at work in the example above.

To explore them in more detail please go through the [Margins, padding, and borders](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model#the_alternative_css_box_model:~:text=think%20it%20is!-,Margins%2C%20padding%2C%20and%20borders,-You%27ve%20already%20seen) portion of the MDN walkthrough.

## Using display: inline-block

`display: inline-block` is a special value of `display`, which provides a middle ground between `inline` and `block`. Use it if you do not want an item to break onto a new line, but do want it to respect `width` and `height` and avoid the overlapping seen above.

An element with `display: inline-block` does a subset of the block things we already know about:

- The `width` and `height` properties are respected.
- `padding`, `margin`, and `border` will cause other elements to be pushed away from the box.

It does not, however, break onto a new line, and will only become larger than its content if you explicitly add `width` and `height` properties.

Where this can be useful is when you want to give a link a larger hit area by adding `padding`. `<a>` is an inline element like `<span>`; you can use `display: inline-block` to allow padding to be set on it, making it easier for a user to click the link.

You see this fairly frequently in navigation bars. The navigation displayed is in a row using flexbox and we have added padding to the `<a>` element as we want to be able to change the `background-color` when the `<a>` is hovered. The padding appears to overlap the border on the `<ul>` element. This is because the `<a>` is an inline element.

Adding `display: inline-block;` to the rule with the `.links-list` a selector, and we will see how it fixes this issue by causing the padding to be respected by other elements!
