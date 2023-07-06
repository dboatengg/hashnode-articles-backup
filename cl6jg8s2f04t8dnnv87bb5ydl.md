---
title: "A Complete Guide to Debugging Javascript in Chrome"
datePublished: Sun Aug 07 2022 14:58:00 GMT+0000 (Coordinated Universal Time)
cuid: cl6jg8s2f04t8dnnv87bb5ydl
slug: a-complete-guide-to-debugging-javascript-in-chrome
canonical: https://hackmd.io/@dboatengx/BJf4DbgT5
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1659880944397/njMcV24SJ.png
tags: programming-blogs, javascript, web-development, chrome-cj73auo4o0012c3wted1yb7a1

---

As a developer, finding and fixing errors in your code can be extremely difficult at times. The tool that makes resolving errors so much easier is Chrome Developer Tools (also referred to as Chrome DevTools).

Chrome DevTools is a comprehensive developer toolkit with various web authoring and debugging tools. It is built directly into the Chrome browser and gives developers a deeper understanding of their applications.

This article teaches you how to debug JavaScript code using the Chrome DevTools. You will learn how to debug one specific issue, but the general workflow can help resolve all types of errors in your code.

## What Does Debugging Mean?

Debugging is the process of finding and resolving bugs within software programs. In programming and software development, the word "bug" is synonymous with "error." A bug refers to the defects or errors that cause computer software (or programs) to produce incorrect or unexpected results.

Let us look at some errors you are likely encounter in your program.

* **Syntax error:** There are specific guidelines for writing code in each programming language. Syntax errors are produced when you violate one or more of these guidelines. For instance, in JavaScript, `consol.log('your result')` would cause a syntax error because `console` is misspelled.
    
* **Semantic (logical) error:** This causes a program to compile and run correctly. However, it will not produce the desired or expected output.
    
* **Runtime error:** Here, a program is syntactically sound but has an error that can only be discovered during its execution.
    

The debugging process is vital in software development and often takes just as much time as writing code.

## What is Chrome Developer Tools?

Chrome Developer Tools is a set of web developer tools built directly into the Google Chrome browser. It helps developers edit web pages and identify and resolve errors, enabling them to build sites and applications much faster and efficiently.

The interface of Chrome DevTools has about nine panels.

![](https://i.imgur.com/p7y6uNA.png align="left")

Here is a summary of what each panel does:

* **Elements:** Modify DOM elements in real-time and observe the effects of your changes on the page.
    
* **Console:** Provides information about the interactive elements on a web page.
    
* **Sources:** View and edit program files, debug JavaScript code and set up workspaces ( so that changes you make in DevTools get saved to the code on your file system).
    
* **Network:** Displays all the resources or files loaded on a site.
    
* **Performance:** Analyses the speed and optimization of web applications.
    
* **Memory:** Provides information about how a page uses memory.
    
* **Application:** Displays content from your browser's storage. e.g. localStorage, sessionStorage, cookies, IndexDB, etc.
    
* **Security:** Provides basic security-related information, allowing you to view a site's HTTPS certificate and TLS status.
    
* **Lighthouse:** Audit applications' quality, performance, accessibility, and SEO.
    

This article will primarily cover the **Sources panel**, where we debug JavaScript code.

## The Sources Panel

To get started with the *Sources panel* and all its components, let's first look at how to open Chrome DevTools in your browser.

### Opening Chrome DevTools

Here are some ways you can open the Chrome DevTools in your browser.

* Using keyboard shortcuts:
    
    * <kbd>Command</kbd> + <kbd>Opt</kbd> + <kbd>I</kbd> (macOs)
        
    * <kbd>Control</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd> (Windows or Linux)
        
* Right-click anywhere on the browser page and click the "Inspect" option.
    
* Using the Chrome main menu:
    
    1. Click the Chrome menu button
        
    2. Select *More Tools*
        
    3. Select *Developer Tools*
        

Here’s what you’ll see when you open Chrome Developer Tools:

![](https://i.imgur.com/w3n1Rbp.png align="left")

> By default, the Chrome DevTools opens to the Elements panel.

### Exploring the Sources panel

Open the **Sources panel** for the sample demo page we'll be using for this tutorial by following the intstructions below.

* Open the [example page](https://devtools-demo.netlify.app/) in Chrome.
    
* Open Chrome developer tools.
    
* Select the *Sources tab*.
    

Here's what you would see if you opened the *Sources panel* for the first time:

![](https://i.imgur.com/8qrwIOu.png align="left")

Click the toggler button and select the `main.js` file in the tree view. Here’s what would show up:

![](https://i.imgur.com/PYA7JCA.png align="left")

As can be seen, the Sources panel has three parts:

* **File Navigator Page \[1\]:** Displays all the files that a page loads, such as HTML, JavaScript, CSS, and other files.
    
* **Code Editor \[2\]:** Click on a file in the file navigator pane to view or edit its contents in the code editor.
    
* **JavaScript Debugging Pane \[3\]**: Contains all the necessary tools for debugging JavaScript code.
    

## Example Page Project

We will use the sample demo page you opened in the previous section to demonstrate how to debug JavaScript with Chrome DevTools. The program for the demo performs a basic arithmetic operation of adding two numbers and printing out their sum.

![](https://i.imgur.com/FrBRkcl.png align="left")

However, there are some bugs on this page that you will fix if you follow this tutorial.

## The Console.log Method

The simplest way to resolve the bug on the sample demo page is to insert the `console.log()` function in your code to inspect variable values simultaneously.

This method is one of the most common among developers. Often, it’s enough, but sometimes you don’t get enough insights or the expected results needed to debug an error.

Although the`console.log()` function can be a good option for resolving bugs, Chrome DevTools does a more effective job.

Therefore, rather than using the `console.log()` function to determine where your code is going wrong, you should consider using Chrome DevTools instead.

## How to Debug JavaScript with DevTools

Now that we have had a quick overview of Chrome DevTools, let's discuss some useful debugging strategies to help debug the code for the example demo page.

The general idea here is to set a breakpoint, an intentional stopping place in your code, and then step through your code's execution, one line at a time.

### Step 1: Reproduce the bug

Reproducing the bug is the first step to debugging. "Reproduce the bug" means finding a series of actions that consistently cause the bug to appear.

Follow along with the instructions below to reproduce the bug that you’re going to fix:

* Open [sample demo page](https://devtools-demo.netlify.app/) in a new tab.
    
* On the page, enter 23 for the first input field.
    
* Enter 4 for the other input field.
    
* Click "Add Numbers" button.
    

![](https://i.imgur.com/Rzae666.png align="left")

Whoops! Looking at the results printed below the button. It says 23 + 4 = 234, which is wrong. The result should rather be 27. This is the bug that you're going to fix.

### Step 2: Add Breakpoint

A breakpoint is an intentional stopping point in your code's execution. It is the point in a program's execution where the developer wishes to pause the program and inspect the contents of variables and other properties.

On the demo page, it is evident that the sum of the two numbers becomes incorrect after clicking the “Add numbers” button. Therefore, you need to check to see if the program is adding the correct values.

To do this, you must set a breakpoint just before the program adds the two numbers. Doing this will help to analyze the values of all defined variables up to the breakpoint.

There are many types of breakpoints you can set in your code. Let's take a look at some of them:

| Type of Breakpoint | Use This When You Want to Pause... |
| --- | --- |
| Line-of-code | on an exact point in your code. |
| Conditional | on an exact point in your code but only when a defined condition evaluates to true. |
| DOM | at point in a code block that modifies a specific DOM node. |
| Event Listener | at a piont in a code block that runs after an event is fired. |
| Function | Whenever a function is called. |

#### How to Add Breakpoints

Here, we are going to set a line-of-code breakpoint. To do this:

* Open Chrome DevTools and go to the *Sources panel*
    
* Navigate to the *file navigator pane* and select `main.js` to open its content in the code editor.
    
* Within the code editor, click at line number 21, right on the number digit, not on the code.
    

It should look like this:

![](https://i.imgur.com/c8vPCvG.png align="left")

After setting the breakpoint, the easiest way to activate the debugger is to fill in the input fields on the demo page and click the "Add numbers" button. DevTools will pause the execution and highlight the *21st line* (where the breakpoint was set).

*Congratulations! You've set a breakpoint.*

### Step 4: Step through the code

Executing scripts in the wrong order is a common source of bugs. Stepping through your code allows you to walk through the code one line at a time to find out where the bug occurred.

To help illustrate the concept of stepping through your code, we will use the buttons at the top of the *JavaScript debugging pane*. *Let's get started:*

* **Resume:** With this button, DevTools executes your script until the next breakpoint. And if there are no more breakpoints, the debugger loses control of the program.
    
* **“Step”:** This is used to run the next javaScript statement.
    
* **Step over next function call:** Allows debugger to execute the next code block. However, if the code block involves a function call, the debugger "steps over" (skips) it.
    
* **Step into next function call:** Causes debugger to execute the next function to further analyse it. If there is a function call, it goes into it and you can see how the function is executes line by line till it returns.
    
* **Step out of current function:** If you step into a function but don't want to see how the rest of the function executes, you can skip it with this button.
    

That’s the basic idea behind stepping through your code. If you look at the code in `main.js`, it is evident that the bug is probably somewhere in the `onClick()` function (where the two numbers are added).

> **IMPORTANT**  
> When debugging a large program, a lot of code may not be related to the problem you're debugging.  
>   
> You could "step" through all the lines, but that can be tedious. You could also set a line-of-code breakpoint on the line you're interested in and then press "Resume Script Execution” to debug , but there's a faster way.  
>   
> Right-click the line of code you're interested in, and then select "Continue to here." DevTools will instantly run all the code up to that point and then pause on that line.

### Step 5: Check variable values

Chrome DevTool provides tools that help you analyze the state of your code and variable values on any line as you step through it.

* **Watch:** Using the Watch window, you can specify a variable (or expression) you want to monitor. You can add the expression or variable by clicking the plus sign **+**.
    
* **Call Stack:** The Call Stack window displays a set of functions and methods invoked during your code's execution.
    
* **Scope:** Use the scope window to view and edit values of properties and variables in the clossure, local and global scope.
    

By "watching" the variables`firstNumber` and `secondNumber`, we can see that their values look suspicious. They're wrapped in quotes, which means that they're string values. To confirm this, let's watch the data type of these variables by adding the following expressions to the watch list:

* `typeof firstNumber`
    
* `typeof secondNumber`
    

![](https://i.imgur.com/DrNbZIb.png align="left")

It is now confirmed that the values of the variables are strings, which is probably the cause of the bug.

### Step 5: Applying a fix

After finding the cause of the bug, all that's left is to try to fix it. You can do this by editing your code and re-running the demo. You don't even need to leave DevTools to apply the fix. Following the instructions below, you can edit your JavaScript code directly within the DevTools interface.

* If you are in debugging mode, click the *Resume script execution* button to exit.
    
* Now, in the Code Editor, replace the code on *line 21* with `let sum = parseInt(firstNumber) + parseInt(secondNumber)`.
    
* Press <kbd>Command</kbd>+<kbd>S</kbd> (Mac) or <kbd>Control</kbd> +<kbd>S</kbd> (Windows, Linux) to save your change.
    
* Click *Deactivate breakpoints* to ignore any breakpoints you've set.
    

Now, try out the demo with different values.

![](https://i.imgur.com/4xGHeP8.png align="left")

The demo now works as expected!

## Wrapping Up

Congrats! You’ve successfully debugged the code for the sample demo page using Chrome DevTools. There's so much you can do with Chrome DevTools. It is a powerful tool, and taking the time to master it will make you a more efficient debugger.

I encourage you to experiment with DevTools using your own applications. Get used to stepping through your code and analyzing the state of variables and properties at each point.

Thanks for reading. I hope this has been a worthwhile read. Kindly share this article and follow me on Twitter [@dboatengx](https://twitter.com/dboatengx) for updates on future posts.

Cheers!

> **Want to learn more?**  
> Check out Google's [documentation](https://developer.chrome.com/docs/devtools/javascript/) on debugging JavaScript with Chrome DevTools.