# SECTION 2: JavaScript Fundamentals - Part 1

## Lecture 2: Hello World!

In this lecture, we write our very first JavaScript code using the browser's console. The console is a great place for testing code and fixing errors, though we won't use it for real applications later.

We can open the console in Chrome using:
- Command + Option + J (Mac) / Ctrl + Alt + J (Windows)
- Right-click → Inspect → Console tab
- Menu → View → Developer → JavaScript Console

Let's write our first JavaScript code:
```js
alert('Hello World!');
// We can write any JavaScript and it gets immediately evaluated
const javascript = 'amazing';
if (javascript === 'amazing') alert("Let's learn JavaScript!");
// We can also do math
40 + 8 + 23 - 10; // 61
// Store results in variables
const totalHours = 40 + 8 + 23 - 10;
totalHours; // 61
```

The alert creates a popup with our text. This is just a taste of what JavaScript can do!

---

## Lecture 3: A Brief Introduction to JavaScript

JavaScript is a high-level, object-oriented, multi-paradigm programming language. But what does that actually mean?

- As a programming language, JavaScript allows us to write code that instructs computers to perform actions.
- Being high-level means we don't need to worry about complex details like memory management — there are abstractions that make the language easier to write and learn.
- JavaScript is object-oriented, meaning it's based on the concept of objects for storing data.
- It's also multi-paradigm, allowing different programming styles like imperative and declarative programming.

History and runtime:
- Created in 1995 by Brendan Eich (originally named Mocha → LiveScript → JavaScript).
- JavaScript has evolved significantly:
  - ES5 (2009)
  - ES6 / ES2015 (2015) — major update
  - Annual releases since (ES2016, ES2017, ...)
- Runs in browsers via JS engines (V8 in Chrome, SpiderMonkey in Firefox).
- JavaScript can run outside browsers using Node.js — enabling backend development and full-stack JavaScript.

---

## Lecture 4: Linking a JavaScript File

While we previously wrote code directly in the console, real development involves writing code in files. Let's properly connect JavaScript to our HTML document.

Options:

1. Inline script tags (in HTML)
```html
<script>
  const javascript = 'amazing';
  if (javascript === 'amazing') alert("Let's learn JavaScript!");
  console.log(40 + 8 + 23 - 10);
</script>
```

2. External JavaScript file (recommended)
```html
<!-- In HTML file -->
<script src="script.js"></script>
```
```js
// In script.js file
const javascript = 'amazing';
if (javascript === 'amazing') alert("Let's learn JavaScript!");
console.log(40 + 8 + 23 - 10);
```

Notes:
- External files separate website content (HTML) from logic (JS) for better maintainability.
- When using external files, use `console.log()` to see results in the console (unlike entering code directly into the console).

---

## Lecture 5: Values and Variables

Values are the most fundamental unit of information in programming. We store values in variables to reuse them.

Examples:
```js
// Values
console.log('Jonas'); // String
console.log(23); // Number
console.log(23 + 7); // Expression -> 30

// Storing values in variables
let firstName = 'Jonas';
console.log(firstName);
console.log(firstName);
```

Variable naming rules:
- Use camelCase (e.g., `myFirstJob`)
- Names can contain letters, numbers, underscores, or `$`
- Cannot start with a number
- Cannot use reserved JavaScript keywords
- Variable names should be descriptive

Valid and invalid examples:
```js
// Valid
let _age = 26;
let $name = 'Jonas';
let myFirstJob = 'Programmer';

// Invalid
let 3years = 3;        // cannot start with number
let jonas&matilda = 'JM'; // no special characters
let new = 27;          // 'new' is a reserved keyword

// Less descriptive - avoid
let job1 = 'Programmer';
let job2 = 'Teacher';
```

---

## Lecture 6: Data Types

JavaScript types fall into two main categories:
- Primitive types: Number, String, Boolean, Undefined, Null, Symbol, BigInt
- Object types: Objects, Arrays, Functions, etc.

Dynamic typing:
- Types are determined at runtime and can change when reassigning a variable.

Examples:
```js
let javascriptIsFun = true; // Boolean
console.log(typeof javascriptIsFun); // "boolean"
console.log(typeof 23); // "number"
console.log(typeof 'Jonas'); // "string"

// Dynamic typing
javascriptIsFun = 'YES!';
console.log(typeof javascriptIsFun); // "string"

// Undefined
let year;
console.log(year); // undefined
console.log(typeof year); // "undefined"
year = 1991;
console.log(typeof year); // "number"

// Note: typeof null returns "object" (historical bug)
console.log(typeof null); // "object"
```

---

## Lecture 7: Let, Const, and Var

Three ways to declare variables:

1. let — for variables that can change (block-scoped)
```js
let age = 30;
age = 31; // reassign allowed
let firstName; // can declare without initializing
```

2. const — for variables that shouldn't change (must be initialized)
```js
const birthYear = 1991;
// birthYear = 1990; // Error
// const job; // Error: must initialize
```

3. var — old way (function-scoped; avoid)
```js
var job = 'Programmer';
job = 'Teacher';
```

Best practice:
- Use `const` by default, `let` when reassignment is needed, avoid `var`.

Don't create globals implicitly:
```js
// Don't do this!
lastName = 'Schmedtmann'; // creates global property on window (bad)
```

---

## Lecture 8: Basic Operators

Operators let us transform and combine values.

Math operators:
```js
const now = 2037;
const ageJonas = now - 1991; // 46
const ageSarah = now - 2018; // 19
console.log(ageJonas, ageSarah);
console.log(ageJonas * 2); // 92
console.log(ageJonas / 10); // 4.6
console.log(2 ** 3); // 8 (exponentiation)
```

Concatenation with `+`:
```js
const firstName = 'Jonas';
const lastName = 'Schmedtmann';
console.log(firstName + ' ' + lastName); // "Jonas Schmedtmann"
```

Assignment operators:
```js
let x = 10 + 5; // 15
x += 10; // 25
x *= 4; // 100
x++; // 101
console.log(x);
```

Comparison operators (return boolean):
```js
console.log(ageJonas > ageSarah); // true
console.log(ageSarah >= 18); // true
console.log(now - 1991 > now - 2018); // true
```

---

## Lecture 9: Operator Precedence

JavaScript follows a defined operator precedence, similar to mathematics.

Examples:
```js
const now = 2037;
const ageJonas = now - 1991;
const ageSarah = now - 2018;

// Math before comparison
console.log(now - 1991 > now - 2018); // true (46 > 19)

// Left-to-right for same precedence
console.log(25 - 10 - 5); // 10

// Right-to-left for assignment
let x, y;
x = y = 25 - 10 - 5; // x = y = 10 -> x = 10, y = 10
console.log(x, y);

// Grouping with parentheses
const averageAge = (ageJonas + ageSarah) / 2;
console.log(averageAge); // 32.5
```

Simplified precedence summary (highest to lowest):
1. Parentheses ()
2. Increment/decrement ++/--
3. Exponentiation **
4. Multiply/divide * /
5. Add/subtract + -
6. Comparison < > <= >=
7. Equality == !=
8. Assignment = += -= *= /=

(For full table see MDN documentation.)

---

## Lecture 11: Strings and Template Literals

Template literals make embedding variables and expressions in strings easier.

Examples:
```js
const firstName = 'Jonas';
const job = 'teacher';
const birthYear = 1991;
const year = 2037;

// Old way (concatenation)
const jonasOld =
  "I'm " + firstName + ', a ' + (year - birthYear) + ' year old ' + job + '!';
console.log(jonasOld);

// New way (template literals)
const jonasNew = `I'm ${firstName}, a ${year - birthYear} year old ${job}!`;
console.log(jonasNew);

// Regular template literal
console.log(`Just a regular string!`);

// Multi-line with template literals
console.log(`String with
multiple
lines`);

// Old multi-line (less clean)
console.log('String with \n\
multiple \n\
lines');
```

Template literals (backticks) are more readable and convenient for multi-line strings and interpolation.

---

## Lecture 12: Taking Decisions: if/else Statements

Conditional statements execute different code based on conditions.

Example:
```js
const age = 19;

if (age >= 18) {
  console.log('Sarah can start driving license 🚗');
} else {
  const yearsLeft = 18 - age;
  console.log(`Sarah is too young. Wait another ${yearsLeft} years ⏳`);
}
```

Creating variables conditionally:
```js
const birthYear = 1991;
let century;
if (birthYear <= 2000) {
  century = 20;
} else {
  century = 21;
}
console.log(century);
```

If/else structure:
```txt
if (condition) {
  // runs when condition is TRUE
} else {
  // runs when condition is FALSE
}
```

---

## Lecture 14: Type Conversion and Coercion

JavaScript handles types explicitly (conversion) and implicitly (coercion).

Type Conversion (explicit):
```js
const inputYear = '1991';
console.log(Number(inputYear) + 18); // 2009
console.log(Number('Jonas')); // NaN
console.log(String(23)); // "23"
```

Type Coercion (automatic):
```js
console.log('I am ' + 23 + ' years old'); // + coerces to string
console.log('23' - '10' - 3); // 10 (coerced to numbers)
console.log('23' * '2'); // 46
console.log('23' > '18'); // true
```

Mixed coercion:
```js
let n = '1' + 1; // '11' (string)
n = n - 1; // 10 (number)
console.log(n); // 10
```

Key points:
- `+` with a string converts numbers to strings.
- `-`, `*`, `/`, `>`, `<` convert strings to numbers.
- Understand coercion to avoid unexpected bugs.

---

## Lecture 15: Truthy and Falsy Values

Falsy values (become false when converted to boolean):
- 0
- '' (empty string)
- undefined
- null
- NaN

Examples:
```js
console.log(Boolean(0)); // false
console.log(Boolean('')); // false
console.log(Boolean(undefined)); // false
console.log(Boolean('Jonas')); // true
console.log(Boolean({})); // true
```

Implicit boolean conversion in conditions:
```js
const money = 0;
if (money) {
  console.log("Don't spend it all!");
} else {
  console.log('You should get a job!'); // executes because 0 is falsy
}

let height;
if (height) {
  console.log('Height is defined');
} else {
  console.log('Height is UNDEFINED'); // executes because height is undefined
}
```

Be careful treating `0` or `''` as truthy values.

---

## Lecture 16: Equality Operators: == vs. ===

Equality operators:
- Strict equality `===` — no type coercion
- Loose equality `==` — with type coercion

Examples:
```js
const age = 18;
console.log(age === 18); // true
console.log('18' === 18); // false (different types)
console.log(age == 18); // true
console.log('18' == 18); // true (coerced)
```

Practical example with prompt:
```js
const favourite = Number(prompt("What's your favourite number?"));
if (favourite === 23) {
  console.log('Cool! 23 is an amazing number!');
} else if (favourite === 7) {
  console.log('7 is also a cool number');
} else {
  console.log('Number is not 23 or 7');
}
```

Best practice: always use strict equality (`===`) to avoid unexpected coercion. Convert types explicitly when needed.

---

## Lecture 17: Boolean Logic

Boolean logic uses TRUE and FALSE values with logical operators:
- AND (`&&`): true only if all operands are true
- OR (`||`): true if at least one operand is true
- NOT (`!`): inverts the value

Truth-table summary:
- A && B -> true only when both A and B true
- A || B -> true when either A or B or both true
- !A -> true when A is false

We'll apply these operators in examples below.

---

## Lecture 18: Logical Operators

JavaScript logical operators: `&&`, `||`, and `!`.

Example:
```js
const hasDriversLicense = true; // A
const hasGoodVision = true;     // B
const isTired = false;          // C

// AND
console.log(hasDriversLicense && hasGoodVision); // true

// OR
console.log(hasDriversLicense || hasGoodVision); // true

// NOT
console.log(!hasDriversLicense); // false

// Practical example
const shouldDrive = hasDriversLicense && hasGoodVision && !isTired;
if (shouldDrive) {
  console.log('Sarah is able to drive!');
} else {
  console.log('Someone else should drive...');
}

// Complex condition
console.log(hasDriversLicense && hasGoodVision && !isTired); // true
```

These operators are essential for complex conditions in `if/else` statements.

---

## Lecture 20: The Switch Statement

`switch` provides an alternative to long `if/else` chains when checking one value against multiple options.

Example:
```js
const day = 'monday';

switch (day) {
  case 'monday': // day === 'monday'
    console.log('Plan course structure');
    console.log('Go to coding meetup');
    break; // prevents fall-through

  case 'tuesday':
    console.log('Prepare theory videos');
    break;

  case 'wednesday':
  case 'thursday': // same code for both days
    console.log('Write code examples');
    break;

  case 'friday':
    console.log('Record videos');
    break;

  case 'saturday':
  case 'sunday':
    console.log('Enjoy the weekend :D');
    break;

  default: // like 'else' if no case matches
    console.log('Not a valid day!');
}
```

Equivalent `if/else` structure:
```js
if (day === 'monday') {
  console.log('Plan course structure');
  console.log('Go to coding meetup');
} else if (day === 'tuesday') {
  console.log('Prepare theory videos');
} else if (day === 'wednesday' || day === 'thursday') {
  console.log('Write code examples');
} else if (day === 'friday') {
  console.log('Record videos');
} else if (day === 'saturday' || day === 'sunday') {
  console.log('Enjoy the weekend :D');
} else {
  console.log('Not a valid day!');
}
```

`switch` can improve readability when checking a single value against many cases.

---

## Lecture 21: Statements and Expressions

- Expression: a piece of code that produces a value (e.g., `3 + 4`, `1991`, `true && false && !false`)
- Statement: a larger piece of code that performs an action but doesn't produce a value by itself (e.g., `if` blocks)

Example:
```js
if (23 > 10) {
  const str = '23 is bigger!';
}
```

In template literals, only expressions can be inserted:
```js
console.log(`I'm ${2037 - 1991} years old`); // works (expression)
// console.log(`I'm ${if (age > 18) { 'an adult' }}`); // ERROR (statement)
```

---

## Lecture 22: The Conditional (Ternary) Operator

Ternary operator for concise conditionals:
```js
const age = 23;

// Ternary
const drink = age >= 18 ? 'wine 🍷' : 'water 💧';
console.log(drink);

// Equivalent if/else
let drink2;
if (age >= 18) {
  drink2 = 'wine 🍷';
} else {
  drink2 = 'water 💧';
}
console.log(drink2);

// Ternary inside template literal
console.log(`I like to drink ${age >= 18 ? 'wine 🍷' : 'water 💧'}`);
```

Useful for short decisions; use `if/else` for complex multi-line logic.

---

## Lecture 24: JavaScript Releases: ES5, ES6+, and ESNext

JavaScript evolution:
- ES5 (2009): long-time standard
- ES6 / ES2015 (2015): major update introducing:
  - let / const
  - Arrow functions
  - Template literals
  - Classes
  - Destructuring
  - and more
- ES2016–ES2022: annual smaller releases adding new features

Modern browsers auto-update to support new features; for older browsers use tools like Babel to transpile to ES5.

The language evolves via a 4-stage TC39 proposal process before becoming standard.
