---
title: "JavaScript Local Storage Explained!"
seoDescription: "In this article, you will learn about the theoretical and practical applications of LocalStorage in JavaScript."
datePublished: Sat Sep 24 2022 09:41:13 GMT+0000 (Coordinated Universal Time)
cuid: cl8fq2acm036wqgnv5drgefb1
slug: javascript-local-storage-explained
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1663993976441/Yucp6FYYW.png
tags: javascript, web-development, localstorage

---

In the early days of the internet, you needed a server to store data. But nowadays, through LocalStorage, you can store data on browsers without using a back-end server.

In this article, you will learn about the theoretical and practical applications of Local Storage in JavaScript.

## Let's talk about web storage

Web storage is one of the great features of HTML5 that allows web applications to store data locally within a user's browser.

The two most common forms of web storage are Local Storage and Session Storage. The key difference between the two is that data saved in Local Storage never leaves the browser and remains there until you explicitly remove it. While data stored in Session Storage is removed once a browser window is closed.

## What is Local Storage?

As mentioned earlier, Local Storage allows web applications to store data locally within a user's browser with no expiration date. Here, stored data will remain available even when you close a browser tab/window.

Note that the data stored in Local Storage is only preserved on a user's browser on the device they used to access a site. Hence, users cannot access the stored data if they revisit the same site later with a different browser or on another device.

## LocalStorage Use Cases

The following presents some everyday use cases of Local Storage.

### 1\. Store Partially Submitted Form Data

If a user fills out a long form online, Local Storage can be a helpful resource for storing user inputs. Even when the internet gets disconnected between filling out the form and submitting it, users won't lose their input. They can continue from where they left off when they are back online.

### 2\. Caching

Caching refers to storing data such as login details on a user's device so that future requests for that data can be served faster. You can use localStorage to cache a whole website so that users can still have access to the site even when they are offline.

### 3\. Database for basic applications

As mentioned earlier, data storage was initially only possible by using a database through the backend. But now, with Local Storage, you can store data on the client side without needing a database. Hence Local Storage can sometimes serve as a "little" database for basic applications.

## How to Access LocalStorage

Accessing LocalStorage is pretty simple and takes only a few steps:

1. Go to any website or web application and open the browser console by pressing <kbd>F12</kbd> on the keyboard.
    
2. Click on the *Application* tab, and in the menu on the left, you will see "*Local Storage*" under the *Storage* tab as shown below.
    

![](https://i.imgur.com/xBVUgMh.png align="left")

1. Click on the `LocalStorage` dropdown and further click on the dropdown item.
    
    ![](https://i.imgur.com/ahwI9UI.png align="left")
    

As can be seen, there are two columns, `key`, and `value`. This is where LocalStorage stores every data you save to it.

## How to Use Local Storage

You can use the following methods to manage data in LocalStorage.

| Method | Description |
| --- | --- |
| `setItem()` | To store data in LocalStorage. |
| `getItem()` | To get or retrieve the data from LocalStorage |
| `removeItem()` | To delete data from LocalStorage using a key |
| `key()` | To retrieve data from LocalStorage at a specified index |

### setItem( )

This method is used to store data in LocalStorage. It accepts a key as its first argument and then a value as the second argument.

Let's add data to Local Storage using the following code.

```javascript
localStorage.setItem("name", "Mandy");
// Here, `name` is the key and `Mandy` is the value
```

As mentioned earlier, LocalStorage stores data as strings, so if you want to save data such as objects and arrays, you need to convert them to strings using the `JSON.stringify()` method.

Let's see how this works!

```javascript
//Storing objects in LocalStorage
const user = {
  name: "Mandy",
  age: 23,
};

localStorage.setItem("user-info", JSON.stringify(user));

//Storing arrays/lists in LocalStorage
const names = ["John", "Jake", "Vanessa"];
localStorage.setItem("names", JSON.stringify(names));
```

### getItem()

Use the `getItem()` method to retrieve data from LocalStorage. This method accepts a single parameter, which is the `key` used when saving data.

For example, to retrieve data such as the above `user` object, you will use the following statement:

```javascript
localStorage.getItem("user-info");
```

The above code will return a `JSON` string as shown below:

```javascript
"{name:"Mandy", age:"23"}"
```

You should then convert it to an object using the `JSON.parse()` method.

```javascript
JSON.parse(localStorage.getItem('user-info'));
```

### removeItem()

Use the `removeItem()` method to remove data from LocalStorage. This method accepts a `key` as a parameter.

For example, you will use the following statement to delete the `user` object from LocalStorage.

```javascript
localStorage.removeItem("user-info");
```

### key()

Use `key(index)` method to retrieve data from LocalStorage, where `index` represents the `nth` data you want to retrieve.

```javascript
localStorage.key(2);
```

### clear()

Use the `clear()` method to clear out or remove all data from LocalStorage at a particular instance.

```javascript
localStorage.clear()
```

## Project

Now that you've learned about the main methods used to manage data in Local Storage, let’s get our hands dirty by creating a web application where users can:

* Save data to LocalStorage
    
* Retrieve the data
    
* Remove/Delete the data using a `key`
    
* And also clear out all data from LocalStorage.
    

Let's start by creating a new folder and opening it in a code editor. Next, create three files, `index.html` , `style.css` and `main.js`.

### Let’s Code!

The `index.html` file will contain the HTML markup for the web application. The HTML code below comprises a form having various input fields with buttons.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Local Storage</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="form">
      <form id="userForm">
        <h1>LocalStorage Application</h1>
        <label for="userName">User</label>
        <input
          type="text"
          id="userName"
          placeholder="Enter user name"
          required
          autofocus
        /><br />
        <label for="age">Age</label>
        <input
          type="number"
          id="age"
          placeholder="Enter user age"
          required
        /><br />
        <label for="key">Key</label>
        <input type="text" id="key" placeholder="Enter key" required /><br />
        <button type="submit">Save user</button>
      </form>
      <br />
      <label for="key">Enter Key to retrieve user</label>
      <input
        type="text"
        id="retrieveKey"
        placeholder="Enter key to access user"
        required
      /><br />
      <button id="retrieveButton">Retrieve user</button>
      <br />
      <div id="userData"></div>
      <br />
      <label for="removeKey">Enter Key to delete user</label>
      <input
        type="text"
        id="removeKey"
        placeholder="removeKey"
        required
      /><br />
      <button id="removeButton">Delete user</button>
      <br />
      <button id="clearButton">Delete all users</button>
    </div>
    <script type="text/javascript" src="main.js"></script>
  </body>
</html>
```

Here's the CSS code.

```css
/* base styles  */
html {
  font-size: 67.5%;
}
body {
  font-size: 1.6rem;
  padding: 0;
  margin: 0;
}

/* form   */
#form {
  margin-left: 2rem;
}
```

Here’s the `main.js` file containing all the functions to store, retrieve, and delete data from LocalStorage.

```javascript
//store user data in the localStorage
function store() {
  var userName = document.getElementById("userName").value;
  var age = document.getElementById("age").value;
  var key = document.getElementById("key").value;

  const user = {
    userName,
    age,
  };

  //convert user object to string and save it
  localStorage.setItem(key, JSON.stringify(user));
}

//retrieve user data from localStorage
function retrieveUserData() {
  let key = document.getElementById("retrieveKey").value;
  console.log("retrive records");
  let userData = localStorage.getItem(key); //searches for the key in localStorage
  let paragraph = document.createElement("p");
  let info = document.createTextNode(userData);
  paragraph.appendChild(info);
  let element = document.getElementById("userData");
  element.appendChild(paragraph);
  retrieveKey.value = "";
}

//delete user data from localStorage
function removeUserData() {
  var removeKey = document.getElementById("removeKey").value;
  localStorage.removeItem(removeKey);
  removeKey.value = "";
}

//delete all user data from localStorage
function deleteAllUserData() {
  localStorage.clear();
}

//ensures the page is fully loaded before functions can be executed.
window.onload = function () {
  document.getElementById("userForm").onsubmit = store;
  document.getElementById("clearButton").onclick = deleteAllUserData;
  document.getElementById("removeButton").onclick = removeUserData;
  document.getElementById("retrieveButton").onclick = retrieveUserData;
};
```

## Results

The following video shows how the final result of the project works:

%[https://youtu.be/VFZw9N_12-s] 

## Some Essential Points About LocalStorage

* Local storage has no data protection and it is therefore not secure to store sensitive data as they can be accessed by anyone.
    
* Local storage can only store a maximum of 5MB of data on the browser.
    

## Conclusion

I encourage you to practice and experiment with Local Storage by using it in your applications. Get used to saving, retrieving, and removing data from it.

Thanks for reading!

I hope this has been a worthwhile read.

Kindly share this article and follow me on [Twitter @dboatengx](https://twitter.com/alege_dev) for updates on future posts.