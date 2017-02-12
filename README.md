# Assignment - Parameters, Variadic parameters continued

> Understand variadic functions and their purpose

[![Build Status](https://travis-ci.org/helio-training/fs-corejs-functions-arguments.svg?branch=solutions)](https://travis-ci.org/helio-training/fs-corejs-functions-arguments)

## Function Parameters Revisited

A function's parameters are defined when the function declaration or expression is created.  The parameters are placed inside the `()`.


Value and kind (below) are examples of named parameters.

```js

/**
*                Parameters
*                 |      |
*                 v      v
*/
const format = (value, kind) => {
  // Additional code...
};
```

The actual names of the parameters are arbitrary so it is very common for new developers to get confused about the names of the parameters.  These values are like variables and, although the <em>can</em> be named anything, it's a good practice to have parameter names that indicate what the parameter actually represents.

For example, the `format(value, kind)` function above could be written:

```js
// Sames as the format function above, the only difference is in the function's scope which would need to be modified to use the new variables.
const format = (thing, type) => {
  // Additional code
};
```


### Function's body

The body of the function is the area between the `{ ... }`.  The curly braces are not simply a visual container - they also delineate <em> functional scope</em>, and ensure the variables don't leak into unanticipated scopes.

```js
const format = (value, kind) => {
  // Function Body here....
  // The body can use value, and kind similar to variables.
};
```

#### Default Parameters

In JS, parameters can also have a default value.  This value is assigned by default when a parameter is omitted from a function call.
 
```js
const format = (value = '', kind = 'ssn') => {
  // Additional logic.
};

/**
* value = '123-45-6789'
* kind = 'ssn' because no parameter was provided
*/
format('123-45-6789');
```



#### Variadic Parameters/Arguments and the rest operator (...)

Sometimes you don't know how many parameters a function will need. This situation calls for a variadic function.  Variadic functions work by allowing a function to pass multiple parameters to the same function.
 
```js

// Notice the ...
const greet = (...greetings) => {
  // greetings will be an array of params
};

greet('Hello', 'What up', 'Top of the morning');

// greetings = ['Hello', 'What up', 'Top of the morning'];
// We can access the parameters via the array syntax greetings[0] will be 'Hello';
```

#### Special arguments object

Inside a function, there exists a special object `arguments`.  Before the rest operator was introduced in ES2015, this was one of the only ways to create a variadic function.  Because the rest operator provides the functionality, and overcomes the shortcomings of `arguments`, rest operators are quickly becoming common practice in javascript.

```js
function oldSchool() {
  this.arguments
}
```

### Arguments revisited

When calling a function the value provided to the function are called arguments.  Developers often interchange the words "parameter" (when defining a function) and "argument" (when calling a function).
  
```js
// The `message` parameter is before the arrow function, and after the assignment
const greet = message => message.toUpperCase();

// When calling the greet function, 'Hello' is passed as an argument
greet('Hello');
```


## Assignment

1. Create a class Calculator, and export it as default
2. Create an `add` function
    1. Declare the `add` function as a variadic function
    2. Add all the values together
    3. return the result
3. Create an `introspect` function in the `Calculator` class
    1. Return the arguments passed into the `introspect` function
