# Object Type

#### Grouped

| Meal      | Calories |
| --------- | -------- |
| Breakfast | 460      |
| Snack     | 180      |
| Lunch     | 600      |
| Snack     | 240      |
| Dinner    | 800      |

---

#### Data Structure (Object Literal) -> "Record"

| Meal      | Calories |
| --------- | -------- |
| Breakfast | 460      |

---

```js
const meal = {
  description: "Breakfast",
  calories: 180,
  date: new Date(2020, 0, 1)
};
console.log(meal.description); // Breakfast
console.log(meal.calories); // 180
console.log(meal.test); // undefined
console.log(meal.date); // 2019-12-31T17:00:00.000Z
console.log(meal.date.toString()); // Wed Jan 01 2020 00:00:00 GMT+0700 (Indochina Time)
```

---

#### Exercises

- [knowthen.com/fp2](https://jsbin.com/desugo/1/edit?js,console)
- [Answer](https://jsbin.com/cojacal/1/edit?js,console)

---

```js
// 1. create a meal object for a snack
// print both the snacks description
// and calories to the console
const meal = {
  description: "Snack",
  calories: 180
};
console.log(meal.description); // Snack
console.log(meal.calories); // 180

/*
   2. create a new constant named 
   updatedCalories, setting it to 150
   plus the calories used in the above
   meal object.
   Print the value of updatedCalories 
   to the console.
   
   Note: use the dot notation syntax as
   part of the expression
*/
const updatedCalories = meal.calories + 150;
console.log(updatedCalories); // 330

// Completed exercise at
// https://jsbin.com/cojacal/1/edit?js,console
```
