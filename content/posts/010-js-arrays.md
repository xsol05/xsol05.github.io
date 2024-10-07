---
title: "🌸 JavaScript Array Methods"
date: 2023-05-23T14:43:53+12:00
draft: false
summary: "Nine of the most commonly used array methods" #displays underneath title in blog title card on homepage
description: "Nine of the most commonly used array methods" #displays underneath title in actual blog page
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
editPost:
    URL: "https://github.com/xsol05/xsol05.github.io/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

The really handy thing about JavaScript is that because of its [declarative](https://ui.dev/imperative-vs-declarative-programming) nature, it comes with various array methods that enable you to perform a myriad of operations without having to explicitly build them (eg using loops, counters etc).

In this post, I'll be covering some of the most commonly used methods using this data source as an example:

```javascript
// Array of objects
const bears = [
  {
    id: 'PB',
    name: 'Pink bear',
    qualities: ['hungry', 'cute', 'clingy'],
  },
  {
    id: 'YB',
    name: 'Yellow bear',
    qualities: ['cheeky', 'active', 'caring'],
  },
  {
    id: 'BB',
    name: 'Blue bear',
    qualities: ['caring', 'emotional', 'girly'],
  },
]

// Array of numbers
const ages = [1, 2, 3, 4, 5, 10, 13]

// Array of strings
const fruits = [
  'apple',
  'banana',
  'mango',
  'pineapple',
  'papaya',
  'durian',
  'mangosteen',
  'strawberry',
]
```

## 1. `map()`

**What:** Executes the provided function on every element in the array

**Returns:** A new array with the updated elements

```javascript
// Map objects
const mapBears = bears.map((bear) => bear.name)
console.log(mapBears) // ['Pink Bear', 'Yellow Bear', 'Blue Bear']

// Map numbers
const mapAges = ages.map((age) => age * 3)
console.log(mapAges) // [3, 6, 9, 12, 15, 30, 39]

// Map strings
const mapFruits = fruits.map((fruit) => fruit.length)
console.log(mapFruits) // [5, 6, 5, 9, 6, 6, 10, 10]
```

## 2. `forEach()`

**What:** Executes the provided function on every element in the array

**Returns:** `undefined` - it does not return anything! Instead, you need to `console.log` the result of executing the function on each element.

`map()` and `forEach()` are similar in that they both perform the same operation and both do not change the original source array, but they differ in that `map()` actually returns a new array with the results while `forEach()` does not return anything.

```javascript
// forEach objects
const forEachBears = bears.forEach((bear) => console.log(bear.id + 'Y2K'))
// PBY2K\n YBY2K\n BBY2K\n

// forEach numbers
const forEachAge = ages.forEach((age) => console.log(age * 2))
// 2\n 4\n 6\n 8\n 10\n 20\n 26

// forEach strings
const forEachFruit = fruits.forEach((fruit) => console.log(fruit + ' is tasty'))
// apple is tasty\n banana is tasty\n mango is tasty\n pineapple is tasty\n papaya is tasty\n durian is tasty\n mangosteen is tasty\n strawberry is tasty
```

## 3. `reduce()`

**What:** Executes a reducer function on every element in the array to flatten the array

**Returns:** A single output value ie it will do something to the elements in the array and magically return a single value

The `reduce()` function is a little complex so you can read more [here](https://www.programiz.com/javascript/library/array/reduce)

```javascript
// Reduce objects
const reduceBears = bears.reduce(
  (allQualities, bear) => [...allQualities, ...bear.qualities],
  []
)
console.log(reduceBears) // ["hungry", "cute", "clingy", "cheeky", "active", "caring", "caring", "emotional", "girly"]

// Reduce numbers
const reduceAges = ages.reduce((totalAge, age) => totalAge - age)
console.log(reduceAges) // -36

// Reduce strings
const reduceFruits = fruits.reduce((fruitString, fruit) => fruitString + fruit)
console.log(reduceFruits) // applebananamangopineapplepapayadurianmangosteenstrawberry
```

## 4. `filter()`

**What:** Checks every element in the array to see if it meets certain criteria

**Returns:** A new array with the elements that return truthy for the criteria. If no elements meet the criteria, an empty array will be returned.

```javascript
// Filter objects
const filterBears = bears.filter((bear) => bear.qualities.includes('caring'))
console.log(filterBears) // [{id: "YB", ...}, {id: "PB", ...}]

// Filter numbers
const filterAges = ages.filter((age) => age % 2 === 0)
console.log(filterAges) // [2, 4, 10]

// Filter strings
const filterFruits = fruits.filter((fruit) => fruit.includes('y'))
console.log(filterFruits) // ['papaya', 'strawberry']
```

## 5. `includes()`

**What:** Checks whether the array includes a certain value among its entries

**Returns:** `true` or `false`

```javascript
// Includes objects
const includesBears = bears.map((bear) => bear.name).includes('Blue bear')
console.log(includesBears) // true

// Includes numbers
const includesAges = ages.includes(15)
console.log(includesAges) // false

// Includes strings
const includesFruits = fruits.includes('kiwi')
console.log(includesFruits) // false
```

## 6. `some()`

**What:** Checks whether _at least one_ element in the array satisfies the provided testing function

**Returns:** `true` or `false`

```javascript
// Some objects
const someBears = bears.some((bear) => bear.name.includes('Yellow bear'))
console.log(someBears) // true

// Some numbers
const someAges = ages.some((age) => age % 2 === 0)
console.log(someAges) // true

// Some strings
const someFruits = fruits.some((fruit) => fruit.length === 6)
console.log(someFruits) // true
```

## 7. `every()`

**What:** Checks whether _all_ elements in the array satisfy the provided testing function

**Returns:** `true` or `false`

```javascript
// Every objects
const everyBears = bears.every((bear) => bear.qualities.includes('caring'))
console.log(everyBears) // false

// Every numbers
const everyAges = ages.every((age) => age % 2 === 0)
console.log(everyAges) // false

// Every strings
const everyFruits = fruits.every((fruit) => fruit.includes('a'))
console.log(everyFruits) // true
```

## 8. `find()`

**What:** Finds an element in the array that satisfies the provided testing function

**Returns:** The first element to satisfy the provided testing function. If no elements satisfy the testing function, `undefined` is returned.

```javascript
// Find objects
const findBears = bears.find((bear) => bear.name === 'Yellow bear')
console.log(findBears) // {id: "YB", ...}
console.log(findBears.id) // YB

// Find numbers
const findAges = ages.find((age) => age > 10)
console.log(findAges) // 13

// Find strings
const findFruits = fruits.find((fruit) => fruit.length > 5)
console.log(findFruits) // banana
```

## 9. `findIndex()`

**What:** Finds an element in the array that satisfies the provided testing function

**Returns:** The _index_ of the first element to satisfy the provided testing function. If no elements satisfy the testing function, `-1` is returned.

```javascript
// findIndex objects
const findIndexBears = bears.findIndex((bear) => bear.id === 'YB')
console.log(findIndexBears) // 1

// findIndex numbers
const findIndexAges = ages.findIndex((age) => age % 2 !== 0)
console.log(findIndexAges) // 0

// findIndex strings
const findIndexFruits = fruits.findIndex((fruit) => fruit.includes('s'))
console.log(findIndexFruits) // 6
```

## Summary

| Method    | What                                                                                       | Returns                                                                                                                                   |
| --------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| map       | Executes the provided function on every element in the array                               | A new array with the updated elements                                                                                                     |
| forEach   | Executes the provided function on every element in the array                               | `undefined`                                                                                                                               |
| reduce    | Executes a reducer function on every element in the array to flatten the array             | A single output value                                                                                                                     |
| filter    | Checks every element in the array to see if it meets certain criteria                      | A new array with the elements that return truthy for the criteria. If no elements meet the criteria, an empty array will be returned.     |
| includes  | Checks whether the array includes a certain value among its entries                        | `true` or `false`                                                                                                                         |
| some      | Checks whether _at least one_ element in the array satisfies the provided testing function | `true` or `false`                                                                                                                         |
| every     | Checks whether _all_ elements in the array satisfy the provided testing function           | `true` or `false`                                                                                                                         |
| find      | Finds an element in the array that satisfies the provided testing function                 | The first element to satisfy the provided testing function. If no elements satisfy the testing function, `undefined` is returned.         |
| findIndex | Finds an element in the array that satisfies the provided testing function                 | The _index_ of the first element to satisfy the provided testing function. If no elements satisfy the testing function, `-1` is returned. |
