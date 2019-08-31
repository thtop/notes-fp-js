# Introduction to Currying

## Function To Transform Array - map

```js
// greet -> Higher-Order fn (return function)
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}

console.log(greet('Good Morning')('James'));

// ** array
const friends = ['Nate', 'Jim', 'Scorr', 'Dean'];

// map = Higher-Order fn (function input parameter)
const friendGreetings = friends.map(greet('Good Morning'));

console.log(friendGreetings);
```

## Higher-Order Function

- function that either takes a function as an input parameter
- and or returns a function

```js
function MyFunction(Fn) {
  return function() {
    //...
  };
}
```

## Closure

- passing in the `greeting` parameter in the `greet()`
- and referencing the `greeting` inside the return anonymous function is called a closure

```js
// greet -> Higher-Order fn (return function)
function greet(greeting) {
  return function(name) {
    return `${greeting} ${name}`;
  };
}
```

- closure are functions that can access
- and use variables that aren't directly passed into the function
- because of the placement of the function relative to the variables

## Exercise

- [knowthen.com/fp7](https://jsbin.com/satowo/edit?js,console)
- [solution](https://jsbin.com/vaqomiy/1/edit?js,console)

```js
// Functional Programming for Beginners Excercise

// create the code to go from studentPoints array,
// to studentFeedback (as shown in comments below)

const studentPoints = [
  { name: 'Joe', points: 88 },
  { name: 'Jen', points: 94 },
  { name: 'Steph', points: 77 },
  { name: 'Allen', points: 60 },
  { name: 'Gina', points: 54 }
];

const messages = {
  a: 'Excellent Job',
  b: 'Nice Job',
  c: 'Well cone',
  d: 'What happened',
  f: 'Not good'
};

function letterGrade(points) {
  if (points >= 90) {
    return 'a';
  } else if (points >= 80) {
    return 'b';
  } else if (points >= 70) {
    return 'c';
  } else if (points >= 60) {
    return 'd';
  } else {
    return 'f';
  }
}

function feedBack(message) {
  return function(student) {
    const grade = letterGrade(student.points);
    const msg = message[grade];
    return `${msg} ${student.name}, you got an ${grade}`;
  };
}

const gradeFeedback = studentPoints.map(feedBack(messages));

console.log(gradeFeedback);

/*
const studentFeedback = [
  'Nice Job Joe, you got an b',
  'Excellent Job Jen, you got an a',
  'Well done Steph, you got an c',
  'What happened Allen, you got an d',
  'Not good Gina, you got an f',
]; 
*/

// Solution found at:
// https://jsbin.com/vaqomiy/1/edit?js,console
```
