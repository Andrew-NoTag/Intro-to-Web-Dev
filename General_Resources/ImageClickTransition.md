Example on how to make an image transition on click!

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .image-container {
        cursor: pointer;
        width: 300px;
        height: 300px;
        position: relative;
      }

      img {
        width: 100%;
        height: 100%;
        position: absolute;
        transition: transform 0.8s ease, opacity 0.4s ease;
      }

      .hidden {
        opacity: 0;
      }

      .spin {
        transform: rotate(360deg);
      }
    </style>
  </head>
  <body>
    <div class="image-container" onclick="toggleImages()">
      <img src="./JavaScript_Intro/img/pizza.jpg" id="image1" />
      <img
        src="./JavaScript_Intro/img/skating.jpg"
        id="image2"
        class="hidden"
      />
    </div>

    <script>
      function toggleImages() {
        const img1 = document.getElementById("image1");
        const img2 = document.getElementById("image2");

        if (img1.classList.contains("hidden")) {
          img1.classList.remove("hidden");
          img1.classList.add("spin");
          img2.classList.add("hidden");
          img2.classList.remove("spin");
        } else {
          img2.classList.remove("hidden");
          img2.classList.add("spin");
          img1.classList.add("hidden");
          img1.classList.remove("spin");
        }
      }
    </script>
  </body>
</html>
```
