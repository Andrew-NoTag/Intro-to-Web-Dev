### Here's how to add a downloaded font to your CSS/HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* Method 1: Using @font-face for fonts you've downloaded */
      @font-face {
        font-family: "MyCustomFont";
        src: url("path/to/font/file.woff2") format("woff2"), url("path/to/font/file.woff")
            format("woff"), url("path/to/font/file.ttf") format("truetype");
        font-weight: normal;
        font-style: normal;
      }

      /* Using the custom font */
      body {
        font-family: "MyCustomFont", sans-serif;
      }

      h1 {
        font-family: "MyCustomFont", sans-serif;
        font-weight: bold;
      }
    </style>
  </head>
  <body>
    <h1>This text uses my custom font</h1>
    <p>This paragraph also uses the custom font.</p>
  </body>
</html>
```

Here's the step-by-step process:

1. Download the font files - Common formats include .ttf, .woff, and .woff2 (woff2 is most modern and efficient)
2. Create a folder for your fonts - Typically in your project directory, create a folder like "fonts" or "assets/fonts"
3. Add the @font-face rule - This tells the browser where to find your font files and what to call them
4. Use the font in your CSS - Reference the font by the name you gave it in the `font-family` property
5. Always include fallback fonts - Add generic font families like sans-serif or serif at the end of your font-family list

For a more complete example with multiple font weights:
css

```css
@font-face {
  font-family: "MyCustomFont";
  src: url("fonts/mycustomfont-regular.woff2") format("woff2"), url("fonts/mycustomfont-regular.woff")
      format("woff");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "MyCustomFont";
  src: url("fonts/mycustomfont-bold.woff2") format("woff2"), url("fonts/mycustomfont-bold.woff")
      format("woff");
  font-weight: bold;
  font-style: normal;
}

@font-face {
  font-family: "MyCustomFont";
  src: url("fonts/mycustomfont-italic.woff2") format("woff2"), url("fonts/mycustomfont-italic.woff")
      format("woff");
  font-weight: normal;
  font-style: italic;
}
```
