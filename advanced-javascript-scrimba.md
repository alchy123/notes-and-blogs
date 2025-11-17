# Scrimba's Advanced Javascript Course Notes

<!-- If note file have it's own folder, use './../readme.md' path to go one back. However if note file doesn't have it's own folder, you should use './readme.md' path to go one back. -->
* [Click here to go one back](./readme.md).

## Advanced Foundations Chapter

* Object Destructuring means extracting properties from objects into distinct variables. [Destructuring in JavaScript - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring)

* [`setTimeout`](https://developer.mozilla.org/en-US/docs/Web/API/Window/setTimeout) function allows us to delay a piece of code. We are specifying the delay time as milliseconds and give the piece of code that will be delayed as a function.(without parantheses, because we don't want to call the function, we want to refer to it).
    * Warning: When we give an argument to our function argument directly in it's parantheses, that cause the function argument to run immediately. If we want setTimeout to work properly, we need to give the arguments to directly setTimeout function, not to the actual function argument of ours. It's not valid if your function argument is an anonymous function, if you directly created the piece of code there. 
    * We can stop a setTimeout function. You can hold that setTimeout function inside of a variable and use `clearTimeout` function to stop it. If we use this function before it executes it's argument function, we would prevent that from executing. 

* What does calling and referring means for a function? [StackExchange Forum Answer](https://softwareengineering.stackexchange.com/questions/332892/why-use-parentheses-for-function-call-when-no-arguments-are-passed#332899), [Treehouse Community Forum](https://teamtreehouse.com/community/why-do-you-not-include-parentheses-when-passing-a-function-as-an-argument)

* You can execute a piece of code repeatedly with `setInterval` function. You can stop a setInterval function with using clearInterval function. setInterval's function structures is similar with setTimeout function's structure.

* About the call stack, event loop and etc.
    * 