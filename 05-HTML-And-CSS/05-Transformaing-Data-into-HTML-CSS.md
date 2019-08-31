# Tranforming Data into HTML and CSS

## What function to create?

- Single Responsibility Principle
- Each Function Does 1 Thing

---

## Plan / Function to Create

- :white_check_mark: cell
- :white_check_mark: mealRow
- :black_square_button: headerRow
- :black_square_button: totalRow
- :white_check_mark: mealBody
- :black_square_button: mealHeader
- :black_square_button: mealsTable

---

## Exercise

- [knowthen.com/fp10](https://jsbin.com/zucexug/1/edit?js,output)

```js
const MEALS = [
  { description: 'Breakfast', calories: 460 },
  { description: 'Snack', calories: 180 },
  { description: 'Lunch', calories: 600 }
];

const { td, th, tr, tbody } = tags;

function cell(tag, className, value) {
  return tag({ className }, value);
}

function mealRow(className, meal) {
  return tr({ className }, [
    cell(td, 'pa2', meal.description),
    cell(td, 'pa2 tr', meal.calories)
  ]);
}

function mealsBody(className, meals) {
  const rows = R.map(R.partial(mealRow, ['stripe-dark']), meals);
  return tbody({ className }, rows);
}

const node = document.getElementById('app');

const view = mealsBody('', MEALS);

node.appendChild(view);
```
