# Summarize information in an array

## Example Reduce

```js
const numbers = [1, 2, 3];

const total = numbers.reduce(sum);

function sum(accumulator, number) {
  return accumulator + number;
}

console.log(total); // 6
```

## Reduce with grades (AVG)

```js
const grades = [60, 55, 80, 90, 99, 92, 75, 72];

const total = grades.reduce(sum);

function sum(acc, grade) {
  return acc + grade;
}

const count = grades.length;

console.log(total, total / count); // 623 77.875
```

## Reduce with grades (Letters)

```js
const grades = [60, 55, 80, 90, 99, 92, 75, 72];

const letterGradeCount = grades.reduce(groupByGrade, {});

function groupByGrade(acc, grade) {
  const { a = 0, b = 0, c = 0, d = 0, f = 0 } = acc;
  if (grade >= 90) {
    return { ...acc, a: a + 1 };
  } else if (grade >= 80) {
    return { ...acc, b: b + 1 };
  } else if (grade >= 70) {
    return { ...acc, c: c + 1 };
  } else if (grade >= 60) {
    return { ...acc, d: d + 1 };
  } else {
    return { ...acc, f: f + 1 };
  }
}

console.log(letterGradeCount); //{ d: 1, f: 1, b: 1, a: 3, c: 2 }
```

## Ecercise

- [knowthen.com/fp6](https://jsbin.com/dawamuy/1/edit?js,console)
- [TIP](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names)
- [solution](https://jsbin.com/dehiqux/1/edit?js,console)

```js
// Functional Programming for Beginners Exercise

const reviews = [
  4.5,
  4.0,
  5.0,
  2.0,
  1.0,
  5.0,
  3.0,
  4.0,
  1.0,
  5.0,
  4.5,
  3.0,
  2.5,
  2.0
];

// 1. Using the reduce function, create an object that
// has properties for each review value, where the value
// of the property is the number of reviews with that score.
// for example, the answer should be shaped like this:
// { 4.5: 1, 4: 2 ...}

const countGroupeByReview = reviews.reduce(groupBy, {});

function groupBy(acc, review) {
  const count = acc[review] || 0;
  return { ...acc, [review]: count + 1 };
}

console.log(countGroupeByReview);

// { '1': 2, '2': 2, '3': 2, '4': 2, '5': 3, '4.5': 2, '2.5': 1 }

// TIP: checkout computed properties discussed here:
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names
// solution can be found at:
// https://jsbin.com/dehiqux/1/edit?js,console
```
