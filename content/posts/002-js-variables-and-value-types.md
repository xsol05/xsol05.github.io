---
title: "🧶 JavaScript Variables and Value Types"
date: 2022-06-27T16:15:27+12:00
draft: true
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

- Used in pre-ES6 versions of JS and is no longer used currently
- It is global scoped or function scoped.

### `let`

- Preferred way to declare a variable when it can be reassigned
- It is [block scoped](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/) meaning it can't be accessed outside the block it was defined in

```javascript
let hobby = "reading";
console.log(hobby); // reading
hobby = "sleeping";
console.log(hobby); // sleeping
```

### `const`

- Preferred way to declare a variable with a constant value
- It is [block scoped](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/) meaning it can't be accessed outside the block it was defined in

```javascript
const happy = true;
console.log(happy); // true
happy = false; // Throws TypeError as it cannot be reassigned
const happy = false; // Throws SyntaxError as it cannot be redeclared
```

While const variables cannot be reassigned or redeclared, it does not mean that the value which `const` points to is immutable.

```javascript
const poop = {
  scoop: true,
};
poop.scoop = false;
console.log(poop); // { scoop: false }
```

Since a variable, regardless of its keyword, simply points to a value, this means that the behaviour of the value being changed depends on the **type** of value being manipulated.

## Value Types

In JavaScript, there are 8 different types of values, and only Objects are mutable.

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

#### 1. String

- Can be represented with `''`, `""`, or ` `` `

#### 2. Boolean

- Only `true` or `false`
- Be careful with the operator signs

#### 3. Number

- JS uses numbers with limited precision. Their decimal part offers more precision closer to `0`, and less precision further away from it.
- Floating point maths includes a few special numbers - `Nan`, `Infinity`, `-Infinity`, and `-0`.
- `typeof(NaN)` is a number because `NaN` is a numeric value. It’s called “Not a Number” because it represents the *idea* of an “invalid” number.

```javascript
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

#### 4. BigInt

- Regular numbers can’t represent large integers with precision, so BigInts fill that gap
- They usually have `n` at the end
- They have arbitrary precision, meaning there is an infinite number of BigInts - one for each integer in Maths

#### 5. Symbol

-

#### 6. Null

- An intentionally missing value
- It is incorrectly described as an object when you do `console.log(typeof(null))` but this is a historical JS bug

#### 7. Undefined

- An unintentionally missing value

### Non-primitive (mutable) values

Non-primitive values are mutable, meaning they can be changed.

#### 8. Object

## Quiz

Here's a quiz to check for your understanding. Answers included in comments (but don't cheat!) All credits go to [Ben Coullie](https://github.com/bencoullie) for this!

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
// 9. { yass: true }
```

---

**References**

- Dan Abramov's [JustJavaScript](https://justjavascript.com/) course
- https://www.geeksforgeeks.org/difference-between-var-let-and-const-keywords-in-javascript/
