# Immutable Data

- What Is Immutable Data?
  - Data that Never Changges once it's been created
  - Good idea to avoid mutating data
  - Data that doesn't change is simple
  - Less complicated code
  - Fewer bugs
  - Easier to
    - understand
    - test
    - maintain

```js
const PI = 3.14;
//PI = 3.145; // Assignment to constant variable.

const meal = {
  description: 'Breakfast',
  calories: 440
};

// JavaScript doesn't care if we modify the object
meal.calories = 600;
console.log(meal.calories); // 600
```

- The `const` keyword prevents reassignment of a value to a constant.
