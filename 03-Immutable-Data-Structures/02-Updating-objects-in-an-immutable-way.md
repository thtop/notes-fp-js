# Updating objects, in an immutable way

- State
  - Things Apps Remember
    - Adding
    - Updating
    - Deleting
  - Maintaining Sate
- Immutable Data & State
  - Every program has state
  - State -> Date Changed / Mutated

---

## How To Make changes Object (records)

```js
const meal = {
  id: 1,
  description: 'Breakfast'
};

const updatedMeal = {
  id: meal.id,
  description: meal.description,
  calories: 600
};

console.log(meal, updatedMeal);
```

---

## Spread Operator (adding)

```js
const meal = {
  id: 1,
  description: 'Breakfast'
};

const addedCalories = {
  ...meal,
  calories: 600
};

console.log(meal, addedCalories);
```

---

## Spread Operator (updating)

```js
const meal = {
  id: 1,
  description: 'Breakfast'
};

const updatedMeal = {
  ...meal,
  description: 'Brunch', // update
  calories: 600
};

console.log(meal, updatedMeal);
```

---

## Destructuring + Rest

```js
const meal = {
  id: 1,
  description: 'Breakfast'
};

const updatedMeal = {
  ...meal,
  description: 'Brunch', // update
  calories: 600
};
console.log(meal, updatedMeal);

// ** Destructuring + Rest (deleting)

// const description = updatedMeal.description;
// const calories = updatedMeal.calories;

const { description, calories } = updatedMeal;

console.log(description, calories); // Brunch 600
```

---

## Destructuring + Rest (deleting)

```js
const meal = {
  id: 1,
  description: 'Breakfast'
};

const updatedMeal = {
  ...meal,
  description: 'Brunch', // update
  calories: 600
};
console.log(meal, updatedMeal);

// Deleting
const { id, ...mealWithoutId } = updatedMeal;

console.log(mealWithoutId);
// { description: 'Brunch', calories: 600 }
```

---

## Practice

- [knowthen.com/fp4](https://jsbin.com/sudefuc/edit?js,console)
- [solution](https://jsbin.com/sunewil/edit?js,console)

```js
const meal = {
  description: 'Dinner'
};
// 1. In an Immutable way, add a property to the
// meal called calories setting it's value to 200,
// then log the result to the console
const mealWithCalories = {
  ...meal,
  calories: 200
};
console.log(mealWithCalories);
// { description: 'Dinner', calories: 200 }

// 2. In an Immutable way, increase the calories
// by 100 and print the result to the console
const mealWithIncreasedCalories = {
  ...mealWithCalories,
  calories: mealWithCalories.calories + 100
};
console.log(mealWithIncreasedCalories);
// { description: 'Dinner', calories: 300 }

// 3. In an Immutable way, remove the calories property and log the result to the console
const { calories, ...mealWithoutCalories } = mealWithIncreasedCalories;
console.log(mealWithoutCalories); //{ description: 'Dinner' }

// See solution at: https://jsbin.com/sunewil/edit?js,console
```
