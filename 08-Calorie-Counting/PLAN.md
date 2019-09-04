# Calorie Counting App Plan / Notes

## Data Model

Example Model/Shape:

```javascript
meal = {
  id: 1,
  description: 'Breakfast',
  calories: 460
};
model = {
  meals: [],
  showForm: false,
  description: 'Dinner',
  calories: 600,
  editId: 3,
  nextId: 1
};
```

---

## View Functions

- view
  - formView
    - fieldSet
    - buttonSet
  - tableView
    - tableHeader
    - mealsBody
      - mealRow
        - cell
      - totalRow

---

## Update / Interactions

1. click add meal
2. meal input
2. calorie input
4. click save (add / update)
5. click edit icon
6. click delete icon

---

## Styles
```js
const css = {
    cssDiv: 'mw6 center',
    cssH1: 'f2 pv2 bb',
    cssLabel: 'db mb1',
    cssInput: 'pa2 input-reset ba w-100 mb2',
    cssBtnSave: 'f3 pv2 ph3 bg-blue white bn mr2 dim',
    cssBtnCancel: 'f3 pv2 ph3 bg-light-gray bn dim',
    cssForm: 'w-100 mv2',
    cssBtnAdd: 'f3 pv2 ph3 bg-blue white bn',
}

export default css;
```
