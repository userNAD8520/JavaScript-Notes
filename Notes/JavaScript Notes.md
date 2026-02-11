# JavaScript Notes

---

## Table of Contents

- [JavaScript Basics](#javascript-basics)
  - [Data Types](#data-types)
  - [Variables](#variables)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Assignment Operators](#assignment-operators)
  - [Comparison Operators](#comparison-operators)
  - [Logical Operators](#logical-operators)
  - [Comments](#comments)
  - [console.log](#the-consolelog-function)
- [JavaScript Control Flow](#javascript-control-flow)
  - [if Statements](#if-statements)
  - [else if Statements](#else-if-statements)
  - [else Statements](#else-statements)
  - [Ternary Operator](#ternary-operator)
  - [Switch Statement](#switch-statement)
  - [While Loop](#while-loop)
  - [Break & Continue Statements](#break--continue-statements)
  - [Do...While Loop](#dowhile-loop)
  - [For Loop](#for-loop)
  - [For Loops vs Array Methods](#for-loops-vs-array-methods)
- [JavaScript Functions](#javascript-functions)
  - [Function Declaration](#function-declaration)
  - [Function Parameters](#function-parameters)
  - [Function Return](#function-return)
  - [Function Expressions](#function-expressions)
  - [Anonymous Functions](#anonymous-functions)
  - [Arrow Functions](#arrow-functions)
  - [Arrow Functions vs Regular Functions](#arrow-functions-vs-regular-functions)
- [JavaScript Arrays](#javascript-arrays)
  - [Array Declaration](#array-declaration)
  - [Array Indexes](#array-indexes)
  - [Array Length](#array-length)
  - [Array Destructuring](#array-destructuring)
  - [The Spread Operator](#the-spread-operator)
- [JavaScript Array Methods](#javascript-array-methods)
  - [Array Push](#array-push)
  - [Array Pop](#array-pop)
  - [Array Shift](#array-shift)
  - [Array Unshift](#array-unshift)
  - [Array Concat](#array-concat)
  - [Array Slice](#array-slice)
  - [Array Splice](#array-splice)
  - [Array Join](#array-join)
  - [Array Reverse](#array-reverse)
  - [Array Sort](#array-sort)
  - [Array indexOf](#array-indexof)
  - [Array findIndex](#array-findindex)
  - [Array find](#array-find)
  - [Array filter](#array-filter)
  - [Array map](#array-map)
  - [Array reduce](#array-reduce)
  - [Array every](#array-every)
  - [Array some](#array-some)
  - [Array forEach](#array-foreach)
  - [Array isArray](#array-isarray)
  - [Array includes](#array-includes)
  - [Array fill](#array-fill)
  - [Array flat](#array-flat)
  - [Array flatMap](#array-flatmap)
  - [Array from](#array-from)
  - [Array keys](#array-keys)
  - [Array values](#array-values)
  - [Array entries](#array-entries)
- [JavaScript Objects](#javascript-objects)
  - [Object Declaration](#object-declaration)
  - [Object Properties](#object-properties)
  - [Adding Object Properties](#adding-object-properties)
  - [Updating Object Properties](#updating-object-properties)
  - [Deleting Object Properties](#deleting-object-properties)
  - [Checking if a Property Exists](#checking-if-a-property-exists)
  - [Iterating Over Object Properties](#iterating-over-object-properties)
  - [Object Methods](#object-methods)
- [JavaScript String Manipulation](#javascript-string-manipulation)
  - [concat](#concat)
  - [charAt](#charat)
  - [includes](#includes)
  - [indexOf](#indexof)
  - [slice](#slice)
  - [split](#split)
  - [replace](#replace)
  - [toLowerCase](#tolowercase)
  - [toUpperCase](#touppercase)
  - [trim](#trim)
  - [trimLeft & trimRight](#trimleft--trimright)
- [JavaScript String Formatting](#javascript-string-formatting)
  - [Template Literals](#template-literals)
  - [String Concatenation](#string-concatenation)

---

## JavaScript Basics

### Data Types

JavaScript provides seven different data types:

| Data Type | Examples |
|---|---|
| `undefined` | A variable that has not been assigned a value is of type `undefined`. |
| `null` | No value. |
| `string` | `'A'`, `'aa'`, `'Hello!'` |
| `number` | `12`, `-1`, `0.4` |
| `object` | Collection of properties |
| `symbol` | Represents a unique identifier |

---

### Variables

There are three ways to declare variables:

1. **`var`**: Oldest way to declare variables. Not used much in modern JavaScript. Variables declared with `var` are **function-scoped**, meaning they are only available within the function they're declared in.

```javascript
var name = "John";
```

2. **`let`**: Newer way of declaring variables, introduced in ES6. Variables declared with `let` are **block-scoped**, meaning they are only available within the block they're declared in.

```javascript
let age = 25;
```

3. **`const`**: Also introduced in ES6, `const` is used to declare **constants**, i.e., variables that cannot be reassigned. Like `let`, `const` is also block-scoped.

```javascript
const pi = 3.14159;
```

> **Reminders:**
> - Variables declared with `var` are **hoisted** to the top of their scope. This means they can be used before they're declared. This is **not** the case with `let` and `const`.
> - `let` and `const` create variables that are **block-scoped**, meaning they exist only within the block they're declared in. This is different from `var`, which creates **function-scoped** variables.
> - Variables declared with `const` cannot be reassigned. However, if the variable is an object or an array, its properties or elements **can** still be modified.

---

### Arithmetic Operators

Arithmetic operators are used to perform mathematical operations:

| Operator | Description | Example | Result |
|---|---|---|---|
| `+` | Addition | `5 + 2` | `7` |
| `-` | Subtraction | `5 - 2` | `3` |
| `*` | Multiplication | `5 * 2` | `10` |
| `/` | Division | `5 / 2` | `2.5` |
| `%` | Modulus (Remainder) | `5 % 2` | `1` |
| `++` | Increment | `let x = 5; x++` | `6` |
| `--` | Decrement | `let x = 5; x--` | `4` |
| `**` | Exponentiation | `5 ** 2` | `25` |

---

### Assignment Operators

1. **Assignment (`=`)**: Assigns the value on the right to the variable on the left.

```javascript
let x = 10; // x is now 10
```

2. **Addition assignment (`+=`)**: Adds the value on the right to the variable on the left.

```javascript
let x = 5;
x += 10; // x is now 15
```

3. **Subtraction assignment (`-=`)**: Subtracts the value on the right from the variable on the left.

```javascript
let x = 10;
x -= 5; // x is now 5
```

4. **Multiplication assignment (`*=`)**: Multiplies the variable on the left by the value on the right.

```javascript
let x = 5;
x *= 10; // x is now 50
```

5. **Division assignment (`/=`)**: Divides the variable on the left by the value on the right.

```javascript
let x = 10;
x /= 5; // x is now 2
```

6. **Modulus assignment (`%=`)**: Divides the variable on the left by the value on the right and assigns the remainder.

```javascript
let x = 10;
x %= 3; // x is now 1
```

7. **Exponentiation assignment (`**=`)**: Raises the variable on the left to the power of the value on the right.

```javascript
let x = 5;
x **= 2; // x is now 25
```

These operators provide a shorthand way to update the value of a variable in relation to its current value.

---

### Comparison Operators

| Operator | Description | Example | Result |
|---|---|---|---|
| `==` | Equal to | `5 == 5` | `true` |
| `!=` | Not equal to | `5 != 4` | `true` |
| `===` | Strictly equal to | `5 === 5` / `'5' === 5` | `true` / `false` (types differ) |
| `!==` | Strictly not equal to | `5 !== '5'` | `true` |
| `>` | Greater than | `10 > 5` | `true` |
| `<` | Less than | `5 < 10` | `true` |
| `>=` | Greater or equal to | `10 >= 10` | `true` |
| `<=` | Less than or equal to | `5 <= 5` | `true` |

---

### Logical Operators

1. **Logical AND (`&&`)**: Returns `true` if **both** operands are true.

```javascript
true && true;   // true
true && false;  // false
```

2. **Logical OR (`||`)**: Returns `true` if **at least one** of the operands is true.

```javascript
true || false;   // true
false || false;  // false
```

3. **Logical NOT (`!`)**: Returns `true` if the operand is `false`, and vice versa. It reverses the boolean value.

```javascript
!true;   // false
!false;  // true
```

These operators are often used in conditional statements to combine or invert boolean conditions.

---

### Comments

**Single-line comments** are created using two forward slashes `//`. Everything to the right of `//` on the same line is a comment.

```javascript
// This is a single-line comment
```

**Multi-line comments** are created using `/*` to start and `*/` to end. Everything between them is a comment.

```javascript
/*
This is a multi-line comment
It can span multiple lines
*/
```

---

### The console.log Function

The `console.log()` function is used to print output to the console. Useful for debugging.

```javascript
console.log("Hello, World!"); // prints "Hello, World!" to the console
```

You can print the value of variables:

```javascript
let a = 1;
console.log(a); // prints the value of a (1) to the console
```

You can also print multiple values at once by separating them with commas:

```javascript
let a = 1;
let b = 2;
console.log(a, b); // prints "1 2" to the console
```

---

## JavaScript Control Flow

### if Statements

Used to specify a block of code to be executed if a specified condition is `true`.

```javascript
let a = 10;
if (a > 5) {
  console.log('a is greater than 5');
}
```

Because `a` is indeed greater than 5, the message `'a is greater than 5'` will be printed to the console.

---

### else if Statements

Used to specify a new condition to test if the first condition is `false`.

```javascript
let a = 5;
if (a > 5) {
  console.log('a is greater than 5');
} else if (a == 5) {
  console.log('a is equal to 5');
}
```

Because `a` is not greater than 5, the first block is skipped. Since `a` is equal to 5, `'a is equal to 5'` is printed.

---

### else Statements

Used to specify a block of code to be executed if **all** previous conditions are `false`.

```javascript
let a = 4;
if (a > 5) {
  console.log('a is greater than 5');
} else if (a == 5) {
  console.log('a is equal to 5');
} else {
  console.log('a is less than 5');
}
```

Because `a` is neither greater than 5 nor equal to 5, the message `'a is less than 5'` is printed.

---

### Ternary Operator

The ternary operator is a shortcut for the `if` statement. It takes three operands: a condition, a result for `true`, and a result for `false`.

```
condition ? expressionIfTrue : expressionIfFalse
```

```javascript
let a = 10;
let result = a > 5 ? 'a is greater than 5' : 'a is not greater than 5';
console.log(result); // prints "a is greater than 5"
```

The ternary operator is useful for short, simple conditions. For more complex conditions, `if`/`else if`/`else` is more readable.

---

### Switch Statement

The `switch` statement performs different actions based on different conditions. It's a good alternative to a series of `if...else if` statements.

```javascript
switch(expression) {
  case value1:
    // code to be executed if expression equals value1
    break;
  case value2:
    // code to be executed if expression equals value2
    break;
  default:
    // code to be executed if expression doesn't match any cases
}
```

**Example:**

```javascript
let fruit = 'apple';
switch (fruit) {
  case 'banana':
    console.log('I am a banana');
    break;
  case 'apple':
    console.log('I am an apple');
    break;
  default:
    console.log('I am not a banana or an apple');
}
```

Because `fruit` is `'apple'`, the message `'I am an apple'` is printed. The `break` keyword prevents the code from running into the next case automatically.

---

### While Loop

The `while` loop repeatedly executes a block of code as long as a specified condition is `true`.

```javascript
while (condition) {
  // code to be executed as long as the condition is true
}
```

**Example:**

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

The loop prints the numbers `0` through `4`. When `i` becomes `5`, the condition `i < 5` is no longer true, so the loop stops.

---

### Break & Continue Statements

#### Break

The `break` statement exits the current loop prematurely.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;
  }
  console.log(i);
}
// Prints 0 through 4
```

The loop stops when `i` equals `5`, even though the condition `i < 10` would still be true.

#### Continue

The `continue` statement skips the current iteration and moves to the next one.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue;
  }
  console.log(i);
}
// Prints 0 through 4 and 6 through 9
```

The number `5` is not printed because `continue` skips that iteration.

---

### Do...While Loop

The `do...while` loop executes the block of code **once** before checking the condition, then repeats as long as the condition is `true`.

```javascript
do {
  // code to be executed
} while (condition);
```

**Example:**

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

Prints the numbers `0` through `4`.

---

### For Loop

The `for` loop repeatedly executes a block of code a certain number of times.

```javascript
for (initialization; condition; finalExpression) {
  // code to be executed on each loop iteration
}
```

---

### For Loops vs Array Methods

**For Loop:**
- Gives you more control over the looping mechanism (initialization, condition, increment/decrement).
- Can be more efficient for larger datasets.
- Can `break` out of a loop, which is not possible with `forEach`, `map`, etc.

**Array Methods (`forEach`, `map`, `filter`, `reduce`, etc.):**
- Provide a more declarative and readable way to perform operations on arrays.
- `map`, `filter`, `reduce`, etc. return a new array and do **not** mutate the original array.
- Can be chained together for complex operations in a clean, readable way.

**Example — Doubling elements:**

```javascript
// For Loop
let arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length; i++) {
  arr[i] = arr[i] * 2;
}

// Map Method
let arr2 = [1, 2, 3, 4, 5];
let doubled = arr2.map(x => x * 2);
```

In general, if you're working with arrays and don't need to `break`, array methods are cleaner. If you need more control or are working with larger datasets, a `for` loop might be better.

---

## JavaScript Functions

### Function Declaration

A function declaration defines a function using the `function` keyword, followed by the name, parameters in parentheses, and the function body in curly braces.

```javascript
function greet() {
  console.log("Hello, world!");
}

greet(); // Calls the function and prints "Hello, world!"
```

**Key characteristic:** Function declarations are **hoisted**, meaning you can call the function before it's declared in your code:

```javascript
greet(); // This will work!

function greet() {
  console.log("Hello, world!");
}
```

---

### Function Parameters

Function parameters are the names listed in the function definition. They are used to pass values (arguments) into functions.

```javascript
function add(a, b) {
  return a + b;
}

let sum = add(1, 2); // 1 is the argument for 'a', 2 is the argument for 'b'
```

- You can have as many parameters as you want, separated by commas.
- Extra arguments are ignored.
- Missing arguments are set to `undefined`.

---

### Function Return

The `return` statement ends function execution and specifies a value to be returned to the caller.

```javascript
function add(a, b) {
  return a + b;
}

let sum = add(1, 2); // sum is now 3
```

---

### Function Expressions

A function expression defines a function as an expression, assigned to a variable.

```javascript
let greet = function() {
  console.log("Hello, world!");
};

greet(); // Calls the function and prints "Hello, world!"
```

**Function expressions are NOT hoisted**, unlike function declarations:

```javascript
greet(); // This will throw an error!

let greet = function() {
  console.log("Hello, world!");
};
```

---

### Anonymous Functions

An anonymous function is a function without a name. It is usually used where a function is expected as an argument (callbacks, event handlers).

```javascript
let greet = function() {
  console.log("Hello, world!");
};

greet();
```

Anonymous functions as arguments:

```javascript
setTimeout(function() {
  console.log("This message is delayed by 1 second.");
}, 1000);
```

---

### Arrow Functions

Arrow functions provide a concise syntax for writing function expressions. They are anonymous and change the way `this` binds.

```javascript
let greet = () => {
  console.log("Hello, world!");
};

greet();
```

With parameters:

```javascript
let add = (a, b) => a + b;
let sum = add(1, 2); // sum is now 3
```

With a single parameter (parentheses can be omitted):

```javascript
let square = x => x * x;
let result = square(5); // result is now 25
```

---

### Arrow Functions vs Regular Functions

| Feature | Regular Functions | Arrow Functions |
|---|---|---|
| **Syntax** | `function(a, b) { return a + b; }` | `(a, b) => a + b` |
| **`this` keyword** | Refers to the object that called the function | Lexically bound (inherits `this` from surrounding code) |
| **`arguments` object** | Has its own `arguments` object | Does **not** have `arguments`; use rest parameters instead |
| **Constructors** | Can be used with `new` | Cannot be used with `new` |
| **Method definitions** | Preferred for object methods (correct `this`) | Not ideal for object methods |

**`this` example:**

```javascript
// Regular function — `this` is undefined in the inner function
let obj1 = {
  value: 'a',
  createAnonFunction: function() {
    return function() {
      console.log(this.value);
    };
  }
};
obj1.createAnonFunction()(); // undefined

// Arrow function — `this` is inherited from the outer function
let obj2 = {
  value: 'a',
  createArrowFunction: function() {
    return () => {
      console.log(this.value);
    };
  }
};
obj2.createArrowFunction()(); // 'a'
```

---

## JavaScript Arrays

### Array Declaration

Arrays can be declared in several ways:

1. **Array literal** (most common):

```javascript
let fruits = ['apple', 'banana', 'cherry'];
```

2. **Array constructor:**

```javascript
let fruits = new Array('apple', 'banana', 'cherry');
```

3. **`Array.of()` method:**

```javascript
let fruits = Array.of('apple', 'banana', 'cherry');
```

4. **`Array.from()` method:**

```javascript
let fruits = Array.from(['apple', 'banana', 'cherry']);
```

---

### Array Indexes

Each item in an array is assigned a numeric index, starting at `0`.

```javascript
let fruits = ['apple', 'banana', 'cherry'];
console.log(fruits[0]); // 'apple'
console.log(fruits[1]); // 'banana'
console.log(fruits[2]); // 'cherry'
```

You can use the index to modify elements:

```javascript
fruits[1] = 'blueberry'; // changes 'banana' to 'blueberry'
console.log(fruits[1]); // 'blueberry'
```

---

### Array Length

The `length` property returns the number of elements in the array. It's a property, not a method.

```javascript
let fruits = ['apple', 'banana', 'cherry'];
console.log(fruits.length); // 3
```

You can also use `length` to truncate an array:

```javascript
fruits.length = 2;
console.log(fruits); // ['apple', 'banana']
```

---

### Array Destructuring

Array destructuring allows you to unpack values from arrays into distinct variables.

```javascript
let fruits = ['apple', 'banana', 'cherry'];
let [fruit1, fruit2, fruit3] = fruits;

console.log(fruit1); // 'apple'
console.log(fruit2); // 'banana'
console.log(fruit3); // 'cherry'
```

You can skip elements:

```javascript
let [fruit1, , fruit3] = fruits;

console.log(fruit1); // 'apple'
console.log(fruit3); // 'cherry'
```

---

### The Spread Operator

The `...` notation (spread operator) allows an iterable to be expanded in places where zero or more arguments or elements are expected.

**Creating a new array:**

```javascript
let fruits = ['apple', 'banana', 'cherry'];
let moreFruits = [...fruits, 'date', 'elderberry'];

console.log(moreFruits); // ['apple', 'banana', 'cherry', 'date', 'elderberry']
```

**Combining two arrays:**

```javascript
let fruits1 = ['apple', 'banana'];
let fruits2 = ['cherry', 'date'];
let allFruits = [...fruits1, ...fruits2];

console.log(allFruits); // ['apple', 'banana', 'cherry', 'date']
```

---

## JavaScript Array Methods

### Array Push

The `push()` method adds one or more elements to the **end** of an array. It modifies the original array and returns the new length.

```javascript
let fruits = ['apple', 'banana'];
fruits.push('orange'); // fruits is now ['apple', 'banana', 'orange']
```

Adding multiple elements:

```javascript
fruits.push('orange', 'pineapple'); // ['apple', 'banana', 'orange', 'pineapple']
```

---

### Array Pop

The `pop()` method removes the **last** element from an array and returns that element.

```javascript
let fruits = ['apple', 'banana', 'orange'];
let lastFruit = fruits.pop(); // lastFruit is 'orange', fruits is now ['apple', 'banana']
```

---

### Array Shift

The `shift()` method removes the **first** element from an array and returns that element.

```javascript
let fruits = ['apple', 'banana', 'orange'];
let firstFruit = fruits.shift(); // firstFruit is 'apple', fruits is now ['banana', 'orange']
```

---

### Array Unshift

The `unshift()` method adds one or more elements to the **beginning** of an array and returns the new length.

```javascript
let fruits = ['banana', 'orange'];
fruits.unshift('apple'); // fruits is now ['apple', 'banana', 'orange']
```

Adding multiple elements:

```javascript
fruits.unshift('apple', 'pineapple'); // ['apple', 'pineapple', 'banana', 'orange']
```

---

### Array Concat

The `concat()` method merges two or more arrays into a **new** array. It does **not** change the existing arrays.

```javascript
let fruits1 = ['apple', 'banana'];
let fruits2 = ['orange', 'pineapple'];
let allFruits = fruits1.concat(fruits2); // ['apple', 'banana', 'orange', 'pineapple']
```

Concatenating more than two arrays:

```javascript
let fruits3 = ['mango', 'kiwi'];
let allFruits = fruits1.concat(fruits2, fruits3);
// ['apple', 'banana', 'orange', 'pineapple', 'mango', 'kiwi']
```

---

### Array Slice

The `slice()` method returns a **shallow copy** of a portion of an array. The original array is **not** modified.

```javascript
let fruits = ['apple', 'banana', 'orange', 'pineapple', 'mango'];
let citrusFruits = fruits.slice(2, 4); // ['orange', 'pineapple']
```

If `end` is not specified, `slice()` returns all elements from `start` to the end:

```javascript
let someFruits = fruits.slice(2); // ['orange', 'pineapple', 'mango']
```

---

### Array Splice

The `splice()` method changes the contents of an array by removing, replacing, or adding elements. It **modifies** the original array.

**1. Removing elements:**

```javascript
let fruits = ['apple', 'banana', 'orange', 'pineapple', 'mango'];
let removedFruits = fruits.splice(2, 2);
// removedFruits is ['orange', 'pineapple']
// fruits is now ['apple', 'banana', 'mango']
```

**2. Adding elements:**

```javascript
let fruits = ['apple', 'banana', 'mango'];
fruits.splice(2, 0, 'orange', 'pineapple');
// fruits is now ['apple', 'banana', 'orange', 'pineapple', 'mango']
```

**3. Replacing elements:**

```javascript
let fruits = ['apple', 'banana', 'mango'];
fruits.splice(1, 1, 'orange');
// fruits is now ['apple', 'orange', 'mango']
```

---

### Array Join

The `join()` method joins all elements of an array into a string. The default separator is a comma (`,`).

```javascript
let fruits = ['apple', 'banana', 'orange'];
let fruitsString = fruits.join(); // 'apple,banana,orange'
```

With a custom separator:

```javascript
let fruitsString = fruits.join(' - '); // 'apple - banana - orange'
```

---

### Array Reverse

The `reverse()` method reverses the order of elements in an array **in place** (mutates the original).

```javascript
let fruits = ['apple', 'banana', 'orange'];
fruits.reverse(); // ['orange', 'banana', 'apple']
```

---

### Array Sort

The `sort()` method sorts elements in place. By default, it converts elements to strings and sorts by UTF-16 code unit values.

```javascript
let fruits = ['banana', 'apple', 'orange'];
fruits.sort(); // ['apple', 'banana', 'orange']
```

> **Warning:** `sort()` can behave unexpectedly with numbers. Use a compare function for numeric sorting:

```javascript
let numbers = [40, 1, 5, 200];
numbers.sort(function(a, b) {
  return a - b;
}); // [1, 5, 40, 200]
```

---

### Array indexOf

The `indexOf()` method returns the **first index** of a specified element, or `-1` if not found.

```javascript
let fruits = ['apple', 'banana', 'orange'];
let index = fruits.indexOf('banana'); // 1
let index2 = fruits.indexOf('pineapple'); // -1
```

---

### Array findIndex

The `findIndex()` method returns the index of the **first element** that satisfies a testing function, or `-1` if none found.

```javascript
let numbers = [5, 12, 8, 130, 44];
let isLargeNumber = (element) => element > 13;
let index = numbers.findIndex(isLargeNumber); // 3
```

---

### Array find

The `find()` method returns the **value** of the first element that satisfies a testing function, or `undefined` if none found.

```javascript
let numbers = [5, 12, 8, 130, 44];
let isLargeNumber = (element) => element > 13;
let found = numbers.find(isLargeNumber); // 130
```

---

### Array filter

The `filter()` method creates a **new array** with all elements that pass the test.

```javascript
let numbers = [5, 12, 8, 130, 44];
let isLargeNumber = (element) => element > 13;
let filtered = numbers.filter(isLargeNumber); // [130, 44]
```

If no elements pass, it returns an empty array `[]`.

---

### Array map

The `map()` method creates a **new array** with the results of calling a function on every element.

```javascript
let numbers = [1, 4, 9, 16];
let roots = numbers.map(Math.sqrt); // [1, 2, 3, 4]
```

With a custom function:

```javascript
let doubles = numbers.map((num) => num * 2); // [2, 8, 18, 32]
```

---

### Array reduce

The `reduce()` method applies a function against an **accumulator** and each element to reduce the array to a single value.

```javascript
let numbers = [1, 2, 3, 4];
let sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue);
// sum is 10
```

With an initial value:

```javascript
let sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 10);
// sum is 20
```

---

### Array every

The `every()` method tests whether **all** elements pass the test. Returns a Boolean.

```javascript
let numbers = [1, 30, 39, 29, 10, 13];
let isBelowThreshold = (currentValue) => currentValue < 40;
let result = numbers.every(isBelowThreshold); // true
```

---

### Array some

The `some()` method tests whether **at least one** element passes the test. Returns a Boolean.

```javascript
let numbers = [1, 2, 3, 4, 5];
let isEven = (element) => element % 2 === 0;
let result = numbers.some(isEven); // true
```

---

### Array forEach

The `forEach()` method executes a provided function once for each array element. It does **not** return a value.

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.forEach((element) => console.log(element));
```

> **Note:** If you need a new array, use `map()`. If you need a Boolean, use `every()` or `some()`. If you need to find an element, use `find()`.

---

### Array isArray

The `Array.isArray()` method determines whether the passed value is an Array. Returns a Boolean.

```javascript
let fruits = ['apple', 'banana', 'orange'];
Array.isArray(fruits); // true

let number = 123;
Array.isArray(number); // false
```

---

### Array includes

The `includes()` method determines whether an array includes a certain value. Returns `true` or `false`.

```javascript
let fruits = ['apple', 'banana', 'orange'];
fruits.includes('banana');    // true
fruits.includes('pineapple'); // false
```

---

### Array fill

The `fill()` method changes all elements in an array to a static value. It modifies the original array.

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.fill(0); // [0, 0, 0, 0, 0]
```

With start and end index:

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.fill(0, 1, 3); // [1, 0, 0, 4, 5]
```

---

### Array flat

The `flat()` method creates a new array with all sub-array elements concatenated recursively up to the specified depth.

```javascript
let nestedArray = [1, 2, [3, 4]];
let flatArray = nestedArray.flat(); // [1, 2, 3, 4]
```

For deeper nesting, specify the depth:

```javascript
let deeplyNestedArray = [1, [2, [3, [4]]]];
let flatArray = deeplyNestedArray.flat(3); // [1, 2, 3, 4]
```

---

### Array flatMap

The `flatMap()` method first maps each element using a mapping function, then flattens the result by one level. More efficient than calling `map()` then `flat()`.

```javascript
let arr = [1, 2, 3, 4];
let newArr = arr.flatMap(x => [x * 2]); // [2, 4, 6, 8]
```

Interleaving data:

```javascript
let arr = ["it's Sunny in", "", "California"];
let newArr = arr.flatMap(x => x.split(' '));
// ["it's", "Sunny", "in", "", "California"]
```

---

### Array from

The `Array.from()` method creates a new, shallow-copied Array from an array-like or iterable object.

```javascript
let string = 'hello';
let array = Array.from(string); // ['h', 'e', 'l', 'l', 'o']
```

---

### Array keys

The `keys()` method returns a new Array Iterator containing the **keys** (indices) for each index.

```javascript
let array = ['a', 'b', 'c'];
let iterator = array.keys();

for (let key of iterator) {
  console.log(key); // 0, then 1, then 2
}
```

---

### Array values

The `values()` method returns a new Array Iterator containing the **values** for each index.

```javascript
let array = ['a', 'b', 'c'];
let iterator = array.values();

for (let value of iterator) {
  console.log(value); // 'a', then 'b', then 'c'
}
```

---

### Array entries

The `entries()` method returns a new Array Iterator containing **key/value pairs** for each index.

```javascript
let array = ['a', 'b', 'c'];
let iterator = array.entries();

for (let [index, value] of iterator) {
  console.log(`index: ${index}, value: ${value}`);
  // 'index: 0, value: a', 'index: 1, value: b', 'index: 2, value: c'
}
```

---

## JavaScript Objects

JavaScript objects are containers for named values, called **properties** and **methods**.

```javascript
let car = {
  maker: "Toyota",
  model: "Camry",
  year: 2020,
  startEngine: function() {
    return "Engine started";
  }
};
```

Access properties using **dot notation** (`car.maker`) or **bracket notation** (`car["maker"]`), and call methods like `car.startEngine()`.

---

### Object Declaration

1. **Object Literal Syntax** (most common):

```javascript
let obj = {
  key1: 'value1',
  key2: 'value2',
  key3: 'value3'
};
```

2. **Object Constructor:**

```javascript
let obj = new Object();
obj.key1 = 'value1';
obj.key2 = 'value2';
obj.key3 = 'value3';
```

3. **Constructor Function** (for creating multiple objects with the same structure):

```javascript
function MyObject(key1, key2, key3) {
  this.key1 = key1;
  this.key2 = key2;
  this.key3 = key3;
}

let obj = new MyObject('value1', 'value2', 'value3');
```

---

### Object Properties

You can read an object property using **dot notation** or **bracket notation**.

```javascript
let obj = {
  key1: 'value1',
  key2: 'value2',
  key3: 'value3'
};

console.log(obj.key1);      // 'value1'
console.log(obj['key1']);    // 'value1'
```

---

### Adding Object Properties

Add properties after creation using dot or bracket notation.

```javascript
let obj = { key1: 'value1', key2: 'value2' };

obj.key3 = 'value3';        // Dot notation
obj['key4'] = 'value4';     // Bracket notation
```

---

### Updating Object Properties

Update existing properties the same way you add them:

```javascript
let obj = { key1: 'value1' };
obj.key1 = 'newValue1';
console.log(obj.key1); // 'newValue1'
```

---

### Deleting Object Properties

Use the `delete` operator to remove properties:

```javascript
let obj = {
  key1: 'value1',
  key2: 'value2',
  key3: 'value3'
};

delete obj.key1;
console.log(obj.key1); // undefined
```

---

### Checking if a Property Exists

1. **The `in` operator:**

```javascript
let obj = { key1: 'value1', key2: 'value2' };

console.log('key1' in obj); // true
console.log('key3' in obj); // false
```

2. **The `hasOwnProperty` method** (checks own properties only, not inherited):

```javascript
console.log(obj.hasOwnProperty("key1")); // true
console.log(obj.hasOwnProperty("key3")); // false
```

3. **Direct property access** (check if value is `undefined`):

```javascript
console.log(obj.key1 !== undefined); // true
console.log(obj.key3 !== undefined); // false
```

> **Note:** Method 3 can give false negatives if the property exists but its value is `undefined`.

---

### Iterating Over Object Properties

Use a `for...in` loop to iterate over an object's properties:

```javascript
let obj = {
  key1: 'value1',
  key2: 'value2',
  key3: 'value3'
};

for (let key in obj) {
  if (obj.hasOwnProperty(key)) {
    console.log(key + ": " + obj[key]);
  }
}
// Output:
// key1: value1
// key2: value2
// key3: value3
```

The `hasOwnProperty` check ensures the property belongs to the object itself and not its prototype chain.

---

### Object Methods

Objects can have methods — functions stored as object properties.

```javascript
let obj = {
  property1: 'value1',
  property2: 'value2',
  myMethod: function() {
    console.log('This is a method!');
  }
};

obj.myMethod(); // 'This is a method!'
```

Using `this` to refer to the object:

```javascript
let obj = {
  property1: 'value1',
  myMethod: function() {
    console.log('Property1 is ' + this.property1);
  }
};

obj.myMethod(); // 'Property1 is value1'
```

---

## JavaScript String Manipulation

### concat

The `concat` method joins two or more strings. It does **not** change the existing strings.

```javascript
let str1 = "Hello, ";
let str2 = "World!";
let result = str1.concat(str2);

console.log(result); // "Hello, World!"
```

---

### charAt

The `charAt` method returns the character at a specific index (0-based).

```javascript
let str = "Hello, World!";
let char = str.charAt(7);

console.log(char); // "W"
```

---

### includes

The `includes` method determines whether one string can be found within another. Returns `true` or `false`. **Case-sensitive.**

```javascript
let str = "Hello, World!";
let result = str.includes("World");

console.log(result); // true
```

---

### indexOf

The `indexOf` method returns the index of the first occurrence of a specified value, or `-1` if not found. **Case-sensitive.**

```javascript
let str = "Hello, World!";
let index = str.indexOf("World");

console.log(index); // 7
```

---

### slice

The `slice` method extracts a section of a string and returns it as a new string. Takes a start index (inclusive) and end index (exclusive).

```javascript
let str = "Hello, World!";
let slicedStr = str.slice(7, 12);

console.log(slicedStr); // "World"
```

---

### split

The `split` method divides a string into an array of substrings based on a separator.

```javascript
let str = "Hello, World!";
let array = str.split(", ");

console.log(array); // ["Hello", "World!"]
```

---

### replace

The `replace` method replaces a specified value with another value. Returns a new string; the original is **not** modified.

```javascript
let str = "Hello, World!";
let newStr = str.replace("World", "Universe");

console.log(newStr); // "Hello, Universe!"
```

---

### toLowerCase

The `toLowerCase` method converts a string to lowercase. Returns a new string.

```javascript
let str = "Hello, World!";
let lowerCaseStr = str.toLowerCase();

console.log(lowerCaseStr); // "hello, world!"
```

---

### toUpperCase

The `toUpperCase` method converts a string to uppercase. Returns a new string.

```javascript
let str = "Hello, World!";
let upperCaseStr = str.toUpperCase();

console.log(upperCaseStr); // "HELLO, WORLD!"
```

---

### trim

The `trim` method removes whitespace from **both ends** of a string. Returns a new string.

```javascript
let str = "   Hello, World!   ";
let trimmedStr = str.trim();

console.log(trimmedStr); // "Hello, World!"
```

---

### trimLeft & trimRight

`trimLeft` removes whitespace from the **beginning**, `trimRight` from the **end**.

```javascript
let str = "   Hello, World!   ";
let trimmedLeftStr = str.trimLeft();
let trimmedRightStr = str.trimRight();

console.log(trimmedLeftStr);  // "Hello, World!   "
console.log(trimmedRightStr); // "   Hello, World!"
```

---

## JavaScript String Formatting

### Template Literals

Template literals (introduced in ES6) use **backticks** (`` ` ``) and allow embedded expressions via `${expression}`.

```javascript
let name = "John";
let age = 30;
let greeting = `Hello, my name is ${name} and I am ${age} years old.`;

console.log(greeting); // "Hello, my name is John and I am 30 years old."
```

---

### String Concatenation

**Using the `+` operator:**

```javascript
let str1 = "Hello, ";
let str2 = "World!";
let result = str1 + str2;

console.log(result); // "Hello, World!"
```

**Using the `concat` method:**

```javascript
let str1 = "Hello, ";
let str2 = "World!";
let result = str1.concat(str2);

console.log(result); // "Hello, World!"
```

> **Recommended:** Use **template literals** for string formatting as they are the most readable and modern approach.
