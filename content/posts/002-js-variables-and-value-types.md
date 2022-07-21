---
title: "🍰 JavaScript Variables and Value Types"
date: 2022-07-21T18:28:25+12:00
draft: false
summary: "The basics aren't very basic"
description: "The basics aren't very basic"
tags: ["JavaScript"]
author: "Magdeline Huang"
showToc: true
TocOpen: false
hidemeta: false
comments: true
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

## Variables

Variables point to values and associate them with a name.

There are three keywords to define variables:

### `var`

- It is used in pre-ES6 versions of JS and is **no longer used currently**
- It is global scoped or function scoped

### `let`

- It is the preferred way to declare a variable when it can be **reassigned**
- It is [block scoped](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/) meaning it can't be accessed outside the block it was defined in
- You can declare a `let` variable without assigning it to a value

```javascript
let hobby;
console.log(hobby); // undefined
hobby = "reading";
console.log(hobby); // reading
hobby = "sleeping";
console.log(hobby); // sleeping
```

### `const`

- It is the preferred way to declare a variable with a **constant value**
- It is [block scoped](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/) meaning it can't be accessed outside the block it was defined in
- You cannot declare a `const` variable without assigning it to a value

```javascript
const happy; // Throws SyntaxErrror as it is not initialised
const happy = true;
console.log(happy); // true
happy = false; // Throws TypeError as it cannot be reassigned
const happy = false; // Throws SyntaxError as it cannot be redeclared
```

While `const` variables cannot be reassigned or redeclared, it does not mean that the value which the `const` variable points to is immutable (cannot be changed). In this example, we have a `const` variable called `emotion` which points to an object. Objects are non-primitive and mutable.

```javascript
const emotion = {
  happy: true,
};
emotion.happy = false;
console.log(emotion); // { happy: false }
```

Since a variable, regardless of its keyword, simply points to a value, this means that the behaviour of the value being changed depends on the **type** of value being manipulated.

## Value Types

In JavaScript, there are 8 different types of values, and only Objects are mutable.

You can check the type of a variable by using the `typeof()` function:

```javascript
let hobby = "reading";
typeof hobby; // 'string'

const happy = true;
typeof happy; // 'boolean'

const emotion = {
  happy: true,
};
typeof emotion; // 'object'
```

<!-- | Primitive (immutable) | Non-primitive (mutable)               |
| --------------------- | ------------------------------------- |
| String                | Object (including array and function) |
| Boolean               |                                       |
| Number                |                                       |
| BigInt                |                                       |
| Symbol                |                                       |
| Null                  |                                       |
| Undefined             |                                       | -->

### Primitive (immutable) values

Primitive values are immutable, meaning they cannot be changed. Each value is unique and independent.

#### 1. Undefined

- There is only one value of this type -- `undefined`
- It is an **unintentionally** missing value eg if you declare a variable but don't assign it to something, it will point to `undefined`
- It will throw an error if you try to access its properties

```javascript
let book;
console.log(book); // undefined
console.log(book.author); // Throws TypeError as it cannot read properties of undefined
```

#### 2. Null

- There is only one value of this type -- `null`
- It is an **intentionally** missing value. This is the main difference between `undefined` and `null`. It distinguishes a coding mistake (which might result in `undefined`) from valid missing data (expressed as `null`).
- It will throw an error if you try to access its properties
- It is incorrectly described as an Object when you do `console.log(typeof(null))` but this is a [historical JS bug](https://2ality.com/2013/10/typeof-null.html)

```javascript
let book = null;
console.log(book); // null
console.log(book.author); // Throws TypeError as it cannot read properties of null
console.log(typeof book); // object (notice how it is not null as it should be 🤦🏻‍♀️)
```

#### 3. Boolean

- There are two values of this type - `true` and `false`
- It is used to perform logical operations

```javascript
let isRaining = true;
let isSunny = !isRaining; // false
let isRainbow = isRaining && isSunny; // false
let isHappy = isRaining || isSunny; // true
```

#### 4. Number

- JS uses numbers with limited precision. Their decimal part offers more precision closer to `0`, and less precision further away from it. Hence in [floating-point maths](https://floating-point-gui.de/formats/fp/), there are only 18 quintillion numbers unlike how there is an infinite set of numbers in real maths.
- `typeof(NaN)` is a number because `NaN` is a numeric value. It’s called “Not a Number” because it represents the *idea* of an “invalid” number.
- Floating point maths includes a few special numbers - `Nan`, `Infinity`, `-Infinity`, and `-0`

```javascript
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

#### 5. BigInt

- Regular numbers can’t represent large integers with precision, so BigInts fill that gap
- It has arbitrary precision, meaning there is an infinite number of BigInts - one for each integer in maths
- It usually has `n` at the end
- It is typically used in financial calculations where precision is important

```javascript
let alot = 9007199254740991n; // n at the end makes it a BigInt!
console.log(alot + 1n); // 9007199254740992n
console.log(alot + 2n); // 9007199254740993n
console.log(alot + 3n); // 9007199254740994n
console.log(alot + 4n); // 9007199254740995n
console.log(alot + 5n); // 9007199254740996n
```

#### 6. String

- It can be represented with single quotes `''`, double quotes `""`, or backticks ` `` `
- It has several built-in properties

```javascript
let country = "New Zealand";
console.log(country.length); // 11
console.log(country.toUpperCase()); // NEW ZEALAND
console.log(country[4]); // Z
```

#### 7. Symbol

- It is a built-in object whose constructor returns a `symbol` primitive — also called a Symbol value or just a Symbol — that's guaranteed to be unique
- It is similar to door keys whereby it lets you hide some information in an object and control which parts of the code can access it
- It is rarely used

### Non-primitive (mutable) values

Non-primitive values are mutable, meaning they can be changed.

#### 8. Object

- It can be used to store keyed collections of various data
- It includes arrays, dates, RegExps, functions, and other non-primitive values
- Its properties can be accessed with `.` (dot notation) or `[]` (bracket notation)

```javascript
let book = {
  title: "Sweet Bean Paste",
  author: "Durian Sukegawa",
};
console.log(book.title); // "Sweet Bean Paste"
console.log(book["author"]); // "Durian Sukegawa"
book.title = "Pinza no Shima";
console.log(book.title); // "Pinza no Shima"
```

## Quiz

Here's a quiz to check for your understanding. Answers included in the comments (but don't cheat!) All credits go to [Ben Coullie](https://github.com/bencoullie) for this!

```javascript
1;
let q = "yass";
q = "nooo";
console.log(q);

2;
const w = "yass";
w = "nooo";
console.log(w);

3;
let e = "yass";
e[0] = "n";
console.log(e);

4;
const r = "yass";
r[0] = "n";
console.log(r);

5;
let t = { yass: true };
t.yass = false;
console.log(t);

6;
const t = { yass: true };
t.yass = false;
console.log(t);

7;
let y = [1];
y[0] = 2;
console.log(y);

8;
const u = [1];
u[0] = 2;
console.log(u);

9;
// Curveball
let i = { yass: true };
Object.freeze(i);
i.yass = false;
console.log(i);

// Answers:
// 1. 'nooo' (a let variable can be reassigned a value)
// 2. 'yass' (a const variable cannot be reassigned a value)
// 3. 'yass' (a string value is immutable)
// 4. 'yass' (a string value is immutable)
// 5. { yass: false } (This let variable points to an object. An object is mutable)
// 6. { yass: false } (This const variable points to an object. An object is mutable)
// 7. [2] (This let variable points to an object. An object is mutable)
// 8. [2] (This const variable points to an object. An object is mutable)
// 9. { yass: true } (Object.freeze prevents an object from being changed)
```

---

**References**

- Dan Abramov's [JustJavaScript](https://justjavascript.com/) course (highly recommended!)
- https://www.geeksforgeeks.org/difference-between-var-let-and-const-keywords-in-javascript/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol
