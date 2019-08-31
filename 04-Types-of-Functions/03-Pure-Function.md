# Pure Function

- Pure Function
  - Creates & Returns Value Based On Input
  - No Side Effects
- Impure Function (procedure)

---

## Pure Function Rules

1. Have Input Parameters
2. No Stateful Values
3. Return based on Input
4. No Side Effects

- Code Causes Change Outside Itself
- Examples
  - Saveing something in a database
  - Writing to a file
  - Making changes to what's seen in the webapp.

```js
function add(x, y) {
  return x + y;
}

const add2 = (x, y) => x + y;
```

---

## Impure Function (procedure)

```js
let counter = 0;

function increment() {
  counter++;
}
```

---

## Why Use Pure Functions?

- Reusable
- Composable
- Easy To Test
- Easy To Cache
- More...

> Functional Programming is Eliminating State As Much As Possible And Tightly Control State When It's Needed.
