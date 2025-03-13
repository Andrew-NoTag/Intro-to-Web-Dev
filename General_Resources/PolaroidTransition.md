```css
body {
  background-color: bisque;
}
.guideline {
  display: flex;
  justify-content: center;
  align-items: center;
  width: fit-content;
  text-align: center;
  margin: 0 auto;
}

.guideline:hover {
  transform: scale(0.8);
  transition: 2s;
}

.guide1 {
  background-color: tomato;
}
```

```html
<html>
  <head>
    <link rel="stylesheet" href="midterm.css" />
  </head>
  <body>
    <h1 align="center">Hesitate again?</h1>
    <h2 align="center">No worries! Let me help you!</h2>
    <div class="guideline">
      <div class="guide1">
        <img src="/midterm/about/do.jpg" />
        <p><a href="/midterm/about/do.html">What to DO next?</a></p>
      </div>
    </div>
  </body>
</html>
```
