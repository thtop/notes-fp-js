# Function Composition

- Making Functions Out of Other Functions
- by combining the logic of the other functions

## Picture Exaple

```js
function slice(apple) {
  return `slice ${apple}`;
}

function bake(slice) {
  return `apple pie`;
}

const makePie = compose(
  bake,
  slice
);

const pie = makePie(apple);
```

---

## JavaScript Example Version 1

```js
// https://cdnjs.cloudflare.com/ajax/libs/ramda/0.26.1/ramda.min.js

const sentence =
  'It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters';

// step: 1
const wordList = R.split(' ', sentence);

console.log(wordList);

// step: 2
const wordCount = R.length(wordList);
console.log(wordCount);

const countWords;

```

---

## Version 2

```js
// https://cdnjs.cloudflare.com/ajax/libs/ramda/0.26.1/ramda.min.js

const sentence =
  'It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters';

const countWords = R.compose(
  R.length, // step: 2
  R.split // step: 1
);

console.log(countWords(' ', sentence));
```

---

## Version 3

```js
// https://cdnjs.cloudflare.com/ajax/libs/ramda/0.26.1/ramda.min.js

const sentence =
  'It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters';

const countWords2 = R.compose(
  R.length, // step: 2
  R.split(' ') // step: 1
);

console.log(countWords2(sentence));
```

---

## Version 4

```js
// https://cdnjs.cloudflare.com/ajax/libs/ramda/0.26.1/ramda.min.js

const sentence =
  'It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters';

const countWords3 = R.pipe(
  R.split(' '),
  R.length
);

console.log(countWords3(sentence));
```

---

## Exercise

- [knowthen.com/fp8](https://jsbin.com/nuzehow/4/edit?js,console)
- [hints](https://jsbin.com/jokefus/2/edit?js,console)
- [solution](https://jsbin.com/duxewec/1/edit?js,console)

```js
// Count how many digits there are in the following
// sentence, using functional composition

// NOTE: If you get stuck, you can get some hints from
// the following jsbin:
// https://jsbin.com/jokefus/2/edit?js,console
// my solution is here: https://jsbin.com/duxewec/1/edit?js,console

const sentence =
  'PechaKucha is a presentation style in which 20 slides are shown for 20 seconds each (6 minutes and 40 seconds in total).';

const numbersInString = expect(numbersInString(sentence)).toBe(7); // add function composition here

console.log('If you see this printed in the console, the test passed!');
```

---

## Hints

```js
// count how many digits there are in the following
// sentence, using functional composition

// HINTS:
// There are 4 steps to this compostion, each of them listed as comments
// in the pipe function.
//

const sentence =
  'PechaKucha is a presentation style in which 20 slides are shown for 20 seconds each (6 minutes and 40 seconds in total).';

const numbersInString = R
  .pipe
  // 1. transform the string into a list of individual characters
  // 2. attempt to transform the individual characters into integers
  // 3. filter the list to only include integers
  // 4. find the length of the list of numbers
  ();

expect(numbersInString(sentence)).toBe(7);

console.log('If you see this printed in the console, the test passed!');

// FURTHER HINTS, Only look if you need to
// 1. Use R.split
// 2. Use R.map and parseInt
// 3. Use R.filter and Number.isInteger
// 4. Use R.length
```

---

## Solution

```js
// Count how many digits there are in the following
// sentence, using functional composition

// NOTE: If you get stuck, you can get some hints from
// the following jsbin:
// https://jsbin.com/gikuwol/edit?js,console

const sentence =
  'PechaKucha is a presentation style in which 20 slides are shown for 20 seconds each (6 minutes and 40 seconds in total).';

const numbersInString = R.pipe(
  R.split(''),
  R.map(parseInt),
  R.filter(Number.isInteger),
  R.length
);

expect(numbersInString(sentence)).toBe(7);

console.log('If you see this printed in the console, the test passed!');
```
