# JavaScript Objects

#### Javascript Object Notation

Let’s write our own JavaScript object and access the properties and their individual variables.

Let’s make a variable to hold our javascript object called customer:

```js
var customer = {};
```

Right now, customer is an empty object. So let’s add a few simple properties:

```js
var customer = {
  firstName: "Tony",
  lastName: "Pony",
};
```

Each property consists of a key and a value, or a key value pair. The syntax is:

```js
var myVar = {
  key: value,
  key: value,
};
```

The key value pairs are separated by commas “,” just like in an Array. Remember to not add a comma after the last key value pair.

The values can be Strings | Integers | Floats | Arrays | other Objects or even Functions. Let’s add some more properties to our customer object. We can do this 2 different ways:

Add an array to our pets key we declare the object:

```js
var customer = {
  firstName: "Tony",
  lastName: "Pony",
  pets: ["Dog", "Cat", "Iguana"],
};
```

Access the firstName property with dot notation

```js
console.log(customer.firstName);
```

Access the second pet in the array

```js
console.log(customer.pets[1]);
```

Add an Integer to our customer object later on in our code (maybe we needed some user form input, or to access our users current geolocation before assigning this property a value):

Add a new property later in our code with dot notation

```js
customer.age = 45;
//log out the entire object to see our added property
console.log(customer);
```

## In Class Exercises

### Syntax practice

Get the [_starting point code_](./In_Class_Exercise/objectSyntax.html) for the syntax exercise and read the comments to finish the code.

### Creating your own object literal

This object will represent one of your favorite bands. The required properties are:

- `name`: A string representing the band name.

- `nationality`: A string representing the country the band comes from.

- `genre`: What type of music the band plays.

- `members`: A number representing the number of members the band has.

- `formed`: A number representing the year the band formed.

- `split`: A number representing the year the band split up, or false if they are still together.

- `albums`: An array representing the albums released by the band. Each array item should be an object containing the following members:

  - `name`: A string representing the name of the album.

  - `released`: A number representing the year the album was released.

Include at least two albums in the `albums` array.

_[Starting point html file](./In_Class_Exercise/objectMaking.html)_
