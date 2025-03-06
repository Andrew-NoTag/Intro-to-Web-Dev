# Image Styling

### Sizing images

As you already know from following these lessons, everything in CSS generates a box.

If you place an image inside a box that is smaller or larger than the dimensions of the image file in either direction, it will either appear smaller than the box, or overflow the box. You need to make a decision about what happens with the overflow.

In the example below we have two boxes, both 200 pixels in size:

One contains an image that is smaller than 200 pixels — it is smaller than the box and doesn't stretch to fill it.
The other is larger than 200 pixels and overflows the box.

```html
<div class="wrapper">
  <div class="box">
    <img
      alt="star"
      src="https://mdn.github.io/shared-assets/images/examples/big-star.png"
    />
  </div>
  <div class="box">
    <img
      alt="balloons"
      src="https://mdn.github.io/shared-assets/images/examples/balloons.jpg"
    />
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  align-items: flex-start;
}

.wrapper > * {
  margin: 20px;
}

.box {
  border: 5px solid darkblue;
  width: 200px;
}

img {
}
```

So what can we do about the overflowing issue?

A common technique is to make the `max-width` of an image 100%. This will enable the image to become smaller in size than the box but not larger. This technique will also work with other replaced elements such as `<video>`'s.

Try adding `max-width: 100%` to the `<img>` element rule in the example above. You will see that the smaller image remains unchanged, but the larger one becomes smaller to fit into the box.

You can make other choices about images inside containers. For example, you may want to size an image so it completely covers a box.

The `object-fit` property can help you here. When using `object-fit` the replaced element can be sized to fit a box in a variety of ways.

Below, the first example uses the value cover, which sizes the image down, maintaining the aspect ratio so that it neatly fills the box. As the aspect ratio is maintained, some parts of the image will be cropped by the box. The second example uses contain as a value: this scales the image down until it is small enough to fit inside the box. This results in "letterboxing" as it is not the same aspect ratio as the box.

```html
<div class="wrapper">
  <div class="box">
    <img
      alt="balloons"
      class="cover"
      src="https://mdn.github.io/shared-assets/images/examples/balloons.jpg"
    />
  </div>
  <div class="box">
    <img
      alt="balloons"
      class="contain"
      src="https://mdn.github.io/shared-assets/images/examples/balloons.jpg"
    />
  </div>
</div>
```

```css
.wrapper {
  display: flex;
  align-items: flex-start;
}

.wrapper > * {
  margin: 20px;
}

.box {
  border: 5px solid darkblue;
  width: 200px;
  height: 200px;
}

img {
  height: 100%;
  width: 100%;
}

.cover {
  object-fit: cover;
}

.contain {
  object-fit: contain;
}
```

### Rounded Images

You can use the `border-radius` property to create rounded images.

### Thumbnail Images

Use the `border` property to create thumbnail images.

#### Thumbnail Image as link

```css
img {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 5px;
  width: 150px;
}

img:hover {
  box-shadow: 0 0 2px 1px rgba(0, 140, 186, 0.5);
}
```

```html
<a href="paris.jpg">
  <img src="paris.jpg" alt="Paris" />
</a>
```

### Responsive Images

Responsive images will automatically adjust to fit the size of the screen.

If you want an image to scale down if it has to, but never scale up to be larger than its original size, add the following:

```css
img {
  max-width: 100%;
  height: auto;
}
```

### Transparent Image

The opacity property can take a value from 0.0 - 1.0. The lower value, the more transparent.

```css
img {
  opacity: 0.5;
}
```
