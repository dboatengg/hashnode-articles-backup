---
title: "Understanding Constructor Functions in JavaScript"
datePublished: Sun Aug 14 2022 10:01:00 GMT+0000 (Coordinated Universal Time)
cuid: cl6t5psjj0dv2fdnve6r2h64w
slug: understanding-constructor-functions-in-javascript
canonical: https://hackmd.io/@dboatengx/HycQXfqaq
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1660487624477/1t1phs3YH.png
tags: programming-blogs, css, javascript, html5

---

Constructor functions are one of the most valuable pieces of JavaScript, and understanding them is crucial to understanding the JavaScript language.

With the help of examples, this article explores JavaScript constructor functions in detail.

Let’s get right into it!

## What is a constructor function?

A constructor function is like a regular JavaScript function that acts as a blueprint for creating objects.

Let's say you're a home builder and want to build a new neighbourhood. You create a blueprint for a house and hire a construction team to build the house. You give them the blueprint and say, "Make twenty houses like this." So they build each house (object) based on the blueprint (constructor function) you've given them. In the end, twenty houses will be built based on the blueprint.

The significant advantage here is that once you create a blueprint, you can make 20, 500, 1000, or more similar houses with different characteristics.

![](https://i.imgur.com/FreVcNN.png align="left")

Like a blueprint for building houses, a constructor function allows you to define an object's structure once and use it as a template to create multiple similar objects.

Constructor functions act as initializers of objects. They are templates with which you can create multiple objects having the same properties and methods but different values.

### Example: A Social Media Website

Assume you want to develop a social media website; the time has come to decide what data you will collect from your users. You will need a way to receive user data in your code by creating a new object for every user that registers on the site.

To gain a better understanding of how the social media website would receive user data, let's consider the following presumptions:

* All users will be required to provide the same information when registering on the site; hence, objects created to receive various user data will have similar properties.
    
* Let's say we look forward to receiving thousands of users data on the site. Hence, we must create multiple objects to be able to receive the data for every user.
    

## How to Create Constructor Functions

We create constructor functions similar to how we create regular JavaScript functions.

The following is an example of a constructor function created to receive user data on our social media site. The function accepts three arguments.

* FirstName
    
* Lastname
    
* Age
    

You can pass as many arguments or no arguments, depending on the amount of data that you want to receive.

```javascript
function User(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
}
```

In the above code,`User` is the constructor function, and its purpose is to create multiple new objects to represent different users who register on the social media site.

Again, considering the `User` constructor function, a couple of things may stick out right away:

* The name of the constructor function starts with a capital letter. This is not necessarily required for the constructor function to work properly, but it is a widely accepted convention and should always be followed. It sometimes aids in distinguishing constructor functions from regular JavaScript functions.
    
* Also, the `this` keyword is quite common.
    

### What is "this" keyword?

In JavaScript, `this` keyword refers to an object. But to which object the `this` keyword will refer to depends on where it's being used.

For example:

* Inside an object `this` keyword will refer to that object.
    
* In the global context, `this` keyword will refer to the global (window) object.
    
* In a constructor function or class, `this` keyword will represent an object instance of the constructor function.
    

When creating constructor functions, we don't want to assign a permanent variable name for objects that will be created. So we use the `this` keyword to dynamically refer to whichever object is being created at any particular instance.

In other words, the `this` keyword allows you to add properties and methods to any object that gets instantiated with a constructor function.

### Calling Constructor Functions

To use a constructor function you need to invoke it with the `new` keyword, and then pass in the actual data you want to receive.

Kindly consider the following code:

```javascript
let user1 = new User("John", "Doe", 23);
```

Here, we are creating a specific instance (object) of the `User` constructor with the following data:

* Firstname as 'John'
    
* Lastname as 'Doe'
    
* Age as 23.
    

Notice that there is a `new` keyword before the `User` constructor function call? It is actually an operator and it is responsible for all the magic that happens when creating new objects from constructor functions.

When you invoke a constructor function with the `new` keyword, it does the following things:

* It creates a new empty object.
    
* It sets the prototype of the newly created object and links it to the constructor function's prototype property.
    
* It sets the `this` keyword of the constructor function to point to the newly created object.
    
* It makes the constructor function return the newly created object if it does not return anything.
    

In the following example, the `newClone` function shows what the `new` operator does behind the scenes.

```javascript

//This function mimics the new operator
function newClone(ConstFunction, ...theArgs) {
  
    //1. Creates a new empty object
  let obj = {};
 
  //2. Sets prototype of newly created object and links to it to prototype  property of constructor function.
  Object.setPrototypeOf(obj, ConstFunction.prototype)
 
  //3. calls the ConstFunction using `call` and sets the new object (obj) as its 'this' keyword.
  let ret = ConstFunction.call(obj, ...theArgs)
  
  //4. if it returns Object then returns it as it is
  if (ret == Object) return ret
 
  //else return obj
  return obj;
}
 
//Person created using the NewClone
const userClone  = newClone(User, 'John', 'Doe', 23)
console.log(userClone );
 
//Person created using the new operator
const user1 = new User('John', 'Doe', 23)
console.log(user1);
```

If you compare the results of both objects (`user1` and `userClone`), you will find that they produce the same output as shown below:

```javascript
{
"firstName": "John",
"lastName": "Doe"
 age: 23
}
```

### Adding Methods to Constructors

When working with constructor functions, you are not limited to adding just properties to objects; you can also add methods.

There are two ways of adding methods to constructor functions.

* Declaring method inside constructor function
    
* Adding method to constructor via prototypes
    

The following code adds a method to the `User` constructor by declaring it inside the constructor function.

```javascript
function User(firstName, lastName, age){
    
    // defined properties
    
    //Adding method
    this.speak = function() {
        console.log("Hello! My name is " + this.firstName + " " + this.lastName + " and I'm " + this.age)+" years old.";
    }
}
```

The other approach to adding methods is through prototypes. A prototype is a type of inheritance in JavaScript. We use it when we want to add a method or property to a constructor after it has been defined. Once added, the properties or methods become available to all object instances of that constructor.

Let's extend the `User` constructor with another method to print out a user's full name.

```javascript
function User(firstName, lastName, age){
    
    // defined properties  
}

User.prototype.getFullName = function() {
    console.log(this.firstName + " " + this.lastName);
}
 
user1 = new User("John", "Doe", 23);
user1.getFullName() // John Doe
```

As seen from the above code, we just used the `prototype` keyword immediately after the name of the constructor to utilize the prototype functionality. The custom method `getFullName()` is now availabe to all object instances of the `User` constructor.

## Types of Constructor Functions in JavaScript

There are mainly two types of constructor functions in JavaScript.

### 1\. User-defined Constructor Functions

The constructor function discussed so far in this article is considered as a user-defined constructor. User-defined constructors are constructor functions declared and defined by developers to be used throughout an application.

### 2\. Built-in Constructor Functions

JavaScript has built-in constructor functions for every primitive data type, like String, Number, Boolean, Object, etc.

Kindly consider some of the built-in constructor functions in JavaScript below:

```javascript
const str = new String("string") //A new string object.
const num = new Number(56) //A a number object.
const bool = new Boolean(true) //A new boolean object.
const arr = new Array([23,32]) //A new JavaScript array.
const obj = new Object({"name":"Joe"}) //A new JavaScript object.

//Display types
console.log(typeof str) //object
console.log(typeof num) //object
console.log(typeof bool) //object
console.log(typeof arr) //object
console.log(typeof obj) //object
```

After running the codes above, we can see that each one returns an object because all constructors in JavaScript return an object.

This confirms that JavaScript has object versions of its primitive data types. However, using these objects in your code is not recommended because primitive data type values are much faster.

## JavaScript Object Prototype

As shown below, JavaScript is a dynamic language, and you can attach new properties to an object at any instance.

```javascript
function Person() {
    this.name = 'John Doe';
    this.occupation = 'Developer';
}

const person1 = new Person();
person1.age = 34;
console.log(person1.age); // 34

const person2 = new Person();
console.log(person2.age); // undefined
```

As you can see in the above example code, the `age` property is only available on `person1` object and not `person2`. This is because `age` was defined only on `person1`.

So what do we do if we want to add new properties to a constructor function after it has been defined and have them available to all object instances?

The answer is **Prototype**.

In JavaScript, every function has a property called the **prototype**. This property exists as an empty object in the function and remains dormant throughout the life of that function. It only becomes active and quite helpful if that function is used as a constructor.

![](https://i.imgur.com/husaE8m.png align="left")

The prototype property of a constructor function acts as the prototype for all object instances created from that function.

Kindly run the following code and consider its result:

```javascript
function Person() {
    this.name = 'John';
    this.occupation = 'Developer';
}

// Add property to prototype property of Person constructor
Person.prototype.age = 34;

const person1 = new Person();
console.log(person1.age); // 34

const person2 = new Student()
console.log(person2.age); // 34
```

From the results above, you can see that all the two object instances created from the `Person` constructor now have access to the `age` property, which sits in the prototype property of the Person constructor.

![](https://i.imgur.com/2RFwR2n.png align="left")

## Constructors Vs. Object literal

You can create objects in JavaScript using the following.

* Object literal notation
    
* Constructor notation
    

Let's look at some examples of creating objects with the object literal notation to see how the constructor notation can help speed up the process of creating objects.

#### Example: Storing student information

Let's say a school wants to keep track of all students. We'll create an object for each student using the object literal notation:

```javascript
const student1 = {
    firstName: "Jermaine",
    lastName: "Cole",
    age: 32
}
```

Now we’ll create another:

```javascript
const student2 = {
    firstName: "Kendrick",
    lastName: "Lamar",
    age: 24
}
```

And another:

```javascript
const student3 = {
    firstName: "Jake",
    lastName: "Williams",
    age: 36
}
```

As seen from the above code, creating multiple "student" objects with the object literal notation involves repeatedly typing `firstName`, `lastName`, and `age` properties in every object declaration, which is very ineffective.

However, there is a much faster way to create "student" objects. Instead of using the object literal notation to create each student object manually, you can use the constructor notation to define a function as a template to create any number of "student" objects you want.

```javascript
function Student(firstName,lastName,age) = {
    this.firstName = firstName
    this.lastName = lastName
    this.age = age
}

const student1 = new Student("Jermaine", "Cole", 23);
const student2 = new Student("Kendrick", "Lamar", 32);
const student3 = new Student("Jake", "Williams", 36);
```

As you can see, with the constructor notation, you can define a function once and then use it to create multiple student objects.

Deciding whether to use the object literal or constructor notation essentially boils down to whether you need multiple instances of an object. An object defined with the constructor notation lets you have multiple instances of that object. In contrast, an object defined with the object literal notation exists as a single object with properties and methods.

## Constructor Vs. Classes

Compared to other object-oriented programming languages, JavaScript is unique. It operates based on constructors and prototypes rather than classes, and for a long time, classes did not even exist in JavaScript.

JavaScript classes were introduced in ECMAScript 2015. However, they did not introduce any extra functionality to the JavaScript language. They simply work as syntactic sugar (making code easier to read and write) over the already existing constructor functions.

Classes in JavaScript and constructor functions are closely related. A class is used to create objects just like a constructor function but uses a different syntax.

When creating a JavaScript class, you use the `class` keyword.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
}
// creating an object
const person1 = new Person('John');
const person2 = new Person('Jack');
```

Inside a class declaration, you can add a method called `constructor()` that will work exactly as a constructor function. All the properties in a class are assigned in this constructor function.

The declaration of the constructor method, `constructor()`, inside a class proves that classes in JavaScript operates based on constructor functions behind the scenes.

## Wrapping Up

This article provided a comprehensive explanation of JavaScript constructor functions. There is more to learn about constructors, but for now, you should know enough to start using them in your code.

I do hope you followed through to this point. If you did, you are appreciated. It has been a long discussion, and I hope you learned something new.

Kindly follow me on Twitter [@alege\_dev](https://twitter.com/alege_dev) for updates on future posts.

Happy Coding!