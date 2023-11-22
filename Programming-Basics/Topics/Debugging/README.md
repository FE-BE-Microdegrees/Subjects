# Debugging

## Description

In this topic, we'll learn about debugging in Node JS.

- What is debugging?
- Debugging tools
- Debugging tips

## Learning Outcomes

After completing this topic, you'll be able to:

- Define what debugging is
- List the debugging tools in Node JS

## What is Debugging?

Debugging is the process of finding and fixing bugs in a program. A bug is an error in a program that causes it to behave in an unexpected way. Debugging is an important skill for programmers because it allows them to find and fix bugs in their programs.

## Debugging Tools

In context of Node JS, we can use the built-in debugger to debug our programs. The built-in debugger is a tool that allows us to step through our code line by line and inspect the values of variables at each step. We can use the built-in debugger to find and fix bugs in our programs. The built-in debugger is a command-line tool that is available in Node JS version 8 and above.

Also there are code editors that have built-in debuggers. For example, **Visual Studio Code** has a built-in debugger that allows us to step through our code line by line and inspect the values of variables at each step. We can use the built-in debugger in Visual Studio Code to find and fix bugs in our programs.

To use built-in debugger in Visual Studio Code, we need to start our program in debugging mode by pressing `F5` or by clicking the `Run > Start Debugging` menu item. Then we can choose debugging environment, which in our case is `Node.js`. Then we can set breakpoints in our code by clicking on the line number where we want to set a **breakpoint**. Breakpoint is a point in our code where we want the debugger to pause execution and allow us to inspect the values of variables. Then we can start debugging by pressing `F5` or by clicking the `Run > Start Debugging` menu item. Then we can step through our code line by line and inspect the values of variables at each step.

![Debugging in VSCode](DebuggingNodeJSInVSCode.gif)

There is one more way to debug our programs in Node JS. We can use `console.log()` statements to print the values of variables at different points in our code. This is a simple way to debug our programs, but it is not as powerful as the built-in debugger.

## Debugging Tips

First of all, we should test our code as we write it. We should not wait until we have written a lot of code before testing it. We should test our code frequently. This will help us find bugs in our code early on and fix them before they become bigger problems later on. Most of the bugs are caused by simple mistakes, such as typos, missing semicolons, and missing parentheses. We should always check our code for these simple mistakes before running it.

- Use `console.log()` statements to print the values of variables at different points in your code.
- Use the built-in debugger to step through your code line by line and inspect the values of variables at each step.
- Use the built-in debugger to set breakpoints in your code and inspect the values of variables at those breakpoints.
