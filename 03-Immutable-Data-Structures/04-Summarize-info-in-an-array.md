# Summarize information in an array

## Example Reduce

```js
const numbers = [1, 2, 3];

function sum(accumulator, number) {
  return accumulator + number;
}

const total = numbers.reduce(sum);
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

const count = grades.length;

console.log(total, total / count); // 623 77.875
```
