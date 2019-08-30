# Updating arrays, in an immutable way

## Adding Array - Spread syntax

```js
const meals = [
  { id: 1, description: 'Breakfast', calories: 420 },
  { id: 2, description: 'Lunch', calories: 520 }
];

const meal = {
  id: 3,
  description: 'Snack',
  calories: 180
};

const updatedMeals = [...meals, meal];
console.log(meals, updatedMeals);
```

---

## Updating Array - map()

```js
const numbers = [1, 2, 3];

function double(number) {
  return number * 2;
}

const doubledNumbers = numbers.map(double);

console.log(doubledNumbers); // [ 2, 4, 6 ]
```

---

## Functions

- Transform Values
- Functions are Values
  - Functions
  - Numbers
  - Strings
  - Booleans
  - Objects

```js
const PI = 3.14;
const otherPI = PI;

console.log(PI, PI === otherPI); // 3.14 true

// ** Passing functions
function add(x, y) {
  return x + y;
}

const otherAdd = add;
console.log(otherAdd(1, 2)); // 3
console.log(add, add === otherAdd); // [Function: add] true
```

---

## Updating Array - map()

```js
const meals = [
  { id: 1, description: 'Breakfast', calories: 420 },
  { id: 2, description: 'Lunch', calories: 520 }
];

const meal = {
  id: 3,
  description: 'Snack',
  calories: 180
};

const updatedMeals = [...meals, meal];

const updatedMealDes = updatedMeals.map(updatedDes);

function updatedDes(meal) {
  if (meal.id === 2) {
    return {
      ...meal,
      description: 'Early Lunch'
    };
  }
  return meal;
}

console.log(meals);
console.log(updatedMeals);
console.log(updatedMealDes);
```

---

## Removing Array - filter

```js
const meals = [
  { id: 1, description: 'Breakfast', calories: 420 },
  { id: 2, description: 'Lunch', calories: 520 }
];

const meal = {
  id: 3,
  description: 'Snack',
  calories: 180
};

const updatedMeals = [...meals, meal];

const filteredMeals = updatedMeals.filter(function(meal) {
  return meal.id !== 1;
});

console.log(meals);
console.log(updatedMeals);
console.log(filteredMeals);
```

---

## Practice

- [knowthen.com/fp5](https://jsbin.com/pumexiq/edit?js,console)
- [Solution](https://jsbin.com/nevonet/1/edit?js,console)

```js
// 1. create a constant named friends,
// which is an array that contains 2
// names of your choosing.
const friends = ['Alex', 'Clarke'];

// 2. Create a new constant named updatedFriends,
// which includes the friends array values plus
// one additional name
const updatedFriends = [...friends, 'Supergirl'];
console.log(updatedFriends);

// 3. Create a new constant named friendNameLengths,
// which is based on the array updatedFriends,
// but instead of having the friends names,
// have the array store the length of each persons name.
const friendNameLengths = updatedFriends.map(nameLengths);

function nameLengths(name) {
  return name.length;
}

console.log(friendNameLengths);

// 4. Create a new constant named shorterNamedFriends,
// which will be a list of the friends except the friend with the longest name.
const maxFriendLength = Math.max(...friendNameLengths);
console.log(maxFriendLength);

const shorterNamedFriends = updatedFriends.filter(function(name) {
  return name.length < maxFriendLength;
});
console.log(shorterNamedFriends);

// 5. Print each variable to the console.
console.log('*** *** ***');
console.log(friends, updatedFriends, friendNameLengths, shorterNamedFriends);

// Solution can be seen at:
// https://jsbin.com/nevonet/1/edit?js,console
```
