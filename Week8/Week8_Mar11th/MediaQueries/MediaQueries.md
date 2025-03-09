# CSS Media Queries

The `@media` rule makes it possible to define different style rules for different media types.

Media queries in CSS3 extended the CSS2 `@media` types idea: Instead of looking for a type of device, they look at the capability of the device.

Media queries can be used to check many things, such as:

- width and height of the viewport
- orientation of the viewport (landscape or portrait)
- resolution

### CSS Media Types

| Value  | Description                                            |
| ------ | ------------------------------------------------------ |
| all    | Used for all media type devices                        |
| print  | Used for print preview mode                            |
| screen | Used for computer screens, tablets, smart-phones, etc. |

### CSS Common Media Features

Here are some commonly used media features:

| Value       | Description                                        |
| ----------- | -------------------------------------------------- |
| orientation | Orientation of the viewport. Landscape or portrait |
| max-height  | Maximum height of the viewport                     |
| min-height  | Minimum height of the viewport                     |
| height      | Height of the viewport (including scrollbar)       |
| max-width   | Maximum width of the viewport                      |
| min-width   | Minimum width of the viewport                      |
| width       | Width of the viewport (including scrollbar)        |

### Media Query Syntax

A media query consists of a media type and can contain one or more media features, which resolve to either true or false.

```cs
@media not|only mediatype and (media feature) and (media feature) {
  CSS-Code;
}
```

The mediatype is optional (if omitted, it will be set to all). However, if you use not or only, you must also specify a mediatype.

#### Meaning of the not, only, and and keywords:

not: This keyword inverts the meaning of an entire media query.

only: This keyword prevents older browsers that do not support media queries from applying the specified styles. It has no effect on modern browsers.

and: This keyword combines a media type and one or more media features.

You can also link to different stylesheets for different media and different widths of the browser window (viewport):

```html
<link rel="stylesheet" media="print" href="print.css" />
<link rel="stylesheet" media="screen" href="screen.css" />
<link
  rel="stylesheet"
  media="screen and (min-width: 480px)"
  href="example1.css"
/>
<link
  rel="stylesheet"
  media="screen and (min-width: 701px) and (max-width: 900px)"
  href="example2.css"
/>
etc....
```
