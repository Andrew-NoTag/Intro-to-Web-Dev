# CSS Introduction

## What is CSS?

- CSS stands for Cascading Style Sheets
- CSS describes how HTML elements are to be displayed on screen, paper, or in other media
- CSS saves a lot of work. It can control the layout of multiple web pages all at once
- External stylesheets are stored in CSS files

#### CSS Example

```html
<style>
  body {
    background-color: lightblue;
  }

  h1 {
    color: white;
    text-align: center;
  }

  p {
    font-family: verdana;
    font-size: 20px;
  }
</style>
```

## CSS Syntax

A CSS rule consists of a selector and a declaration block.

![Linking Web Pages within Same Parent Directory](https://www.w3schools.com/css/img_selector.gif)

The selector points to the HTML element you want to style.

The declaration block contains one or more declarations separated by semicolons.

Each declaration includes a CSS property name and a value, separated by a colon.

Multiple CSS declarations are separated with semicolons, and declaration blocks are surrounded by curly braces.

#### Example

```html
<style>
  p {
    color: red;
    text-align: center;
  }
</style>
```

#### Example Explained

`p` is a selector in CSS (it points to the HTML element you want to style: `<p>`).

`color` is a property, and red is the property value

`text-align` is a property, and center is the property value

## Basic CSS Selectors

### The CSS element Selector

The element selector selects HTML elements based on the element name.

#### Example

Here, all `<p>` elements on the page will be center-aligned, with a red text color:

```html
<html>
  <head>
    <style>
      p {
        text-align: center;
        color: red;
      }
    </style>
  </head>
  <body>
    <p>Every paragraph will be affected by the style.</p>
    <p id="para1">Me too!</p>
    <p>And me!</p>
  </body>
</html>
```

### The CSS id Selector

The id selector uses the id attribute of an HTML element to select a specific element.

The id of an element is unique within a page, so the id selector is used to select one unique element!

To select an element with a specific id, write a hash (#) character, followed by the id of the element.

#### Example

The CSS rule below will be applied to the HTML element with id="para1":

```html
<html>
  <head>
    <style>
      #para1 {
        text-align: center;
        color: red;
      }
    </style>
  </head>
  <body>
    <p id="para1">Hello World!</p>
    <p>This paragraph is not affected by the style.</p>
  </body>
</html>
```

### The CSS class Selector

The class selector selects HTML elements with a specific class attribute.

To select elements with a specific class, write a period (.) character, followed by the class name.

#### Example

In this example all HTML elements with class="center" will be red and center-aligned:

```html
<html>
  <head>
    <style>
      .center {
        text-align: center;
        color: red;
      }
    </style>
  </head>
  <body>
    <h1 class="center">Red and center-aligned heading</h1>
    <p class="center">Red and center-aligned paragraph.</p>
  </body>
</html>
```

You can also specify that only specific HTML elements should be affected by a class.

#### Example

```html
<html>
  <head>
    <style>
      p.center {
        text-align: center;
        color: red;
      }
    </style>
  </head>
  <body>
    <h1 class="center">This heading will not be affected</h1>
    <p class="center">This paragraph will be red and center-aligned.</p>
  </body>
</html>
```

HTML elements can also refer to more than one class.

#### Example

```html
<html>
  <head>
    <style>
      p.center {
        text-align: center;
        color: red;
      }

      p.large {
        font-size: 300%;
      }
    </style>
  </head>
  <body>
    <h1 class="center">This heading will not be affected</h1>
    <p class="center">This paragraph will be red and center-aligned.</p>
    <p class="center large">
      This paragraph will be red, center-aligned, and in a large font-size.
    </p>
  </body>
</html>
```

### The CSS Universal Selector

The universal selector (\*) selects all HTML elements on the page.

Example
The CSS rule below will affect every HTML element on the page:

```html
<style>
  * {
    text-align: center;
    color: blue;
  }
</style>
```

### The CSS Grouping Selector

The grouping selector selects all the HTML elements with the same style definitions.

Look at the following CSS code (the h1, h2, and p elements have the same style definitions):

```html
<style>
  h1 {
    text-align: center;
    color: red;
  }

  h2 {
    text-align: center;
    color: red;
  }

  p {
    text-align: center;
    color: red;
  }
</style>
```

It will be better to group the selectors, to minimize the code.

To group selectors, separate each selector with a comma.

#### Example

In this example we have grouped the selectors from the code above:

```html
<style>
  h1,
  h2,
  p {
    text-align: center;
    color: red;
  }
</style>
```

## How To Add CSS

When a browser reads a style sheet, it will format the HTML document according to the information in the style sheet.

### Three Ways to Insert CSS

There are three ways of inserting a style sheet:

1. External CSS
2. Internal CSS
3. Inline CSS

### External CSS

With an external style sheet, you can change the look of an entire website by changing just one file!

Each HTML page must include a reference to the external style sheet file inside the <link> element, inside the head section.

```html
<html>
  <head>
    <link rel="stylesheet" href="mystyle.css" />
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

An external style sheet can be written in any text editor, and must be saved with a .css extension.

The external .css file should not contain any HTML tags.

Here is how the "mystyle.css" file looks:

```html
body { background-color: lightblue; } h1 { color: navy; margin-left: 20px; }
```

**Note:** Do not add a space between the property value (20) and the unit (px):

- _Incorrect (space): margin-left: 20 px;_
- **Correct (no space):** margin-left: 20px;

### Internal CSS

An internal style sheet may be used if one single HTML page has a unique style.

The internal style is defined inside the `<style>` element, inside the head section.

Example
Internal styles are defined within the `<style>` element, inside the <head> section of an HTML page:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-color: linen;
      }

      h1 {
        color: maroon;
        margin-left: 40px;
      }
    </style>
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

### Inline CSS

An inline style may be used to apply a unique style for a single element.

To use inline styles, add the style attribute to the relevant element. The style attribute can contain any CSS property.

#### Example

Inline styles are defined within the "style" attribute of the relevant element:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1 style="color:blue;text-align:center;">This is a heading</h1>
    <p style="color:red;">This is a paragraph.</p>
  </body>
</html>
```

**Tip:** An inline style loses many of the advantages of a style sheet (by mixing content with presentation). Use this method sparingly.

### Multiple Style Sheets

If some properties have been defined for the same selector (element) in different style sheets, the value from the last read style sheet will be used.

Assume that an external style sheet has the following style for the `<h1>` element:

```html
h1 { color: navy; }
```

Then, assume that an internal style sheet also has the following style for the `<h1>` element:

```html
h1 { color: orange; }
```

#### Example

If the internal style is defined after the link to the external style sheet, the `<h1>` elements will be "orange":

```html
<head>
  <link rel="stylesheet" type="text/css" href="mystyle.css" />
  <style>
    h1 {
      color: orange;
    }
  </style>
</head>
```

### Example

However, if the internal style is defined before the link to the external style sheet, the `<h1>` elements will be "navy":

```html
<head>
  <style>
    h1 {
      color: orange;
    }
  </style>
  <link rel="stylesheet" type="text/css" href="mystyle.css" />
</head>
```

### Cascading Order

_What style will be used when there is more than one style specified for an HTML element?_

All the styles in a page will "cascade" into a new "virtual" style sheet by the following rules, where number one has the highest priority:

1. Inline style (inside an HTML element)
2. External and internal style sheets (in the head section)
3. Browser default

So, an inline style has the highest priority, and will override external and internal styles and browser defaults.

## HTML and CSS Comments

Comments are used to explain the code, and may help when you edit the source code at a later date.

You can add comments to your HTML source by using the `<!--...-->` syntax.

```html
<!-- This is an html comment -->
```

A CSS comment starts with `/*` and ends with `*/`.

```html
/* This is a css comment */
```

In the following example, we use a combination of HTML and CSS comments:

Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        color: red; /* Set text color to red */
      }
    </style>
  </head>
  <body>
    <h2>My Heading</h2>

    <!-- These paragraphs will be red -->
    <p>Hello World!</p>
    <p>This paragraph is styled with CSS.</p>
    <p>HTML and CSS comments are not shown in the output.</p>
  </body>
</html>
```

#### References

- [MDN Getting Started with CSS](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Getting_started)
- [W3 School CSS Tutorial](https://www.w3schools.com/css/default.asp)
- [Professor Kathryn Adee's Intro to Web Dev Repository](https://github.com/Kadee80/webdev_sp25)
