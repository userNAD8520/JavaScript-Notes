# JavaScript Comprehensive Notes
## Table of Contents

1. [JavaScript Basics](#1-javascript-basics)
    - [1.1 Data Types](#11-data-types)
    - [1.2 Variables](#12-variables)
    - [1.3 Arithmetic Operators](#13-arithmetic-operators)
    - [1.4 Assignment Operators](#14-assignment-operators)
    - [1.5 Comparison Operators](#15-comparison-operators)
    - [1.6 Logical Operators](#16-logical-operators)
    - [1.7 Comments](#17-comments)
    - [1.8 console.log and Other Console Methods](#18-consolelog-and-other-console-methods)
2. [JavaScript Control Flow](#2-javascript-control-flow)
    - [2.1 if / else if / else Statements](#21-if--else-if--else-statements)
    - [2.2 Ternary Operator](#22-ternary-operator)
    - [2.3 Switch Statement](#23-switch-statement)
    - [2.4 While Loop](#24-while-loop)
    - [2.5 Do...While Loop](#25-dowhile-loop)
    - [2.6 For Loop](#26-for-loop)
    - [2.7 Break and Continue](#27-break-and-continue)
    - [2.8 For Loops vs Array Methods](#28-for-loops-vs-array-methods)
3. [JavaScript Functions](#3-javascript-functions)
    - [3.1 Function Declaration (Hoisted)](#31-function-declaration-hoisted)
    - [3.2 Function Parameters](#32-function-parameters)
    - [3.3 Function Return](#33-function-return)
    - [3.4 Function Expressions (Not Hoisted)](#34-function-expressions-not-hoisted)
    - [3.5 Arrow Functions (ES6)](#35-arrow-functions-es6)
    - [3.6 IIFE (Immediately Invoked Function Expression)](#36-iife-immediately-invoked-function-expression)
    - [3.7 Closures](#37-closures)
    - [3.8 Higher-Order Functions](#38-higher-order-functions)
4. [JavaScript Arrays](#4-javascript-arrays)
    - [4.1 Array Declaration](#41-array-declaration)
    - [4.2 Array Indexes and Length](#42-array-indexes-and-length)
    - [4.3 Array Destructuring](#43-array-destructuring)
    - [4.4 The Spread Operator (...)](#44-the-spread-operator-)
5. [JavaScript Array Methods](#5-javascript-array-methods)
    - [5.1 Mutating Methods](#51-mutating-methods-modify-original-array)
    - [5.2 Non-Mutating Methods](#52-non-mutating-methods-return-new-arrayvalue)
6. [JavaScript Objects](#6-javascript-objects)
    - [6.1 Object Declaration](#61-object-declaration)
    - [6.2 Accessing, Adding, Updating, and Deleting Properties](#62-accessing-adding-updating-and-deleting-properties)
    - [6.3 Checking if a Property Exists](#63-checking-if-a-property-exists)
    - [6.4 Iterating Over Objects](#64-iterating-over-objects)
    - [6.5 Useful Object Methods](#65-useful-object-methods)
7. [JavaScript String Manipulation](#7-javascript-string-manipulation)
    - [7.1 String Methods](#71-string-methods)
    - [7.2 Template Literals (ES6)](#72-template-literals-es6)
    - [7.3 String Concatenation](#73-string-concatenation)
8. [Error Handling](#8-error-handling)
9. [Promises and Async/Await](#9-promises-and-asyncawait)
    - [9.1 Promises](#91-promises)
    - [9.2 Async/Await](#92-asyncawait)
10. [Useful Tips and Patterns](#10-useful-tips-and-patterns)
---

## 1. JavaScript Basics

### 1.1 Data Types

JavaScript has **8 data types** (7 primitive + 1 non-primitive):

| Data Type   | Description                                  | Example                                |
| ----------- | -------------------------------------------- | -------------------------------------- |
| `undefined` | A variable declared but not assigned a value | `let x; // x is undefined`             |
| `null`      | Intentional absence of any value             | `let x = null;`                        |
| `string`    | Textual data enclosed in quotes              | `'Hello'`, `"World"`, `` `Template` `` |
| `number`    | Integer or floating-point numbers            | `42`, `-3.14`, `Infinity`, `NaN`       |
| `boolean`   | Logical values                               | `true`, `false`                        |
| `bigint`    | Integers of arbitrary length (ES2020)        | `9007199254740991n`                    |
| `symbol`    | Unique and immutable identifier (ES6)        | `Symbol('id')`                         |
| `object`    | Collection of key-value pairs                | `{ name: 'John' }`, `[1,2,3]`          |

**Additional Notes:**

- `typeof null` returns `"object"` — this is a known JavaScript bug that persists for backward compatibility.
- `NaN` (Not a Number) is of type `number`. Use `Number.isNaN()` to check for it.
- Arrays, functions, dates, and regex are all technically objects.

```javascript
// Checking types
typeof "hello"      // "string"
typeof 42           // "number"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" (historical bug)
typeof Symbol('x')  // "symbol"
typeof 10n          // "bigint"
typeof {}           // "object"
typeof []           // "object"
typeof function(){} // "function"
```

#### Type Coercion

JavaScript automatically converts types in certain situations:

```javascript
// Implicit coercion
'5' + 3        // "53" (number coerced to string)
'5' - 3        // 2 (string coerced to number)
true + 1       // 2 (true coerced to 1)
false + 1      // 1 (false coerced to 0)
null + 5       // 5 (null coerced to 0)
undefined + 5  // NaN

// Explicit coercion
Number('42')    // 42
String(42)      // "42"
Boolean(0)      // false
Boolean('')     // false
Boolean('hello') // true
parseInt('42px') // 42
parseFloat('3.14abc') // 3.14
```

#### Truthy and Falsy Values

In JavaScript, values are either "truthy" or "falsy" when evaluated in a boolean context:

```javascript
// Falsy values (all of these evaluate to false):
false, 0, -0, 0n, "", null, undefined, NaN

// Everything else is truthy, including:
"0", "false", [], {}, function(){}
```

---

### 1.2 Variables

There are three ways to declare variables:

#### `var` (Function-scoped, hoisted)

```javascript
var name = "John";
var name = "Jane"; // Re-declaration allowed
name = "Bob";      // Re-assignment allowed

// Hoisting example
console.log(x); // undefined (not an error!)
var x = 5;
// This is because var declarations are hoisted to the top
```

#### `let` (Block-scoped, not hoisted in usable form)

```javascript
let age = 25;
// let age = 30; // ERROR: Cannot re-declare
age = 30;        // Re-assignment allowed

// Block scoping
if (true) {
    let blockVar = "I'm inside a block";
    console.log(blockVar); // "I'm inside a block"
}
// console.log(blockVar); // ERROR: blockVar is not defined

// Temporal Dead Zone (TDZ)
// console.log(y); // ERROR: Cannot access 'y' before initialization
let y = 10;
```

#### `const` (Block-scoped, cannot be reassigned)

```javascript
const PI = 3.14159;
// PI = 3.14; // ERROR: Assignment to constant variable

// IMPORTANT: const with objects and arrays
const person = { name: "John" };
person.name = "Jane";  // This WORKS! Properties can be modified
// person = {};         // ERROR: Cannot reassign the variable

const arr = [1, 2, 3];
arr.push(4);    // This WORKS! [1, 2, 3, 4]
// arr = [5, 6]; // ERROR: Cannot reassign
```

**Best Practice:** Use `const` by default. Use `let` when you need to reassign. Avoid `var`.

---

### 1.3 Arithmetic Operators

| Operator | Description         | Example          | Result |
| -------- | ------------------- | ---------------- | ------ |
| `+`      | Addition            | `5 + 2`          | `7`    |
| `-`      | Subtraction         | `5 - 2`          | `3`    |
| `*`      | Multiplication      | `5 * 2`          | `10`   |
| `/`      | Division            | `5 / 2`          | `2.5`  |
| `%`      | Modulus (Remainder) | `5 % 2`          | `1`    |
| `++`     | Increment           | `let x = 5; x++` | `6`    |
| `--`     | Decrement           | `let x = 5; x--` | `4`    |
| `**`     | Exponentiation      | `5 ** 2`         | `25`   |

**Pre-increment vs Post-increment:**

```javascript
let a = 5;
let b = a++;  // b = 5, a = 6 (returns value THEN increments)
let c = ++a;  // c = 7, a = 7 (increments THEN returns value)

// Practical example
let i = 0;
console.log(i++); // 0 (prints first, then increments)
console.log(i);   // 1
console.log(++i); // 2 (increments first, then prints)
```

**Floating Point Precision:**

```javascript
0.1 + 0.2           // 0.30000000000000004 (not 0.3!)
(0.1 + 0.2).toFixed(1) // "0.3" (use toFixed for display)
Math.abs(0.1 + 0.2 - 0.3) < Number.EPSILON // true (use for comparison)
```

---

### 1.4 Assignment Operators

| Operator | Example     | Equivalent              |
| -------- | ----------- | ----------------------- |
| `=`      | `x = 10`    | Assign 10 to x          |
| `+=`     | `x += 5`    | `x = x + 5`             |
| `-=`     | `x -= 5`    | `x = x - 5`             |
| `*=`     | `x *= 5`    | `x = x * 5`             |
| `/=`     | `x /= 5`    | `x = x / 5`             |
| `%=`     | `x %= 5`    | `x = x % 5`             |
| `**=`    | `x **= 2`   | `x = x ** 2`            |
| `&&=`    | `x &&= 5`   | `x = x && 5` (ES2021)   |
| `\|\|=`  | `x \|\|= 5` | `x = x \|\| 5` (ES2021) |
| `??=`    | `x ??= 5`   | `x = x ?? 5` (ES2021)   |

```javascript
// Logical assignment operators (ES2021)
let a = null;
a ??= 10;     // a = 10 (assigns if null or undefined)

let b = 0;
b ||= 5;      // b = 5 (assigns if falsy)

let c = 1;
c &&= 2;      // c = 2 (assigns if truthy)
```

---

### 1.5 Comparison Operators

| Operator | Description           | Example     | Result  |
| -------- | --------------------- | ----------- | ------- |
| `==`     | Equal to (loose)      | `5 == '5'`  | `true`  |
| `!=`     | Not equal to (loose)  | `5 != '5'`  | `false` |
| `===`    | Strictly equal to     | `5 === '5'` | `false` |
| `!==`    | Strictly not equal to | `5 !== '5'` | `true`  |
| `>`      | Greater than          | `10 > 5`    | `true`  |
| `<`      | Less than             | `5 < 10`    | `true`  |
| `>=`     | Greater or equal to   | `10 >= 10`  | `true`  |
| `<=`     | Less than or equal to | `5 <= 5`    | `true`  |

**`==` vs `===` — Why it matters:**

```javascript
// == performs type coercion
0 == false       // true
'' == false      // true
null == undefined // true
'0' == false     // true

// === does NOT perform type coercion (RECOMMENDED)
0 === false       // false
'' === false      // false
null === undefined // false
'0' === false     // false

// Always use === unless you have a specific reason to use ==
```

---

### 1.6 Logical Operators

| Operator | Name               | Description                                         |
| -------- | ------------------ | --------------------------------------------------- |
| `&&`     | AND                | Returns `true` if both operands are true            |
| `\|\|`   | OR                 | Returns `true` if at least one operand is true      |
| `!`      | NOT                | Inverts the boolean value                           |
| `??`     | Nullish Coalescing | Returns right operand if left is `null`/`undefined` |

```javascript
// AND (&&) - returns first falsy value or last value
true && true      // true
true && false     // false
'hello' && 'world' // 'world'
0 && 'hello'      // 0

// OR (||) - returns first truthy value or last value
true || false     // true
false || false    // false
'' || 'default'   // 'default'
0 || 42           // 42

// NOT (!)
!true             // false
!0                // true
!!''              // false (double NOT for boolean conversion)
!!'hello'         // true

// Nullish Coalescing (??) - only checks null/undefined
null ?? 'default'      // 'default'
undefined ?? 'default' // 'default'
0 ?? 'default'         // 0 (unlike ||, doesn't treat 0 as falsy)
'' ?? 'default'        // '' (unlike ||, doesn't treat '' as falsy)

// Optional Chaining (?.) - often used with ??
let user = { address: { street: "Main St" } };
user?.address?.street   // "Main St"
user?.phone?.number     // undefined (no error!)
user?.phone?.number ?? "N/A" // "N/A"
```

**Short-circuit evaluation:**

```javascript
// && stops at first falsy, || stops at first truthy
let result = false && expensiveFunction(); // expensiveFunction never runs
let name = userInput || "Anonymous";       // default value pattern
```

---

### 1.7 Comments

```javascript
// Single-line comment

/*
  Multi-line comment
  Can span multiple lines
*/

/**
 * JSDoc comment - used for documentation
 * @param {string} name - The name of the person
 * @returns {string} A greeting message
 */
function greet(name) {
    return `Hello, ${name}!`;
}
```

---

### 1.8 console.log and Other Console Methods

```javascript
// Basic logging
console.log("Hello, World!");
console.log("Name:", name, "Age:", age);

// Other useful console methods
console.warn("This is a warning");
console.error("This is an error");
console.info("This is informational");
console.table([{name: "John", age: 30}, {name: "Jane", age: 25}]);
console.time("timer");
// ... some code ...
console.timeEnd("timer"); // Outputs elapsed time
console.group("Group Name");
console.log("Inside group");
console.groupEnd();
console.clear(); // Clears the console
console.assert(1 === 2, "1 is not equal to 2"); // Logs only if assertion fails
console.count("counter"); // Counts how many times this label has been called
console.dir(document.body); // Displays object properties
```

---

## 2. JavaScript Control Flow

### 2.1 if / else if / else Statements

```javascript
let score = 85;

if (score >= 90) {
    console.log("Grade: A");
} else if (score >= 80) {
    console.log("Grade: B");
} else if (score >= 70) {
    console.log("Grade: C");
} else if (score >= 60) {
    console.log("Grade: D");
} else {
    console.log("Grade: F");
}
// Output: "Grade: B"
```

**Nested if statements:**

```javascript
let age = 25;
let hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        console.log("You can drive!");
    } else {
        console.log("You need a license first.");
    }
} else {
    console.log("You're too young to drive.");
}
```

---

### 2.2 Ternary Operator

```javascript
// Syntax: condition ? expressionIfTrue : expressionIfFalse

let age = 20;
let status = age >= 18 ? "adult" : "minor";
console.log(status); // "adult"

// Nested ternary (use sparingly — can reduce readability)
let score = 85;
let grade = score >= 90 ? "A"
          : score >= 80 ? "B"
          : score >= 70 ? "C"
          : "F";
console.log(grade); // "B"

// Ternary in template literals
let isLoggedIn = true;
console.log(`User is ${isLoggedIn ? "online" : "offline"}`);
```

---

### 2.3 Switch Statement

```javascript
let day = "Monday";

switch (day) {
    case "Monday":
    case "Tuesday":
    case "Wednesday":
    case "Thursday":
    case "Friday":
        console.log("Weekday");
        break;
    case "Saturday":
    case "Sunday":
        console.log("Weekend");
        break;
    default:
        console.log("Invalid day");
}
// Output: "Weekday"
```

**Important:** Without `break`, execution "falls through" to the next case:

```javascript
let num = 1;
switch (num) {
    case 1:
        console.log("One");
        // No break — falls through!
    case 2:
        console.log("Two");
        break;
    case 3:
        console.log("Three");
        break;
}
// Output: "One" then "Two" (fall-through behavior)
```

---

### 2.4 While Loop

```javascript
// Basic while loop
let count = 0;
while (count < 5) {
    console.log(count); // 0, 1, 2, 3, 4
    count++;
}

// Infinite loop with break condition
let input;
while (true) {
    input = getInput(); // hypothetical function
    if (input === "quit") break;
    processInput(input);
}
```

---

### 2.5 Do...While Loop

The key difference: the code block executes **at least once** before the condition is checked.

```javascript
let i = 10;
do {
    console.log(i); // Prints 10 even though condition is false
    i++;
} while (i < 5);

// Practical example: input validation
let userInput;
do {
    userInput = prompt("Enter a number greater than 10:");
} while (userInput <= 10);
```

---

### 2.6 For Loop

```javascript
// Standard for loop
for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
}

// Looping backwards
for (let i = 10; i >= 0; i--) {
    console.log(i); // 10, 9, 8, ..., 0
}

// Looping with step
for (let i = 0; i <= 20; i += 5) {
    console.log(i); // 0, 5, 10, 15, 20
}

// for...of (iterates over values — arrays, strings, etc.)
let colors = ["red", "green", "blue"];
for (let color of colors) {
    console.log(color); // "red", "green", "blue"
}

// for...in (iterates over keys/indices — objects)
let person = { name: "John", age: 30, city: "NYC" };
for (let key in person) {
    console.log(`${key}: ${person[key]}`);
}
// name: John, age: 30, city: NYC
```

---

### 2.7 Break and Continue

```javascript
// break — exits the loop entirely
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i); // 0, 1, 2, 3, 4
}

// continue — skips current iteration
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) continue; // skip even numbers
    console.log(i); // 1, 3, 5, 7, 9
}

// Labeled statements (for nested loops)
outer: for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        if (i === 1 && j === 1) break outer; // breaks out of BOTH loops
        console.log(`i=${i}, j=${j}`);
    }
}
```

---

### 2.8 For Loops vs Array Methods

| Feature            | For Loop                           | Array Methods                                |
| ------------------ | ---------------------------------- | -------------------------------------------- |
| Control            | Full control over iteration        | Declarative, less control                    |
| `break`/`continue` | Supported                          | Not supported (except `some`/`every` tricks) |
| Mutation           | Can mutate original array          | `map`, `filter`, `reduce` return new arrays  |
| Readability        | More verbose                       | More concise and expressive                  |
| Chaining           | Not chainable                      | Can chain methods together                   |
| Performance        | Slightly faster for large datasets | Slightly slower but negligible               |

```javascript
// Chaining array methods (powerful pattern)
let result = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    .filter(n => n % 2 === 0)   // [2, 4, 6, 8, 10]
    .map(n => n * 3)             // [6, 12, 18, 24, 30]
    .reduce((sum, n) => sum + n, 0); // 90
```

---

## 3. JavaScript Functions

### 3.1 Function Declaration (Hoisted)

```javascript
// Can be called before declaration due to hoisting
sayHello(); // Works!

function sayHello() {
    console.log("Hello!");
}

// With parameters
function calculateArea(width, height) {
    return width * height;
}
console.log(calculateArea(5, 10)); // 50
```

---

### 3.2 Function Parameters

```javascript
// Default parameters (ES6)
function greet(name = "World") {
    console.log(`Hello, ${name}!`);
}
greet();        // "Hello, World!"
greet("Alice"); // "Hello, Alice!"

// Rest parameters (collects remaining arguments into an array)
function sum(...numbers) {
    return numbers.reduce((total, n) => total + n, 0);
}
console.log(sum(1, 2, 3, 4)); // 10

// Destructured parameters
function displayUser({ name, age, city = "Unknown" }) {
    console.log(`${name}, ${age}, from ${city}`);
}
displayUser({ name: "John", age: 30 }); // "John, 30, from Unknown"

// Arguments object (available in regular functions, NOT arrow functions)
function showArgs() {
    console.log(arguments); // array-like object
    console.log(arguments[0]); // first argument
}
showArgs("a", "b", "c");
```

---

### 3.3 Function Return

```javascript
// Single return value
function add(a, b) {
    return a + b;
}

// Return multiple values using an object
function getMinMax(arr) {
    return {
        min: Math.min(...arr),
        max: Math.max(...arr)
    };
}
let { min, max } = getMinMax([3, 1, 4, 1, 5, 9]);
console.log(min, max); // 1 9

// Early return pattern
function processAge(age) {
    if (age < 0) return "Invalid age";
    if (age < 18) return "Minor";
    return "Adult";
}
```

---

### 3.4 Function Expressions (Not Hoisted)

```javascript
// Anonymous function expression
const greet = function() {
    console.log("Hello!");
};

// Named function expression (useful for recursion and stack traces)
const factorial = function fact(n) {
    return n <= 1 ? 1 : n * fact(n - 1);
};
console.log(factorial(5)); // 120
```

---

### 3.5 Arrow Functions (ES6)

```javascript
// Full syntax
const add = (a, b) => {
    return a + b;
};

// Concise body (implicit return)
const add = (a, b) => a + b;

// Single parameter (parentheses optional)
const square = x => x * x;

// No parameters
const greet = () => "Hello!";

// Returning an object literal (wrap in parentheses)
const createUser = (name, age) => ({ name, age });
console.log(createUser("John", 30)); // { name: "John", age: 30 }
```

#### Arrow Functions vs Regular Functions

| Feature            | Regular Function             | Arrow Function                       |
| ------------------ | ---------------------------- | ------------------------------------ |
| `this` binding     | Dynamic (depends on caller)  | Lexical (inherits from parent scope) |
| `arguments` object | Available                    | Not available (use rest params)      |
| `new` keyword      | Can be used as constructor   | Cannot be used as constructor        |
| `prototype`        | Has prototype property       | No prototype property                |
| Hoisting           | Declarations are hoisted     | Not hoisted                          |
| Method definition  | Preferred for object methods | Avoid for object methods             |

```javascript
// this behavior difference
const obj = {
    value: 42,
    regularMethod: function() {
        setTimeout(function() {
            console.log(this.value); // undefined (this = global/window)
        }, 100);
    },
    arrowMethod: function() {
        setTimeout(() => {
            console.log(this.value); // 42 (this = obj)
        }, 100);
    }
};
```

---

### 3.6 IIFE (Immediately Invoked Function Expression)

```javascript
// Creates a private scope
(function() {
    let privateVar = "I'm private";
    console.log(privateVar);
})();
// console.log(privateVar); // ERROR: not defined

// Arrow function IIFE
(() => {
    console.log("Arrow IIFE");
})();

// With parameters
((name) => {
    console.log(`Hello, ${name}!`);
})("World");
```

---

### 3.7 Closures

A closure is a function that remembers the variables from its outer scope even after the outer function has returned.

```javascript
function createCounter() {
    let count = 0;
    return {
        increment: () => ++count,
        decrement: () => --count,
        getCount: () => count
    };
}

const counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
console.log(counter.getCount()); // 1

// Practical example: function factory
function multiplier(factor) {
    return (number) => number * factor;
}
const double = multiplier(2);
const triple = multiplier(3);
console.log(double(5));  // 10
console.log(triple(5));  // 15
```

---

### 3.8 Higher-Order Functions

Functions that take other functions as arguments or return functions.

```javascript
// Function as argument
function applyOperation(a, b, operation) {
    return operation(a, b);
}
console.log(applyOperation(5, 3, (a, b) => a + b)); // 8
console.log(applyOperation(5, 3, (a, b) => a * b)); // 15

// Function returning a function
function greeting(prefix) {
    return function(name) {
        return `${prefix}, ${name}!`;
    };
}
const sayHi = greeting("Hi");
const sayHello = greeting("Hello");
console.log(sayHi("Alice"));    // "Hi, Alice!"
console.log(sayHello("Bob"));   // "Hello, Bob!"
```

---

## 4. JavaScript Arrays

### 4.1 Array Declaration

```javascript
// Array literal (most common)
let fruits = ['apple', 'banana', 'cherry'];

// Array constructor
let numbers = new Array(1, 2, 3);

// Array.of()
let items = Array.of(1, 2, 3);

// Array.from() — from iterables or array-like objects
let chars = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
let nums = Array.from({length: 5}, (_, i) => i); // [0, 1, 2, 3, 4]

// Empty array with specific length
let empty = new Array(5); // [empty × 5]
let zeros = new Array(5).fill(0); // [0, 0, 0, 0, 0]
```

---

### 4.2 Array Indexes and Length

```javascript
let fruits = ['apple', 'banana', 'cherry'];

// Accessing elements
fruits[0]  // 'apple'
fruits[2]  // 'cherry'
fruits[-1] // undefined (use fruits.at(-1) for last element in ES2022)
fruits.at(-1) // 'cherry' (ES2022)

// Modifying elements
fruits[1] = 'blueberry';

// Length
fruits.length // 3

// Truncating array
fruits.length = 2; // fruits is now ['apple', 'blueberry']
```

---

### 4.3 Array Destructuring

```javascript
let [a, b, c] = [1, 2, 3];
console.log(a, b, c); // 1 2 3

// Skip elements
let [first, , third] = [1, 2, 3];
console.log(first, third); // 1 3

// Rest pattern
let [head, ...tail] = [1, 2, 3, 4, 5];
console.log(head); // 1
console.log(tail); // [2, 3, 4, 5]

// Default values
let [x = 10, y = 20] = [1];
console.log(x, y); // 1 20

// Swapping variables
let m = 1, n = 2;
[m, n] = [n, m];
console.log(m, n); // 2 1

// Nested destructuring
let [a2, [b2, c2]] = [1, [2, 3]];
console.log(a2, b2, c2); // 1 2 3
```

---

### 4.4 The Spread Operator (`...`)

```javascript
// Expanding arrays
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]

// Combining arrays
let combined = [...arr1, ...arr2]; // [1, 2, 3, 1, 2, 3, 4, 5]

// Copying arrays (shallow copy)
let copy = [...arr1]; // [1, 2, 3]

// Spread in function calls
function sum(a, b, c) { return a + b + c; }
console.log(sum(...arr1)); // 6

// Spread with strings
let letters = [..."hello"]; // ['h', 'e', 'l', 'l', 'o']

// Finding max/min
let nums = [3, 1, 4, 1, 5, 9];
Math.max(...nums); // 9
Math.min(...nums); // 1
```

---

## 5. JavaScript Array Methods

### 5.1 Mutating Methods (modify original array)

#### `push()` — Add to end

```javascript
let arr = [1, 2];
arr.push(3);       // arr = [1, 2, 3], returns 3 (new length)
arr.push(4, 5);    // arr = [1, 2, 3, 4, 5], returns 5
```

#### `pop()` — Remove from end

```javascript
let arr = [1, 2, 3];
let last = arr.pop(); // last = 3, arr = [1, 2]
```

#### `unshift()` — Add to beginning

```javascript
let arr = [2, 3];
arr.unshift(1);     // arr = [1, 2, 3], returns 3
arr.unshift(-1, 0); // arr = [-1, 0, 1, 2, 3]
```

#### `shift()` — Remove from beginning

```javascript
let arr = [1, 2, 3];
let first = arr.shift(); // first = 1, arr = [2, 3]
```

#### `splice()` — Remove, add, or replace elements

```javascript
let arr = ['a', 'b', 'c', 'd', 'e'];

// Remove: splice(startIndex, deleteCount)
arr.splice(1, 2);    // removes 'b','c' → arr = ['a', 'd', 'e']

// Add: splice(startIndex, 0, ...items)
arr.splice(1, 0, 'x', 'y'); // arr = ['a', 'x', 'y', 'd', 'e']

// Replace: splice(startIndex, deleteCount, ...items)
arr.splice(1, 1, 'z'); // replaces 'x' with 'z' → arr = ['a', 'z', 'y', 'd', 'e']
```

#### `reverse()` — Reverse in place

```javascript
let arr = [1, 2, 3];
arr.reverse(); // arr = [3, 2, 1]
```

#### `sort()` — Sort in place

```javascript
// Alphabetical (default)
['banana', 'apple', 'cherry'].sort(); // ['apple', 'banana', 'cherry']

// Numeric ascending
[40, 1, 5, 200].sort((a, b) => a - b); // [1, 5, 40, 200]

// Numeric descending
[40, 1, 5, 200].sort((a, b) => b - a); // [200, 40, 5, 1]

// Sort objects by property
let people = [{name: "John", age: 30}, {name: "Jane", age: 25}];
people.sort((a, b) => a.age - b.age);
// [{name: "Jane", age: 25}, {name: "John", age: 30}]
```

#### `fill()` — Fill with static value

```javascript
[1, 2, 3, 4, 5].fill(0);       // [0, 0, 0, 0, 0]
[1, 2, 3, 4, 5].fill(0, 1, 3); // [1, 0, 0, 4, 5]
```

---

### 5.2 Non-Mutating Methods (return new array/value)

#### `concat()` — Merge arrays

```javascript
let a = [1, 2];
let b = [3, 4];
let c = a.concat(b);       // [1, 2, 3, 4]
let d = a.concat(b, [5]);  // [1, 2, 3, 4, 5]
```

#### `slice()` — Extract portion

```javascript
let arr = ['a', 'b', 'c', 'd', 'e'];
arr.slice(1, 3);  // ['b', 'c']
arr.slice(2);     // ['c', 'd', 'e']
arr.slice(-2);    // ['d', 'e']
arr.slice();      // ['a', 'b', 'c', 'd', 'e'] (shallow copy)
```

#### `join()` — Array to string

```javascript
['apple', 'banana', 'cherry'].join();     // "apple,banana,cherry"
['apple', 'banana', 'cherry'].join(' - '); // "apple - banana - cherry"
['2024', '01', '15'].join('-');            // "2024-01-15"
```

#### `indexOf()` — Find index of value

```javascript
let arr = ['a', 'b', 'c', 'b'];
arr.indexOf('b');     // 1 (first occurrence)
arr.indexOf('b', 2);  // 3 (search from index 2)
arr.indexOf('z');     // -1 (not found)
```

#### `includes()` — Check if value exists

```javascript
[1, 2, 3].includes(2);    // true
[1, 2, 3].includes(4);    // false
[1, 2, NaN].includes(NaN); // true (unlike indexOf)
```

#### `find()` — Find first matching element

```javascript
let users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
    { id: 3, name: "Charlie" }
];
let user = users.find(u => u.id === 2);
console.log(user); // { id: 2, name: "Bob" }
```

#### `findIndex()` — Find index of first match

```javascript
let nums = [5, 12, 8, 130, 44];
nums.findIndex(n => n > 13); // 3 (index of 130)
nums.findIndex(n => n > 200); // -1
```

#### `filter()` — Filter elements

```javascript
let nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let evens = nums.filter(n => n % 2 === 0); // [2, 4, 6, 8, 10]

// Remove falsy values
let mixed = [0, 1, false, 2, '', 3, null, undefined, NaN];
let truthy = mixed.filter(Boolean); // [1, 2, 3]

// Remove duplicates (with Set)
let unique = [...new Set([1, 2, 2, 3, 3, 4])]; // [1, 2, 3, 4]
```

#### `map()` — Transform elements

```javascript
let nums = [1, 4, 9, 16];
let roots = nums.map(Math.sqrt);       // [1, 2, 3, 4]
let doubled = nums.map(n => n * 2);    // [2, 8, 18, 32]

// Extract property from objects
let users = [{name: "Alice"}, {name: "Bob"}];
let names = users.map(u => u.name); // ["Alice", "Bob"]
```

#### `reduce()` — Reduce to single value

```javascript
// Sum
let sum = [1, 2, 3, 4].reduce((acc, cur) => acc + cur, 0); // 10

// Max value
let max = [3, 1, 4, 1, 5].reduce((a, b) => Math.max(a, b)); // 5

// Count occurrences
let fruits = ['apple', 'banana', 'apple', 'cherry', 'banana', 'apple'];
let count = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});
// { apple: 3, banana: 2, cherry: 1 }

// Flatten array
let nested = [[1, 2], [3, 4], [5, 6]];
let flat = nested.reduce((acc, arr) => acc.concat(arr), []); // [1,2,3,4,5,6]

// Group by property
let people = [
    { name: "Alice", dept: "Engineering" },
    { name: "Bob", dept: "Marketing" },
    { name: "Charlie", dept: "Engineering" }
];
let grouped = people.reduce((acc, person) => {
    (acc[person.dept] = acc[person.dept] || []).push(person);
    return acc;
}, {});
```

#### `every()` — Test if ALL elements pass

```javascript
[2, 4, 6, 8].every(n => n % 2 === 0);  // true
[2, 4, 5, 8].every(n => n % 2 === 0);  // false
```

#### `some()` — Test if ANY element passes

```javascript
[1, 3, 5, 7].some(n => n % 2 === 0);  // false
[1, 3, 4, 7].some(n => n % 2 === 0);  // true
```

#### `forEach()` — Execute function for each element

```javascript
['a', 'b', 'c'].forEach((element, index) => {
    console.log(`${index}: ${element}`);
});
// 0: a
// 1: b
// 2: c
// Note: forEach returns undefined, cannot break out of it
```

#### `flat()` — Flatten nested arrays

```javascript
[1, [2, [3, [4]]]].flat();    // [1, 2, [3, [4]]]
[1, [2, [3, [4]]]].flat(2);   // [1, 2, 3, [4]]
[1, [2, [3, [4]]]].flat(Infinity); // [1, 2, 3, 4]
```

#### `flatMap()` — Map then flatten (depth 1)

```javascript
let sentences = ["Hello World", "Goodbye Moon"];
let words = sentences.flatMap(s => s.split(' '));
// ["Hello", "World", "Goodbye", "Moon"]

// Useful for filtering and mapping simultaneously
let nums = [1, 2, 3, 4, 5];
nums.flatMap(n => n % 2 === 0 ? [n * 2] : []);
// [4, 8] — filters evens and doubles them
```

#### `Array.isArray()` — Check if value is array

```javascript
Array.isArray([1, 2, 3]);  // true
Array.isArray('hello');     // false
Array.isArray({length: 3}); // false
```

#### `Array.from()` — Create array from iterable

```javascript
Array.from('hello');                    // ['h', 'e', 'l', 'l', 'o']
Array.from({length: 3}, (_, i) => i);  // [0, 1, 2]
Array.from(new Set([1, 1, 2, 3]));     // [1, 2, 3]
```

#### `keys()`, `values()`, `entries()` — Iterators

```javascript
let arr = ['a', 'b', 'c'];

for (let key of arr.keys())     console.log(key);   // 0, 1, 2
for (let val of arr.values())   console.log(val);   // 'a', 'b', 'c'
for (let [i, v] of arr.entries()) console.log(i, v); // 0 'a', 1 'b', 2 'c'
```

---

## 6. JavaScript Objects

### 6.1 Object Declaration

```javascript
// Object literal
let person = {
    name: "John",
    age: 30,
    greet() {
        return `Hi, I'm ${this.name}`;
    }
};

// Object constructor
let obj = new Object();
obj.name = "John";

// Constructor function
function Person(name, age) {
    this.name = name;
    this.age = age;
}
let john = new Person("John", 30);

// ES6 Class syntax
class Animal {
    constructor(name, sound) {
        this.name = name;
        this.sound = sound;
    }
    speak() {
        return `${this.name} says ${this.sound}`;
    }
}
let dog = new Animal("Dog", "Woof");

// Object.create()
let proto = { greet() { return "Hello"; } };
let child = Object.create(proto);
child.greet(); // "Hello"

// Shorthand property names (ES6)
let name = "John", age = 30;
let user = { name, age }; // same as { name: name, age: age }
```

---

### 6.2 Accessing, Adding, Updating, and Deleting Properties

```javascript
let car = { maker: "Toyota", model: "Camry", year: 2020 };

// Access
car.maker;        // "Toyota" (dot notation)
car["model"];     // "Camry" (bracket notation)

// Dynamic property access
let prop = "year";
car[prop];        // 2020

// Update
car.year = 2024;

// Add
car.color = "blue";

// Delete
delete car.color;
console.log(car.color); // undefined

// Computed property names (ES6)
let key = "status";
let obj = { [key]: "active" }; // { status: "active" }
```

---

### 6.3 Checking if a Property Exists

```javascript
let obj = { a: 1, b: undefined };

// in operator (checks own + prototype chain)
'a' in obj;  // true
'c' in obj;  // false

// hasOwnProperty (own properties only)
obj.hasOwnProperty('a'); // true

// Object.hasOwn() (ES2022 — recommended)
Object.hasOwn(obj, 'a'); // true

// Note the difference with undefined values:
obj.b !== undefined; // false (WRONG — property exists but is undefined)
'b' in obj;          // true (CORRECT)
```

---

### 6.4 Iterating Over Objects

```javascript
let person = { name: "John", age: 30, city: "NYC" };

// for...in loop
for (let key in person) {
    if (person.hasOwnProperty(key)) {
        console.log(`${key}: ${person[key]}`);
    }
}

// Object.keys() — array of keys
Object.keys(person);   // ["name", "age", "city"]

// Object.values() — array of values
Object.values(person);  // ["John", 30, "NYC"]

// Object.entries() — array of [key, value] pairs
Object.entries(person); // [["name","John"], ["age",30], ["city","NYC"]]

// Practical: convert entries back to object
let entries = [["name", "John"], ["age", 30]];
let obj = Object.fromEntries(entries); // { name: "John", age: 30 }
```

---

### 6.5 Useful Object Methods

```javascript
// Object.assign() — copy/merge objects
let target = { a: 1 };
let source = { b: 2, c: 3 };
Object.assign(target, source); // target = { a: 1, b: 2, c: 3 }

// Spread operator for objects (ES2018)
let merged = { ...target, ...source, d: 4 };

// Object.freeze() — prevent modifications
let frozen = Object.freeze({ x: 1, y: 2 });
frozen.x = 10; // Silently fails (or throws in strict mode)

// Object.seal() — prevent adding/deleting, allow updating
let sealed = Object.seal({ x: 1, y: 2 });
sealed.x = 10;  // Works
sealed.z = 3;   // Fails
delete sealed.x; // Fails

// Destructuring objects
let { name, age, city = "Unknown" } = person;

// Renaming during destructuring
let { name: fullName, age: years } = person;
console.log(fullName); // "John"
```

---

## 7. JavaScript String Manipulation

### 7.1 String Methods

```javascript
let str = "Hello, World!";

// concat — join strings
str.concat(" How are you?"); // "Hello, World! How are you?"

// charAt — character at index
str.charAt(0);    // "H"
str.charAt(7);    // "W"

// at() — supports negative indexing (ES2022)
str.at(-1);       // "!"

// includes — check substring existence
str.includes("World"); // true
str.includes("world"); // false (case-sensitive)

// indexOf / lastIndexOf — find position
str.indexOf("o");      // 4 (first occurrence)
str.lastIndexOf("o");  // 8 (last occurrence)

// slice — extract substring
str.slice(7, 12);  // "World"
str.slice(-6);     // "orld!"
str.slice(0, 5);   // "Hello"

// substring — similar to slice but no negative indices
str.substring(7, 12); // "World"

// split — string to array
str.split(", ");    // ["Hello", "World!"]
str.split("");      // ["H","e","l","l","o",","," ","W","o","r","l","d","!"]
"a.b.c".split(".");  // ["a", "b", "c"]

// replace — replace first match
str.replace("World", "Universe"); // "Hello, Universe!"

// replaceAll — replace all matches (ES2021)
"aabbcc".replaceAll("a", "x"); // "xxbbcc"

// Regex replace
"Hello 123 World 456".replace(/\d+/g, "#"); // "Hello # World #"

// toLowerCase / toUpperCase
str.toLowerCase(); // "hello, world!"
str.toUpperCase(); // "HELLO, WORLD!"

// trim / trimStart / trimEnd
"  hello  ".trim();      // "hello"
"  hello  ".trimStart();  // "hello  "
"  hello  ".trimEnd();    // "  hello"

// padStart / padEnd
"5".padStart(3, "0");  // "005"
"5".padEnd(3, "0");    // "500"

// repeat
"ha".repeat(3); // "hahaha"

// startsWith / endsWith
"Hello".startsWith("He");  // true
"Hello".endsWith("lo");    // true

// match — regex matching
"test123".match(/\d+/);    // ["123"]
"a1b2c3".match(/\d/g);     // ["1", "2", "3"]

// matchAll (ES2020)
let matches = [...'a1b2c3'.matchAll(/[a-z](\d)/g)];
// [["a1","1"], ["b2","2"], ["c3","3"]]
```

---

### 7.2 Template Literals (ES6)

```javascript
let name = "John";
let age = 30;

// String interpolation
let greeting = `Hello, my name is ${name} and I am ${age} years old.`;

// Multi-line strings
let html = `
    <div>
        <h1>${name}</h1>
        <p>Age: ${age}</p>
    </div>
`;

// Expressions in template literals
let price = 9.99;
let qty = 3;
console.log(`Total: $${(price * qty).toFixed(2)}`); // "Total: $29.97"

// Tagged templates (advanced)
function highlight(strings, ...values) {
    return strings.reduce((result, str, i) => {
        return result + str + (values[i] ? `<b>${values[i]}</b>` : '');
    }, '');
}
let msg = highlight`Hello ${name}, you are ${age} years old.`;
// "Hello <b>John</b>, you are <b>30</b> years old."
```

---

### 7.3 String Concatenation

```javascript
// Using + operator
let result = "Hello" + ", " + "World!"; // "Hello, World!"

// Using concat()
let result2 = "Hello".concat(", ", "World!"); // "Hello, World!"

// Using template literals (RECOMMENDED)
let name = "World";
let result3 = `Hello, ${name}!`; // "Hello, World!"

// Using join() for arrays of strings
let parts = ["Hello", "World"];
let result4 = parts.join(", "); // "Hello, World"
```

---

## 8. Error Handling

```javascript
// try...catch...finally
try {
    let result = riskyOperation();
    console.log(result);
} catch (error) {
    console.error("Error:", error.message);
} finally {
    console.log("This always runs");
}

// Throwing custom errors
function divide(a, b) {
    if (b === 0) throw new Error("Division by zero");
    return a / b;
}

// Error types
// TypeError, ReferenceError, SyntaxError, RangeError, URIError

// Custom error class
class ValidationError extends Error {
    constructor(message, field) {
        super(message);
        this.name = "ValidationError";
        this.field = field;
    }
}
throw new ValidationError("Invalid email", "email");
```

---

## 9. Promises and Async/Await

### 9.1 Promises

```javascript
// Creating a promise
let promise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("Operation succeeded!");
    } else {
        reject("Operation failed!");
    }
});

// Consuming a promise
promise
    .then(result => console.log(result))
    .catch(error => console.error(error))
    .finally(() => console.log("Done"));

// Promise.all — wait for all
Promise.all([fetch(url1), fetch(url2)])
    .then(([res1, res2]) => console.log(res1, res2));

// Promise.race — first to settle
Promise.race([promise1, promise2])
    .then(result => console.log("First:", result));

// Promise.allSettled — wait for all, regardless of outcome
Promise.allSettled([promise1, promise2])
    .then(results => results.forEach(r => console.log(r.status)));
```

### 9.2 Async/Await

```javascript
async function fetchData() {
    try {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        return data;
    } catch (error) {
        console.error("Fetch failed:", error);
    }
}

// Parallel async operations
async function fetchMultiple() {
    let [users, posts] = await Promise.all([
        fetch('/api/users').then(r => r.json()),
        fetch('/api/posts').then(r => r.json())
    ]);
    return { users, posts };
}
```

---

## 10. Useful Tips and Patterns

```javascript
// Nullish coalescing for defaults
let config = userConfig ?? defaultConfig;

// Optional chaining
let street = user?.address?.street ?? "N/A";

// Short-circuit evaluation
isLoggedIn && showDashboard();
isError || continueProcess();

// Object destructuring in function params
function createUser({ name, age, role = "user" }) {
    return { name, age, role };
}

// Array/Object spread for immutable updates
let newArr = [...oldArr, newItem];
let newObj = { ...oldObj, updatedProp: newValue };

// Convert NodeList to Array
let divs = [...document.querySelectorAll('div')];

// Remove duplicates
let unique = [...new Set(array)];

// Check if array is empty
if (arr.length === 0) { /* empty */ }

// Clone object (shallow)
let clone = { ...original };
let clone2 = Object.assign({}, original);

// Clone object (deep)
let deepClone = structuredClone(original); // Modern browsers
let deepClone2 = JSON.parse(JSON.stringify(original)); // Older approach
```

---

*These notes cover JavaScript fundamentals through intermediate concepts. For advanced topics, explore: Prototypes & Inheritance, Modules (import/export), Web APIs (DOM, Fetch, Storage), Event Loop & Microtasks, Generators, Proxies, and WeakMap/WeakSet.*
