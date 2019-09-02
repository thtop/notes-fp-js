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

## Exercise 1

- [knowthen.com/fp10](https://jsbin.com/zucexug/1/edit?js,output)
- Link: HTNL
  - `<script src="https://cdn.rawgit.com/knowthen/d90da7fbbcc3222252d2845eef2adc38/raw/6099003c3102daf281681cd92b7158477a1bc5f4/hyperscript-browser.js"></script>`
  - `<script src="https://cdnjs.cloudflare.com/ajax/libs/ramda/0.25.0/ramda.js"></script>`
  - `<link rel="stylesheet" href="https://unpkg.com/tachyons@4.9.0/css/tachyons.min.css"/>`

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

---

## Exercise 2

- :white_check_mark: cell
- :white_check_mark: mealRow
- :white_check_mark: headerRow
- :white_check_mark: totalRow
- :white_check_mark: mealBody
- :white_check_mark: mealHeader
- :white_check_mark: mealsTable

```js
const MEALS = [
  { description: 'Breakfast', calories: 460 },
  { description: 'Snack', calories: 180 },
  { description: 'Lunch', calories: 600 }
];

const { td, th, tr, tbody, thead, table } = tags;

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
  const rowsWithTotal = R.append(totalRow(meals), rows);
  return tbody({ className }, rowsWithTotal);
}

// Total
function totalRow(meals) {
  const total = R.pipe(
    R.map(meal => meal.calories),
    R.reduce((acc, calories) => acc + calories, 0)
  )(meals);
  return tr({ className: 'bt b' }, [
    cell(td, 'pa2 tr', 'Total:'),
    cell(td, 'pa2 tr', total)
  ]);
}

// Header
const headerRow = tr([
  cell(th, 'pa2 tl', 'Meal'),
  cell(th, 'pa2 tr', 'Calories')
]);

const mealHeader = thead(headerRow);

// Table
function mealsTable(meals) {
  return table({ className: 'mw5 center w-100 collapse' }, [
    mealHeader,
    mealsBody('', MEALS)
  ]);
}

const node = document.getElementById('app');

const view = mealsTable(MEALS);

node.appendChild(view);
```
