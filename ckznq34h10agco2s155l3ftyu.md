---
title: "Build A Real-time Changing Digital Clock Using HTML, CSS & JavaScript"
seoTitle: "Build A Real-time Changing Digital Clock Using HTML, CSS & JavaScript"
seoDescription: "HTML, CSS and JavaScript are known for building dynamic web elements. In this tutorial, we discuss how to build a simple real-time changing digital clock."
datePublished: Tue Feb 15 2022 06:06:41 GMT+0000 (Coordinated Universal Time)
cuid: ckznq34h10agco2s155l3ftyu
slug: build-a-real-time-changing-digital-clock-using-html-css-and-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1644888568299/HK1uDPJib.png
tags: css, javascript, codepen, html5

---

HTML, CSS, and JavaScript are used to create attractive, dynamic web components and one useful component we can build is a digital clock.

In this short tutorial, we'll go through how to build a basic real-time changing digital clock that displays the current time and date.

## How to Build a Digital Clock using HTML, CSS and JS
We would start by establishing the HTML markup for our project.

We would create a folder called `clock`. Inside this folder, we would create three files: `index.html`, `styles.css`, and `main.js`. We would then link the two other files into our `index.html` file, as seen below:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <script src="main.js" type="text/javascript"></script>
</body>
</html>
``` 
Alternatively, you can copy the code above into your `index.html` file, or get the code for this project from [Codepen](https://codepen.io/Boatengg/pen/JjOEXry)


## HTML Markup for our Clock
The HTML markup for our digital clock is pretty simple. It consists of an `h1` element with an id of `date-time` wrapped around by a `div` element also with an id of `clock`.

```
<div id="clock">
  <h1 id="date-time"></h1>
</div>
``` 
Nothing would display for our digital clock unless we bring in some JavaScript.

# Adding JavaScript to our Clock
We're going to write some JavaScript at this point to bring our digital clock to life.

Let's go to our main.js file and paste the following code in there.
>Please read the comments in the code for further clarification.

```
window.addEventListener("load", () => {
  clock();
  function clock() {
    const today = new Date();

    // get time components
    const hours = today.getHours();
    const minutes = today.getMinutes();
    const seconds = today.getSeconds();

    //add '0' to hour, minute & second when they are less 10
    const hour = hours < 10 ? "0" + hours : hours;
    const minute = minutes < 10 ? "0" + minutes : minutes;
    const second = seconds < 10 ? "0" + seconds : seconds;

    //make clock a 12-hour time clock
    const hourTime = hour > 12 ? hour - 12 : hour;

    // if (hour === 0) {
    //   hour = 12;
    // }
    //assigning 'am' or 'pm' to indicate time of the day
    const ampm = hour < 12 ? "AM" : "PM";

    // get date components
    const month = today.getMonth();
    const year = today.getFullYear();
    const day = today.getDate();

    //declaring a list of all months in  a year
    const monthList = [
      "January",
      "February",
      "March",
      "April",
      "May",
      "June",
      "July",
      "August",
      "September",
      "October",
      "November",
      "December"
    ];

    //get current date and time
    const date = monthList[month] + " " + day + ", " + year;
    const time = hourTime + ":" + minute + ":" + second + ampm;

    //combine current date and time
    const dateTime = date + " - " + time;

    //print current date and time to the DOM
    document.getElementById("date-time").innerHTML = dateTime;
    setTimeout(clock, 1000);
  }
});
``` 

## Styling Our Clock with CSS
Let's add some CSS styles to our app to make it more attractive.

```
/*font family from google fonts*/
@import url("https://fonts.googleapis.com/css2?family=Oswald:wght@300;400&display=swap");

html {
  font-size: 62.5%; /*62.5% = 10px; to make it easier to calculate REM units.*/
}
body {
  text-align: center;
  font-family: "Oswald", sans-serif;
  font-weight: 300;
  font-size: 2.2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #faedcd;
  height: 100vh;
}
#clock {max-width: 600px;}

/* for smaller screens below 700px */
@media only screen and (max-width: 700px) {
  body {font-size: 1.8rem;}
}

/*for smaller screens below 300px*/
@media only screen and (max-width: 300px) {
  body {font-size: 1.6rem;}
}
``` 

This is how our digital clock app looks and behaves in the end:

%[https://codepen.io/Boatengg/pen/JjOEXry]


## CONCLUSION
I hope you found this tutorial useful. Please leave a comment and feel free to follow me on [Twitter](https://twitter.com/dboatengg) if you enjoyed this article.
