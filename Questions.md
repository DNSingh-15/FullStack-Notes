## Javascript questions
js is an object-oriented programming language that is having a lot of applications. 

It can be used for both client-side as well as server-side

### 1. difference between var, let & const

var => reassigned + redeclared
```
var a = 5,
var a = 10
```

let => reassigned + non-redeclared
```
let a = 5,
  a = 10
```

cont => non-reassigned + non-redeclared
```
const a = 5
```
### 2. difference between == , ===
```
==  => it compares only value
=== => compare value as well as data type
```

### 3. Promises, callback functions, async Await
#### Promises
* promises represents that is something eventually fullfilled
* promises are used to handle the asynchronous operations
1. promises provide more elegant way

types
1. Reject
2. resolve 
3. pending

#### callback
* callback is a function that passed into another function as a parameter
* callback is also used to handle the asynchronous operations
1. callback is a tradition way

#### async Await
* async Await is also used to handle the asynchronous operations
* async Await allows us to execute our flows without blocking our application
1. async Await provides more convenient and readable way

### 4. callback hell
Nested callbacks is call back hell
* it is unreadable and difficult to manage the code
* callback hell can be avoided by using the Promises and async / await

### 5. Hoisting
Hoisting is JavaScript's default behavior for use functions & variables before they're declared
* it host only declaration and initialization

### 6. Generator function 
generator function is a such type of function that we can pause and resume with the using of yield
* 
Generator Functions are memory efficient, they save a lot of memory

### 7. closure
closure is a function where an inner function has access to the outer function's variables and arguments

```
function greeting() {
    let message = 'Hi';

    function sayHi() {
        console.log(message);
    }
    sayHi();
}
greeting();
```

### 8. new features in ES6 (ECMAScript)
1. let
2. const
3. Arrow Functions
4. For/of
5. Classes
6. Map Objects

### 9. event loop
event loop is a mechanism that allows the runtime to execute tasks asynchronously

### 10. Global variable scope
variable that declared outside of the function is Global variable

we can define it using => var, let and const

it can be accessed anywhere in the program


### 11. Session State and the View State
Session state is saved on the server, ViewState is saved in the page
* in Session State have access all pages within a web application
* ViewState is used for accessing a session only

### 12. Is JavaScript a case-sensitive language
Yes, here for keywords, variables, function names,we are using consistent capitalization of letters.



## Node.js questions

node.s is a javascript run time environment
* runtime environment allows the source code to interact with the operating system.
 
### 1. Body Parser, params & query
#### Body Parser
it is a http request body 
exm  =>  payload

#### params
params are used to send additional information to the server
exm => http://www.google.com/books/1

here  `req.param.id = 1`

#### query
Query are used to retrieve information from the URL of page
exm => http://www.google.com/books/?id=5

here  `req.query = ?id=5`






