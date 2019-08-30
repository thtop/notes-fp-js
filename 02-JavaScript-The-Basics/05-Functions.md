# Functions

## Not functions

```js
const grade1 = 50 + Math.random() * 50.0;
const grade2 = 50 + Math.random() * 50.0;
const grade3 = 50 + Math.random() * 50.0;

console.log(grade1);
console.log(grade2);
console.log(grade3);

if (grade1 >= 90) {
  console.log('A');
} else if (grade1 >= 80) {
  console.log('B');
} else if (grade1 >= 70) {
  console.log('C');
} else if (grade1 >= 60) {
  console.log('D');
} else {
  console.log('F');
}

if (grade2 >= 90) {
  console.log('A');
} else if (grade2 >= 80) {
  console.log('B');
} else if (grade2 >= 70) {
  console.log('C');
} else if (grade2 >= 60) {
  console.log('D');
} else {
  console.log('F');
}

if (grade3 >= 90) {
  console.log('A');
} else if (grade3 >= 80) {
  console.log('B');
} else if (grade3 >= 70) {
  console.log('C');
} else if (grade3 >= 60) {
  console.log('D');
} else {
  console.log('F');
}
```

---

## Functions

```js
const grade1 = 50 + Math.random() * 50.0;
const grade2 = 50 + Math.random() * 50.0;
const grade3 = 50 + Math.random() * 50.0;

console.log(grade1, letterGrade(grade1));
console.log(grade2, letterGrade(grade2));
console.log(grade3, letterGrade(grade3));

function letterGrade(grade) {
  if (grade >= 90) {
    return 'A';
  } else if (grade >= 80) {
    return 'B';
  } else if (grade >= 70) {
    return 'C';
  } else if (grade >= 60) {
    return 'D';
  } else {
    return 'F';
  }
}
```

- functions allow us to create reusable logic
- or code that transforms values from one thing to another
- X -> Y
- 95% -> A

---

## Exercise

- [knowthen.com/fp3](https://jsbin.com/nobuloc/edit?js,console)

```js
const name = 'James';

const greeting = greet('Good Day', name);

console.log(greeting);

// I'm using the "greet" function on line 3 above,
// but "greet" doesn't actually exist.
// You need to write the greet function so it returns

function greet(message, name) {
  return `${message} ${name}`;
}
```
