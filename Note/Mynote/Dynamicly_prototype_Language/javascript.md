## Table of Contents
- [Variables and Constants](#variables-and-constants)
- [Data Types](#data-types)
- [Operators](#operators)
- [Conditional Statements](#conditional-statements)
- [Switch Statement](#switch-statement)
- [Loops](#loops)
- [Functions](#functions)
- [Arrays](#arrays)
- [Objects](#objects)
- [Classes](#classes)
- [Async/Await](#asyncawait)
- [Promises](#promises)

## Variables and Constants
```js
// Variables
let variableName = 'Hello';
var variableName = 'World';

// Constants
const constantName = 'Cannot be changed or mutable';
```

## Data Types
```js
// Primitive data types
let number = 32;       // Number
let string = 'waiyat';  // String
let boolean = true;    // Boolean
let undef;             // Undefined
let empty = null;      // Null

// Object data type
let obj = { name: 'waiyat', age: number }; // Object
```

## Operators
```js

// Arithmetic Operators
let sum = 5 + 2;      // Addition
let diff = 5 - 2;     // Subtraction
let product = 5 * 2;  // Multiplication
let quotient = 5 / 2; // Division
let remainder = 5 % 2; // Modulus

// Comparison Operators
let isEqual = (5 == '5'); // true
let isStrictEqual = (5 === '5'); // false
let isNotEqual = (5 != '5'); // false
let isGreater = (5 > 2); // true

// Logical Operators
let and = (true && false); // false
let or = (true || false);  // true
let not = !true;           // false

```

## Conditional Statements
```js
// if...else statement
if (condition) {
  // code block
} else if (anotherCondition) {
  // another code block
} else {
  // fallback code block
}

// Ternary operator
let result = (age >= 18) ? 'Adult' : 'Minor';
```



## Switch Statement 
Switch Statement in JS is use  to perform different actions based on different conditions
```javascript
switch (expression) {
  case value1:
    // code to be executed if expression === value1
    break;
  case value2:
    // code to be executed if expression === value2
    break;
  default:
    // code to be executed if expression doesn't match any case
}
```




## Loops
```js
// for loop
for (let i = 0; i < 5; i++) {
  console.log(i);
}

// while loop
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// do...while loop
do {
  console.log(i);
  i++;
} while (i < 5);
```

## Functions
```js
// Function declaration
function greet(name) {
  return `Hello, ${name}!`;
}

// Function expression
const add = function(x, y) {
  return x + y;
};

// Arrow function
const multiply = (x, y) => x * y;
```

## Arrays
```js
// Array of idols
let idols = ['lisa', 'chaewon', 'iu'];

// Accessing elements
console.log(idols[0]); // lisa

// Array methods
idols.push('eunchae');    // Adds an idol to the end
idols.pop();            // Removes the last idol
idols.shift();          // Removes the first idol
idols.unshift('hanni'); // Adds an idol to the beginning

// Loop through elements using forEach
idols.forEach(idol => console.log(idol)); 

//
let upperCaseIdols = idols.map(idols => idols.toUpperCase());
```



## Objects
```js
// Object
let person = {
  name: 'Yuqi',
  age: 23,
  greet: function() {
    console.log('Hello, I am Yuqi!');
  }
};

// Access properties
console.log(person.name); // Yuqi
person.greet(); // Hello, I am Yuqi!

// Add new properties
person.group = 'G(I)-DLE';
```




## Classes
```js
// Class definition
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

// Create an instance
let person1 = new Person('Eunchae', 25);
person1.greet(); // Hello, my name is Eunchae
```




## Async/Await
- Async: allows the computer to do other things while waiting for a slow task (like loading or fetching data). 
 Instead of just sitting and waiting, it can run other parts of the code at the same time. Its a promise 
- Await:  special pause button. It tells the computer "Wait right here! Don't move forward until this specific thing is done"
```js
// Async/Await
async function fetchData() {
  try {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```





## Promises
1) A Promise is like that—you ask JavaScript to do something (like fetch data from the internet), but it doesn’t happen immediately.
2) A Promise will tells you:
  - "either it complete the task 
  - "or something goes wrong."

```js
// Promise
let promise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve('Operation successful');
  } else {
    reject('Operation failed');
  }
});

// Using promises
promise.then(response => console.log(response))
       .catch(error => console.log(error));

```