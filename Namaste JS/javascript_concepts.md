
## JavaScript Concepts

### 1. How JavaScript Works? What is Execution Context?
JavaScript is a single-threaded, non-blocking, asynchronous, concurrent programming language. The execution context is an abstract concept that holds information about the environment within which the current code is being executed. 

```js
// Global Execution Context
console.log(this); // Points to the global object (window in browsers)
```

### 2. How JavaScript Code is executed? Call Stack
JavaScript uses a call stack to manage execution contexts. The call stack is a stack data structure that keeps track of function calls.

```js
function first() {
    console.log("First");
}

function second() {
    first();
    console.log("Second");
}

second(); // Outputs: "First", "Second"
```

### 3. Hoisting in JavaScript (variables & functions)
Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope.

```js
console.log(a); // undefined
var a = 5;

hoistedFunction(); // Works because function declarations are hoisted
function hoistedFunction() {
    console.log("Hoisted!");
}
```

### 4. How functions work in JS and what is Variable Environment?
Functions in JS create their own execution context and variable environment, which is a place where variables live.

```js
function greet() {
    var name = "John";
    console.log(name); // "John"
}
greet();
```

### 5. SHORTEST JS Program is an empty file. Explain window & this keyword in all scenarios
- `window` is the global object in browsers.
- `this` refers to different things depending on the context.

```js
console.log(this === window); // true in global context

function showThis() {
    console.log(this); // In a function, this refers to the global object (window in browsers)
}

const obj = {
    method: function() {
        console.log(this); // In a method, this refers to the object
    }
};

new showThis(); // `this` refers to the new instance
```

### 6. undefined vs not defined in JS
- `undefined`: A variable declared but not assigned a value.
- `not defined`: A variable that has not been declared.

```js
var a;
console.log(a); // undefined
console.log(b); // ReferenceError: b is not defined
```

### 7. The Scope Chain, Scope & Lexical Environment
Scope is the context in which variables are accessible. The scope chain is a list of all the scopes in which a variable can be resolved.

```js
function outer() {
    var a = 10;
    function inner() {
        var b = 20;
        console.log(a + b); // 30
    }
    inner();
}
outer();
```

### 8. let & const in JS and Temporal Dead Zone
`let` and `const` are block-scoped. Temporal Dead Zone (TDZ) is the time between entering scope and variable declaration.

```js
console.log(x); // ReferenceError
let x = 10;

const y = 20;
y = 30; // TypeError: Assignment to constant variable.
```

### 9. BLOCK SCOPE & Shadowing in JS
Block scope allows variables to be confined to a specific block. Shadowing occurs when a variable in a local scope has the same name as one in an outer scope.

```js
let a = 5;
{
    let a = 10; // shadows outer `a`
    console.log(a); // 10
}
console.log(a); // 5
```

### 10. Closures in JS
A closure is a function that retains access to its lexical scope even when the function is executed outside that scope.

```js
function outer() {
    let a = 10;
    return function inner() {
        console.log(a); // 10
    };
}
const closureFunc = outer();
closureFunc();
```

### 11. setTimeout + Closures Interview Questions
Closures can capture variables for use in asynchronous callbacks.

```js
for (let i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i); // 0, 1, 2 (because `let` is block-scoped)
    }, 1000);
}
```

### 12. Give hard interview questions(problems) on Closures along with answer (code)
**Question**: Create a function that keeps a private counter and returns functions to increment and retrieve the counter.

```js
function createCounter() {
    let count = 0;
    return {
        increment: function() {
            count++;
        },
        getCount: function() {
            return count;
        }
    };
}

const counter = createCounter();
counter.increment();
console.log(counter.getCount()); // 1
```

### 13. FIRST CLASS FUNCTIONS and Anonymous Functions
Functions in JavaScript are first-class citizens, meaning they can be stored in variables, passed as arguments, and returned from other functions.

```js
const greet = function() {
    console.log("Hello");
};

function caller(fn) {
    fn();
}

caller(greet); // "Hello"
```

### 14. Callback Functions in JS and Event Listeners
A callback function is passed as an argument to another function and executed at a certain time.

```js
document.getElementById("btn").addEventListener("click", function() {
    console.log("Button clicked");
});
```

### 15. Asynchronous JavaScript & EVENT LOOP from scratch
JavaScript's event loop allows it to perform non-blocking I/O operations by offloading operations to the browser's APIs and handling their callbacks asynchronously.

```js
console.log("Start");
setTimeout(() => {
    console.log("Middle");
}, 0);
console.log("End");

// Output: Start, End, Middle
```

### 16. JS Engine and Google's V8 Architecture
The V8 engine compiles JavaScript directly to native machine code, providing fast execution.

```js
// Example of V8-optimized code
const numbers = [1, 2, 3, 4];
const squares = numbers.map(n => n * n);
console.log(squares); // [1, 4, 9, 16]
```

### 17. Everything to know about setTimeout
`setTimeout` schedules a function to run after a specified delay.

```js
setTimeout(() => {
    console.log("Executed after 1 second");
}, 1000);
```

### 18. Higher-Order Functions, Functional Programming
Higher-order functions take other functions as arguments or return them as results.

```js
function multiplyBy(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

### 19. map, filter & reduce
Array methods for functional programming.

```js
const arr = [1, 2, 3, 4, 5];

const doubled = arr.map(n => n * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

const evens = arr.filter(n => n % 2 === 0);
console.log(evens); // [2, 4]

const sum = arr.reduce((total, n) => total + n, 0);
console.log(sum); // 15
```
