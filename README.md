# javascript_interview
collection of javascript interview questions

In certain programming languages, if we defined a function to take in a certain number of parameters,
and used the function with anything other than the requisite number of parameters, it will return a syntax error.
In Javascript however, we’re free to pass in as many or as few parameters to a function as we wish.

var addOneToFirstArgument = function(x) {
  return x+1
}
addOneToFirstArgument(1,2,3)  ‘x’ refers to ‘1’.

If we so desired, the trailing arguments can be accessed within the function body using the ‘arguments’ object:

What is the arguments object?
The arguments object is a collection of parameter values pass in a function. 
It helps us know the number of arguments pass in a function.
It's an Array-like object because it has a length property and we can access individual
values using array indexing notation arguments[1] but it does not have the built-in methods
in an array forEach,reduce,filter.


1) An arguments object will not be created if arguments is the name of a formal parameter 
  or is used as a variable or function declaration within the function body:

function foo(a, arguments) {
    return arguments;
};
foo(1); //undefined
 
function foo(a, b) {
    var arguments = 43;
    return arguments
};
foo(1, 2); //43

Moreover changing the length of arguments has no effect on its indexed properties:

var args = echoArgs(1,2,3);
args.length = 1;
args[2]; //3


the arguments object does not work on ES6 arrow functions.

We can solve this problem by the rest syntax.
const four = (...args) => args;
The rest parameter allows you to represent an indefinite number of arguments as an array.
It collects parameters and turns them into an array.
It gives us an easier and cleaner way of working with an indefinite number of parameters  

function myFunction(...options) {
     return options;
}
myFunction('a', 'b', 'c');      // ["a", "b", "c"]

If there are no arguments, the rest parameter will be set to an empty array:

function myFunction(...options) {
     return options;
}
myFunction();      // []

Nevertheless, the rest parameter is not without its limitations.
For example, it must be the last argument; otherwise, a syntax error will occur:

function logArguments(a, ...params, b) {
        console.log(a, params, b);
}
logArguments(5, 10, 15);    // SyntaxError: parameter after rest parameter

Another limitation is that only one rest parameter is allowed in the function declaration:

function logArguments(...param1, ...param2) {
}
logArguments(5, 10, 15);    // SyntaxError: parameter after rest parameter



 
 

 
 
