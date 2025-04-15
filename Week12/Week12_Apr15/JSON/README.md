# Working with JSON in JavaScript

### What is JSON?

**JSON** (JavaScript Object Notation) is a lightweight text format for storing and sharing data.

It looks a lot like a JavaScript object, but it's actually just a string.

Used in web development to:

- Send data from server → client
- Save structured data (like user profiles, settings, etc.)

**Example JSON:**

```json
{
  "name": "Jane Doe",
  "age": 30,
  "isStudent": false
}
```

### JSON vs JavaScript Objects

| Feature            | JSON               | JavaScript Object       |
| ------------------ | ------------------ | ----------------------- |
| Quotes             | Double quotes only | Single or double quotes |
| Functions allowed? | ❌ No              | ✅ Yes                  |
| Comments?          | ❌ No              | ✅ Yes                  |
| Valid in JS?       | ✅ Yes (parsed)    | ✅ Yes                  |

---

### Common JSON Operations

### Parse JSON string → JavaScript object

```js
const jsonString = '{"name": "Jane"}';
const obj = JSON.parse(jsonString);
console.log(obj.name); // "Jane"
```

### Convert JavaScript object → JSON string

```js
const obj = { name: "Jane" };
const jsonString = JSON.stringify(obj);
```

### JSON Files & Arrays

JSON can represent:

- **Objects**
- **Arrays**
- **Strings**, **numbers**, **booleans**, and **null**

**Example with an array of objects:**

```json
[
  {
    "name": "Hero One",
    "powers": ["Flying", "Strength"]
  },
  {
    "name": "Hero Two",
    "powers": ["Invisibility", "Speed"]
  }
]
```

Accessing data in JS

```js
heroes[0].powers[1]; // "Strength"
```

## Example: Load JSON and Display it

We’ll use the Fetch API to get data and update a webpage.

1. Fetch and parse JSON:

```js
async function populate() {
  const response = await fetch(
    "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json"
  );
  const superHeroes = await response.json();

  populateHeader(superHeroes);
  populateHeroes(superHeroes);
}
```

2. Update the page with data:

```js
function populateHeader(obj) {
  const header = document.querySelector("header");
  const h1 = document.createElement("h1");
  h1.textContent = obj.squadName;
  header.appendChild(h1);

  const p = document.createElement("p");
  p.textContent = `Hometown: ${obj.homeTown} // Formed: ${obj.formed}`;
  header.appendChild(p);
}
```

3.  Display hero cards:

```js
function populateHeroes(obj) {
  const section = document.querySelector("section");
  obj.members.forEach((hero) => {
    const article = document.createElement("article");

    const h2 = document.createElement("h2");
    h2.textContent = hero.name;

    const p = document.createElement("p");
    p.textContent = `Secret Identity: ${hero.secretIdentity}`;

    article.appendChild(h2);
    article.appendChild(p);

    section.appendChild(article);
  });
}
```

Final HTML code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JSON Example: Superheroes</title>
    <style>
      body {
        font-family: sans-serif;
        padding: 1em;
        background: #f4f4f4;
      }

      header {
        background-color: #222;
        color: white;
        padding: 1em;
        margin-bottom: 1em;
      }

      section {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 1em;
      }

      article {
        background: white;
        border: 1px solid #ccc;
        border-radius: 8px;
        padding: 1em;
        box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.1);
      }

      h1,
      h2 {
        margin: 0.5em 0;
      }
    </style>
  </head>
  <body>
    <header></header>
    <section></section>

    <script>
      async function populate() {
        const response = await fetch(
          "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json"
        );
        const superHeroes = await response.json();

        populateHeader(superHeroes);
        populateHeroes(superHeroes);
      }

      function populateHeader(obj) {
        const header = document.querySelector("header");
        const h1 = document.createElement("h1");
        h1.textContent = obj.squadName;
        header.appendChild(h1);

        const p = document.createElement("p");
        p.textContent = `Hometown: ${obj.homeTown} // Formed: ${obj.formed}`;
        header.appendChild(p);
      }

      function populateHeroes(obj) {
        const section = document.querySelector("section");
        obj.members.forEach((hero) => {
          const article = document.createElement("article");

          const h2 = document.createElement("h2");
          h2.textContent = hero.name;

          const p1 = document.createElement("p");
          p1.textContent = `Secret Identity: ${hero.secretIdentity}`;

          const p2 = document.createElement("p");
          p2.textContent = `Age: ${hero.age}`;

          const p3 = document.createElement("p");
          p3.textContent = `Superpowers: ${hero.powers.join(", ")}`;

          article.appendChild(h2);
          article.appendChild(p1);
          article.appendChild(p2);
          article.appendChild(p3);

          section.appendChild(article);
        });
      }

      populate();
    </script>
  </body>
</html>
```

# JavaScript Breakdown

## `populate()` — Fetch the data

```js
async function populate() {
  const response = await fetch(
    "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json"
  );
  const superHeroes = await response.json();

  populateHeader(superHeroes);
  populateHeroes(superHeroes);
}
```

`fetch(...)`: Retrieves the JSON file from the web.

`await response.json()`: Converts it into a JavaScript object.

Then it runs `populateHeader` and `populateHeroes` to add stuff to the page.

## `populateHeader(obj)` — Fills the `<header>`

```js
function populateHeader(obj) {
  const header = document.querySelector("header");
  const h1 = document.createElement("h1");
  h1.textContent = obj.squadName;
  header.appendChild(h1);

  const p = document.createElement("p");
  p.textContent = `Hometown: ${obj.homeTown} // Formed: ${obj.formed}`;
  header.appendChild(p);
}
```

Adds an `<h1>` with the squad’s name.

Adds a `<p>` showing the hometown and formation year.

## `populateHeroes(obj)` — Creates hero cards

```js
function populateHeroes(obj) {
  const section = document.querySelector("section");
  obj.members.forEach((hero) => {
    const article = document.createElement("article");

    const h2 = document.createElement("h2");
    h2.textContent = hero.name;

    const p1 = document.createElement("p");
    p1.textContent = `Secret Identity: ${hero.secretIdentity}`;

    const p2 = document.createElement("p");
    p2.textContent = `Age: ${hero.age}`;

    const p3 = document.createElement("p");
    p3.textContent = `Superpowers: ${hero.powers.join(", ")}`;

    article.appendChild(h2);
    article.appendChild(p1);
    article.appendChild(p2);
    article.appendChild(p3);

    section.appendChild(article);
  });
}
```

Loops through each hero in the members array.

Creates an article (a card) for each:

Adds their name, secret identity, age, and powers.

## Auto-run

```js
populate();
```

As soon as the page loads, it runs `populate()` to fetch and display everything.

### Where’s the data from?

The data comes from this URL:

https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json
