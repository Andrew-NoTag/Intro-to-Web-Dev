# What is an array?

Arrays are generally described as "list-like objects"; they are basically single objects that contain multiple values stored in a list.

If we didn't have arrays, we'd have to store every item in a separate variable, then call the code that does the printing and adding separately for each item.

Creating arrays
Arrays consist of square brackets and items that are separated by commas.

Suppose we want to store a shopping list in an array. Paste the following code into the console:

```js
const shopping = ["bread", "milk", "cheese", "hummus", "noodles"];
console.log(shopping);
```

In the above example, each item is a string, but in an array we can store various data types — `strings`, `numbers`, `objects`, and even other `arrays`. We can also mix data types in a single array — we do not have to limit ourselves to storing only numbers in one array, and in another only strings.

For example:

```js
const sequence = [1, 1, 2, 3, 5, 8, 13];
const random = ["tree", 795, [0, 1, 2]];
```

Create an array of your favorite foods!

Print it to your console.

### Finding the length of an array

You can find out the length of an array (how many items are in it) in exactly the same way as you find out the length (in characters) of a string — by using the `length` property. Try the following:

```js
const shopping = ["bread", "milk", "cheese", "hummus", "noodles"];
console.log(shopping.length); // 5
```

### Accessing and modifying array items

Items in an array are **numbered**, starting from zero. This number is called the _item's index_.

First item has index `0`, the second has index `1`, and so on.

You can access individual items in the array using bracket notation and supplying the item's index, in the same way that you accessed the letters in a string.

Enter the following into your console:

```js
const shopping = ["bread", "milk", "cheese", "hummus", "noodles"];
console.log(shopping[0]);
// returns "bread"
```

You can also modify an item in an array by giving a single array item a new value. Try this:

```js
const shopping = ["bread", "milk", "cheese", "hummus", "noodles"];
shopping[0] = "tahini";
console.log(shopping);
// shopping will now return [ "tahini", "milk", "cheese", "hummus", "noodles" ]
```

    Note: We've said it before, but just as a reminder — JavaScript starts indexing arrays at zero!

Note that an array inside an array is called a **multidimensional array**.

You can access an item inside an array that is itself inside another array by chaining two sets of square brackets together. For example, to access one of the items inside the array that is the third item inside the random array (see previous section), we could do something like this:

```js
const random = ["tree", 795, [0, 1, 2]];
random[2][2];
```

Try making some more modifications to your array examples before moving on.

Play around a bit, and see what works and what doesn't.

### Finding the index of items in an array

If you don't know the index of an item, you can use the indexOf() method.

The indexOf() method takes an item as an argument and will either return the item's index or -1 if the item is not in the array:

```js
const birds = ["Parrot", "Falcon", "Owl"];
console.log(birds.indexOf("Owl")); // 2
console.log(birds.indexOf("Rabbit")); // -1
```

### Adding items

To add one or more items to the end of an array we can use `push()`.

**Note that you need to include one or more items that you want to add to the end of your array.**

```js
const cities = ["Manchester", "Liverpool"];
cities.push("Cardiff");
console.log(cities); // [ "Manchester", "Liverpool", "Cardiff" ]
cities.push("Bradford", "Brighton");
console.log(cities); // [ "Manchester", "Liverpool", "Cardiff", "Bradford", "Brighton" ]
```

The new length of the array is returned when the method call completes.

If you wanted to store the new array length in a variable, you could do something like this:

```js
const cities = ["Manchester", "Liverpool"];
const newLength = cities.push("Bristol");
console.log(cities); // [ "Manchester", "Liverpool", "Bristol" ]
console.log(newLength); // 3
```

To add an item to the start of the array, use `unshift()`:

```js
const cities = ["Manchester", "Liverpool"];
cities.unshift("Edinburgh");
console.log(cities); // [ "Edinburgh", "Manchester", "Liverpool" ]
```

### Removing items

To remove the last item from the array, use `pop()`.

```js
const cities = ["Manchester", "Liverpool"];
cities.pop();
console.log(cities); // [ "Manchester" ]
```

The `pop()` method returns the item that was removed. To save that item in a new variable, you could do this:

```js
const cities = ["Manchester", "Liverpool"];
const removedCity = cities.pop();
console.log(removedCity); // "Liverpool"
```

To remove the first item from an array, use shift():

```js
const cities = ["Manchester", "Liverpool"];
cities.shift();
console.log(cities); // [ "Liverpool" ]
```

If you know the index of an item, you can remove it from the array using `splice()`:

```js
Copy to Clipboard
const cities = ["Manchester", "Liverpool", "Edinburgh", "Carlisle"];
const index = cities.indexOf("Liverpool");
if (index !== -1) {
cities.splice(index, 1);
}
console.log(cities); // [ "Manchester", "Edinburgh", "Carlisle" ]
```

In this call to `splice()`, the first argument says where to start removing items, and the second argument says how many items should be removed.

So you can remove more than one item:

```js
const cities = ["Manchester", "Liverpool", "Edinburgh", "Carlisle"];
const index = cities.indexOf("Liverpool");
if (index !== -1) {
  cities.splice(index, 2);
}
console.log(cities); // [ "Manchester", "Carlisle" ]
```

### Accessing every item

Very often you will want to access every item in the array. You can do this using the `for...of` statement:

```js
const birds = ["Parrot", "Falcon", "Owl"];

for (const bird of birds) {
  console.log(bird);
}
```

Sometimes you will want to do the same thing to each item in an array, leaving you with an array containing the changed items.

You can do this using `map()`. The code below takes an array of numbers and doubles each number:

```js
function double(number) {
return number \* 2;
}
const numbers = [5, 2, 7, 6];
const doubled = numbers.map(double);
console.log(doubled); // [ 10, 4, 14, 12 ]
```

We give a function to the `map()`, and `map()` calls the function once for each item in the array, passing in the item.

It then adds the return value from each function call to a new array, and finally returns the new array.

Sometimes you'll want to create a new array containing only the items in the original array that match some test.

You can do that using `filter()`. The code below takes an array of strings and returns an array containing just the strings that are greater than 8 characters long:

```js
function isLong(city) {
  return city.length > 8;
}
const cities = ["London", "Liverpool", "Totnes", "Edinburgh"];
const longer = cities.filter(isLong);
console.log(longer); // [ "Liverpool", "Edinburgh" ]
```

Like `map()`, we give a function to the `filter()` method, and `filter()` calls this function for every item in the array, passing in the item. If the function returns true, then the item is added to a new array. Finally it returns the new array.

### Converting between strings and arrays

Often you'll be presented with some raw data contained in a big long string, and you might want to separate the useful items out into a more useful form and then do things to them, like display them in a data table.

To do this, we can use the `split()` method.

Let's play with this, to see how it works. First, create a string in your console:

```js
const data = "Manchester,London,Liverpool,Birmingham,Leeds,Carlisle";
```

Now let's split it at each comma:

```js
const cities = data.split(",");
cities;
```

Finally, try finding the length of your new array, and retrieving some items from it:

```js
cities.length;
cities[0]; // the first item in the array
cities[1]; // the second item in the array
cities[cities.length - 1]; // the last item in the array
```

You can also go the opposite way using the `join()` method. Try the following:

```js
const commaSeparated = cities.join(",");
commaSeparated;
```

## In Class Exercise: Favorite Things Elimination Challenge

#### 1. Input Your Favorite Things:

Create an array of your favorite things in a particular category.

For example, it could be:

- **Favorite Foods**
- **Favorite Movies**
- **Favorite Sports**
- **Favorite Hobbies**

Example:

```js
const favoriteFoods = ["Pizza", "Burgers", "Sushi", "Pasta", "Tacos"];
console.log(favoriteFoods);
```

#### 2. Eliminate the first item in your list.

Use `shift()` to remove the first item:

```js
favoriteFoods.shift();
console.log(favoriteFoods); // First item is removed.
Condition 2: "Remove an item of your choice."
```

#### 3. Find then remove

Use `indexOf()` to find the index of the item you want to remove and then `splice()` to remove it.

```js
const index = favoriteFoods.indexOf("Sushi");
if (index !== -1) {
  favoriteFoods.splice(index, 1); // Remove "Sushi"
}
console.log(favoriteFoods);
```

#### 4. Remove all items that start with the letter 'P'.

Use `filter()` to create a new array with only items that don't start with 'P'.

#### 5. Remove Items Until One is Left (Elimination Game):

Create a loop that continues to remove the first item from the array until only one item is left.

```js
while (favoriteFoods.length > 1) {
  favoriteFoods.shift();
}
console.log(favoriteFoods); // Only one item remains.
```

#### 6. "Reorganize" the List:

Use `sort()` to reorder their remaining items alphabetically.

```js
favoriteFoods.sort();
console.log(favoriteFoods); // Alphabetically sorted list.
```
