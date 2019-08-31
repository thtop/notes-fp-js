# Currying and Partial Application

## Curring

```js
function greet(greeting, name) {
  return `${greeting} ${name}`;
}

function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}
```

---

## Function took 2 parameters

```js
function greet(greeting, name) {
  return `${greeting} ${name}`;
}

console.log(greet('Good Morning', 'James')); // Good Morning James
```

---

## Function took 2 parameters just didn't work with map()

:x:

```js
function greet(greeting, name) {
  return `${greeting} ${name}`;
}

const friends = ['Nate', 'Jim', 'Scott', 'Dean'];

// map()
const friendGreetings = friends.map(greet);
console.log(friendGreetings);
// [ 'Nate 0', 'Jim 1', 'Scott 2', 'Dean 3' ]
```

---

## Curring worked just fine with map()

:heavy_check_mark:

```js
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}

const friends = ['Nate', 'Jim', 'Scott', 'Dean'];

// map()
const friendGreetings = friends.map(greet('Good Morning'));
console.log(friendGreetings);
/*
[
  'Good Morning Nate',
  'Good Morning Jim',
  'Good Morning Scott',
  'Good Morning Dean'
]
*/
```

---

## Curry and Partial Application

- Partial Application -> Specializing a function
- Using Function

```js
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}

const morningGreetingFn = greet('Good Morning');
console.log(morningGreetingFn('Nate')); // Good Morning Nate

const afternooGreetingFn = greet('Good Afternoon');
console.log(afternooGreetingFn('Lexa')); // Good Afternoon Lexa
```

- Curry -> Coding Function

```js
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}
```

---

## Partial Application Without Curried Function

- Helper Function To Do Partial Application

```js
// partial: allows for partial application
function add(x, y) {
  return x + y;
}

const add3 = partial(add, [3]);

console.log(add3(2));
```

> Curry -> Creating Function No Data
> Partial Application -> Using Function With Data

---

## Partial Application with

- Curried Function
- Regular Function (w/ helper)

> Using Currying Partial Application **All The Time**!
> 20% Item -> 80% Code

---

## Currying Order of Parameters Matter?

```js
function someFn(parm1, parm2, parm3, parm4) {
  //...
}

// Or

function someFn(parm2, parm4, parm1, parm3) {
  //...
}

// ** 1
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}

// ** 2
function greet(name) {
  return function(greeting) {
    return `${greeting} ${name}`;
  };
}

// We needed the name to be the last parameter because
// the name is what the map() function wolud be supplying
```
---
## Parameters That...

- General -> Specialized Should Be First

```js
// Single person
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}

console.log(greet('Good Afternoon')('Nate')); // Good Afternoon Nate

// curriedFn(1)('two')(3)('four')(5);
```
---
## Ramda Library

```js
// Alternative Function Syntax
// () => {}; // Lambda Functions

//const greet = (greeting, name) => `${greeting} ${name}`;

// https://cdnjs.cloudflare.com/ajax/libs/ramda/0.26.1/ramda.min.js

const greet = R.curry((greeting, name) => `${greeting} ${name}`);

const friends = ['Nate', 'Jim', 'Scott', 'Dean'];

// map()
const friendGreetings = friends.map(greet('Good Morning'));
console.log(friendGreetings);
/*

["Good Morning Nate", "Good Morning Jim", "Good Morning Scott", "Good Morning Dean"]

*/

const morningGreeting = greet('Top of the morning to ya');

console.log(morningGreeting('Dimmer'));
// "Top of the morning to ya Dimmer"
```
