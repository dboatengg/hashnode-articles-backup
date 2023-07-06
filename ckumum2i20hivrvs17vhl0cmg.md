---
title: "10 Javascript Array Methods Every Developer Should Know"
seoTitle: "10 Javascript array methods to help simplify your code"
seoDescription: "This article elaborates on some of the most commonly used array methods that can help web developers simplify their code."
datePublished: Mon Oct 11 2021 16:07:05 GMT+0000 (Coordinated Universal Time)
cuid: ckumum2i20hivrvs17vhl0cmg
slug: 10-javascript-array-methods-every-developer-should-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1634634533867/XBwO4r0Hw.png
tags: javascript, array, array-methods

---

In JavaScript and programming in general, arrays serve as a collection of items and each of these items can be identified by an index (starting from 0).

Example of an array in JavaScript is shown below:

```javascript
const names = ['Diana', 'John', 'Mary']
```

In this article, we are going to learn how to use 10 common array methods that will help simplify your code.

**Let's get to work!**

#### 1\. Filter()

The `filter()` method works by returning an array out of a list of items that pass or satisfy a certain provided condition.

```javascript
const firstNames = ["John", "Bob", "Dana", "Cassandra"]
const passedTest = firstNames.filter(firstName => firstName.length === 4);
console.log(passedTest); //["John", "Dana"]
```

#### 2\. forEach()

The `forEach()` method works by executing a function on every item in an array.

```javascript
const ages = [5, 11, 13, 15];
ages.forEach(age => console.log(age * 2));
//10
//22
//26
//30
```

#### 3\. map()

The `map()` method executes a function on every item in an array and stores all of them in a new array.

```javascript
const ages = [5, 7, 13, 15];
const passedAges = ages.map(number => number * 2);
console.log(passedAges); // [10, 14, 26, 30]
```

#### 4\. every()

The `every()` method implements a function of array items to determine if all of them passed the test provided by the function and then returns a boolean value.

```javascript
const numbers = ["Jong", "Joe", "Ama", "Mouse"];
const all = numbers.every(number => number.length === 3);
console.log(all); //false
```

#### 5\. some()

The `some()` method also implements a function on array items to check if at least one of them passes the test provided by the function and then returns a boolean value.

```javascript
const numbers = ["Jong", "Joe", "Ama", "Mouse"];
const all = numbers.some(number => number.length === 5);
console.log(all); //true
```

#### 6\. includes()

The `includes()` method checks to determine if an array contains a particular item and then also returns a boolean value.

```javascript
const list = [2, 3, 4, 5, 6];

console.log(list.includes(6)); //true
console.log(list.includes("style")); //false
```

#### 7\. reduce()

The `reduce()` method as its name suggests, takes all the elements in an array and reduces them into a single value whether by adding, multiplying or any other possible way.

```javascript
const list = [2, 3, 4, 5, 6];

let sum = list.reduce((a, b) => a + b, 0);
console.log(sum); //20
```

#### 8\. sort()

The `sort()` method is used to arrange items in ascending or descending order. Note that the default arrangement order is ascending.

```javascript
let firstNames = ["John", "Peter", "Chris"];
firstNames.sort();
console.log(firstNames); //["Chris" , "John", "Peter"]
```

However, by default the `sort()` method perceives all items as strings. This makes it work perfectly fine with string values but not with numbers unless a compare function is provided as shown below.

```javascript
//ascending
let ages = [22, 13, 24, 5, 16];
let sortedAges = ages.sort((a, b) => a - b);
console.log(sortedAges); //[5, 13, 16, 22, 24]

//descending
let sortedAges = ages.sort((a, b) => b - a);
console.log(sortedAges); //[24, 22, 16, 13, 5]
```

#### 9\. find()

The `find()` method is used to get the value of the first element in an array that satisfies the provided condition.

```javascript
const numbers = [7, 14, 8, 128, 56];
const found = numbers.find(element => element > 10);

console.log(found); //14
```

#### 10\. findIndex()

The findIndex() method returns the index of the first element in an array that satisfies the provided condition. It returns -1 when no element passed the test.

```javascript
const numbers = [7, 14, 8, 128, 56];
const found = numbers.findIndex(element => element > 10);

console.log(found); //1
```

### CONCLUSION

Thanks for following along.

I hope you learned something useful. Kindly follow me on [Twitter](https://twitter.com/alege_dev) if you are interested in content like this.