## Javascript
js is an object-oriented programming language that is having a lot of applications. 

advantages -
* Less server interaction
* Immediate feedback
* Richer interfaces
* high performance

It can be used for both client-side as well as server-side

### 1. data Tyoes

#### a. primitive
Primitive data types are immutable and they store single values
* do not have methods 
* primitve are the basic data types
example - string, number, boleaan, null, undefined, bigint and sysmbol

#### b. non primitive 
non-primitive data types are mutable and they store multiple values
* primitve are the advance data types
example - array and object


### 2. string methods
These are built-in functions to manipulate a string
  * str.toUpperCase( )
  * str.toLowerCase( )
  * str.trim( ) // removes whitespaces
  * str.slice(start, end?) // returns part of string
  * str1.concat( str2 ) // joins str2 with str1
  * str.replace( searchVal, newVal )
  * str.charAt( idx )

### 3. Array methods
  * Push( ) : add to end
  * Pop( ) : delete from end & return
  * toString( ) : converts array to string
  * Concat( ) : joins multiple arrays & returns result
  * Unshift( ) : add to start
  * shift( ) : delete from start & return
  * Slice( ) : returns a piece of the array
      slice( startIdx, endIdx )
  * Splice( ) : change original array (add, remove, replace)
      ex => splice( startIdx, delCount, newEl1... )
  * map => Creates a new array with the results of some operation.
```
arr.map( callbackFnx( value, index, array ) )

let newArr = arr.map( ( val ) => {
  return val * 2;
 } )
```
  * Filter => Creates a new array of elements that give true for a condition/filter.
```
let newArr = arr.filter( ( ( val ) => {
  return val % 2 === 0;
})
```
  * Reduce => Performs some operations & reduces the array to a single value. It returns
that single value.




 
### Functions
Block of code that performs a specific task,
```
function functionName( ) {                 const functionName = () => {
 do some work                                  do some work
}                                           }

forEach Loop =>
it is Callback Function to execute for each element in the array

arr.forEach( ( val ) => {
  console.log(val);
})
```



## Javascript questions
#### 1. difference between var, let & const

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

### 10. Global variable and local variable and their scope
variable that declared outside of the function is Global variable

* we can define it using => var, let and const
* it can be accessed anywhere in the program

variable that declared inside of the function is local variable


### 11. Session State and the View State
Session state is saved on the server, ViewState is saved in the page
* in Session State have access all pages within a web application
* ViewState is used for accessing a session only

### 12. Is JavaScript a case-sensitive language
Yes, here for keywords, variables, function names,we are using consistent capitalization of letters.

### 13. cookie
cookie is an amount of user information in web pages
* user information data stored our computer

When a web server has sent a web page to a browser, the connection is shut down, and the server forgets everything about the user
so for that we are using the cookie
* When a user visits a web page, his/her name can be stored in a cookie.
* Next time the user visits the page, the cookie "remembers" his/her name.

#### Create a Cookie

```
document.cookie = "username=John Doe";
```

### 14. Local storage & Session storage
both are browser storage
#### Local storage
Local storage allows you to store data in the browser and there is no expiration date until it's deleted manually.
* data is not sent back to the server for every HTTP request

#### Session storage
Session storage allows you to store data in the browser and the data is stored until the browser is closed.


### 15. ‘Strict’ mode
Strict mode is a way to introduce better error-checking
* during strict mode, we cannot implicitly declared variables, or assign a value to a read-only property etc.
* we can enable strict mode by adding “use strict” at top of the code






