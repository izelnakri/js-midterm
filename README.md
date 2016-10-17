Instructions:

- Add your answers inline to the markdown file.
- Use your own words.
- Come up with an answer from memory. Write it down, even if the answer is "I don't know."
- Then, we will go over the answers in class. Write down your revised answer below your original answer.

---
### Part 1: Control Flow - 15 minutes

1. Draw a diagram of an if statement. Name each of the components and how they work together.

  ```js
  if (condition) {
    // executes if condition is truthy.
  }
  ```

2. Draw a diagram of a for loop. Describe each of its components. Indicate the order in which they are executed / evaluated.

  ```js
  for (startWithVariable, endCondition; iterator) {
    // executes this block of code in each loop
  }
  ```

3. Functions
 - 3a. Draw a diagram of a function. Describe each of its components and what each component does. Specify which of them are optional.

 ```js
 function functionName(parameter1, parameter2) {
   // block that gets executed when function runs
   return parameter1;
 }



// parameters are optional
// functionNames are optional
// returning something is optional, otherwise function will return `undefined`
```

 - 3b. Draw a diagram of a function being called, showing the instruction execution order.

 ```js
 functionOne(); // we need paranthesis to run the functions
 functionTwo(); // runs without waiting for the result of functionOne
 ```
 ---

### Part 2: Data Types - 10 minutes

4. Primitive Data Types
 - 4a. Give an example of an empty string and a non-empty string.
 ```js
 // Empty String
 ''
 // Non-Empty string
 'abc'
 ```

 - 4b. Give an example of a boolean.
 ```js
 true
 // or:
 false
 ```
 - 4c. Give an example of a Number.
 ```js
 26
 ```

5. Arrays
 - 5a. Give an example of an empty array.
 ```js
 []
 ```
 - 5b. Give an example of an array with three elements in it.
 ```js
 var array = [1, 'abc', [1, 4, true]];
 ```

 - 5c. How do you add another element to this array?
 ```js
 array.push(value)
 ```
 - 5d. How do you get the length of this array?
 ```js
 array.length // will return 3
 ```
 - 5e. Show how to iterate through the array using a loop.
 ```js
 for (var i = 0; i < array.length; i++) {
   array[i] // this will return each element in the loop we can use it inside this block
 }
 ```

6. Objects
 - 6e. Give an example of an empty object.
 ```js
 {}
 ```
 - 6b. Give an example of an object with three keys and three values.
 ```js
 var exampleObject = {
   propertyOne: 'a',
   propertyTwo: 11,
   propertyThree: false
 };
 ```
 - 6c. Give an example of an object with two keys and two functions as values.
```js
 var object = {
   getName: function() {
     console.log('object');
   },
   sayHello: function(name) {
      if (name) {
        return console.log('Hello, ' + name);
      }

      return console.log('Hello!');
   }
 };
 ```
 - 6d. Describe one way of adding a key to an object.
 ```js
 object.newKey = value
 ```
 - 6e. Describe the other way of adding a key to an object.
 ```js
 object['anotherWay'] = value;
 ```
 - 6f. Explain the difference between these two ways, and when it is appropriate to use each way.
 when we assign values or access values with bracket notation we need the property to be a string. This is useful
 for metaprogramming purposes. We can dynamically put a variable that holds a string value inside those brackets as well.

 The second way of assigning(the dot notation) is more readable, we should use this technique when we dont need to do any
 metaprogramming, this is a preferred way to set an explicit property to an object.

- 6g. Describe how to iterate though an object using a loop.
  ```js
  Object.keys(yourObject).forEach(function(property) {
    yourObject[property] // this will access each value, we can manipulate it
  })
  // or:

  for (var key in yourObject) {
    yourObject[key] // access each value in loop
  }
  ```
---
### Part 3: Algorithms - 20 minutes

7. What is an algorithm?
  fancy word for elegant solution to a problem.

8. For the following problem, first write down how exactly to solve the problem in English. Once you are able to describe it in English, translate it into code.

```js
// Given an array of values, write a function that finds the index of where the value is located, and if nothing is found, returns -1.
// Do not use the indexOf function.
// example: for ['apple', 'orange', 'pineapple']
	// 'orange' returns '1'
	// 'durian' returns '-1'
```

```js
// SOLUTION:
var array = ['apple', 'orange', 'pineapple'];

findIndex('apple') // should return 0
findIndex('orange') // should return  1
findIndex('pineapple') // should return 2

function findIndex(parameter) { // we can declare the function here because of hoisting
  var foundIndex = -1;

  for (var i = 0; i < array.length; i++) {
    if (array[i] === parameter) {
      foundIndex = i;
    }
  }

  return foundIndex;
}

// extra, not asked, prototype version of the solution:

Array.prototype.indexOf = undefined; // we overwrite the native indexOf() function

Array.prototype.indexOf = function(value) {
  var foundIndex = -1;

  for (var i = 0; i < this.length; i++) {
    if (this[i] === parameter) {
      foundIndex = i;
    }
  }

  return foundIndex;  
}

// now we can do:
['apple', 'orange', 'pineapple'].indexOf('apple'); // 0
array.indexOf('orange'); // 1
['apple', 'orange', 'pineapple'].indexOf('pineapple'); // 2
array.indexOf('cherry'); // -1
```

9. Again, for the following problem, first write down how exactly to solve the problem in English. Once you are able to describe it in English, translate it into code.

```js
// Write a function that finds all the indexes of where the value is located and returns them in an array, and if nothing is found, returns -1
// example: ['apple', 'orange', 'orange', 'pineapple']
	// 'orange' returns [1,2]
```

```js
  var array = ['apple', 'orange', 'orange', 'pineapple'];

  findIndexes('apple') // => [0]
  findIndexes('orange') // => [1, 2]
  findIndexes('pineapple') // => [3]
  findIndexes('awesomeness') // => -1
  findIndexes(5) // => -1

  function findIndexes(parameter) {
    var foundValues = [];

    for (var i = 0; i < array.length; i++) {
      if (array[i] === parameter) {
        foundValues.push(i);
      }
    }

    if (foundValues.length > 0) {
      return foundValues;
    }

    return -1;
  }
```
