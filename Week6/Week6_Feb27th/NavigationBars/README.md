# CSS Navigation Bar

Having easy-to-use navigation is important for any web site.

With CSS you can transform boring HTML menus into good-looking navigation bars.

When we learned about linking we created a list of links that normally live on the navigation bar.

```html
<ul>
  <li><a href="index.html">Home</a></li>
  <li><a href="contact.html">Contact</a></li>
  <li><a href="about.html">About</a></li>
</ul>
```

To remove the bullets we can alter the list CSS

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

`list-style-type: none;` -
Removes the bullets. A navigation bar does not need list markers

`Set margin: 0;` and `padding: 0;` to remove browser default settings

## Horizontal Navigation Bar

There are two ways to create a horizontal navigation bar. Using inline or floating list items.

### Inline List Items

One way to build a horizontal navigation bar is to specify the `<li>` elements as inline

```css
li {
  display: inline;
}
```

`display: inline;` - By default, `<li>` elements are block elements. Here, we remove the line breaks before and after each list item, to display them on one line

### Floating List Items

Another way of creating a horizontal navigation bar is to float the `<li>` elements, and specify a layout for the navigation links

```css
li {
  float: left;
}

a {
  display: block;
  padding: 8px;
  background-color: #dddddd;
}
```

`float: left;` - Use float to get block elements to float next to each other

`display: block;` - Allows us to specify padding (and height, width, margins, etc. if you want)

`padding: 8px;` - Specify some padding between each `<a>` element, to make them look good

`background-color:red;` - Add a gray background-color to each `<a>` element

> **Tip:** Add the background-color to `<ul>` instead of each `<a>` element if you want a full-width background color:

### In Class Examples

Create a basic horizontal navigation bar with a dark background color and change the background color of the links when the user moves the mouse over them:

<!-- ```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}
``` -->

#### Hover

```css
/* Change the link color to black on hover */
li a:hover {
  background-color: black;
}
```

#### Active/Current Navigation Link

Add an "active" class to the current link to let the user know which page they are on

```css
.active {
  background-color: #04aa6d;
}
```

> You must add the `class="active"` to the page on the HTML file.

#### Border Dividers

Add the `border-right` property to `<li>` to create link dividers:

```css
/* Add a gray right border to all list items, except the last item (last-child) */
li {
  border-right: 1px solid gray;
}

li:last-child {
  border-right: none;
}
```

#### Fixed Navigation Bar

Make the navigation bar stay at the top or the bottom of the page, even when the user scrolls the page:

```css
ul {
  position: fixed;
  top: 0;
  width: 100%;
}
```

To learn more of what you can do with navigation bars look over the [W3 Schools page](https://www.w3schools.com/css/css_navbar_horizontal.asp).

---

Reference
[W3Schools CSS Navigation Bar Page](https://www.w3schools.com/css/css_navbar.asp)
