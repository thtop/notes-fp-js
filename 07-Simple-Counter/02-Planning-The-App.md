# Planning The App

- Functional Building Blocks
  - (Imputable) Data
  - and (Pure) Functions

## Counter App

- Data?
  - Number (count)
- Functions?
  - View

> Use Pure Functions Almost Exclusively
> Eliminate Side Effects & Controlling Side Effects

---

## Counter Code

```js
import createElement from 'virtual-dom/create-element';
import { h, diff, patch } from 'virtual-dom';
import hh from 'hyperscript-helpers';

const { div, button } = hh(h);

const initModel = 0;

// VIEW
function view(dispatch, model) {
  return div([
    div({ className: 'mr2' }, `Count: ${model}`),
    button(
      { className: 'pv1 ph2 mr2', onclick: () => dispatch(MESG.ADD) },
      '+'
    ),
    button(
      { className: 'pv1 ph2', onclick: () => dispatch(MESG.SUBTRACT) },
      '-'
    )
  ]);
}

const MESG = {
  ADD: 'ADD',
  SUBTRACT: 'SUBTRACT'
};

// UPDATE
function update(msg, model) {
  switch (msg) {
    case MESG.ADD:
      return model + 1;
    case MESG.SUBTRACT:
      return model - 1;
    default:
      return model;
  }
}

// APP
function app(initModel, update, view, node) {
  let model = initModel;
  let currentView = view(dispatch, model);
  let rootNode = createElement(currentView);
  node.appendChild(rootNode);

  function dispatch(msg) {
    model = update(msg, model);
    const updatedView = view(dispatch, model);
    const patches = diff(currentView, updatedView);
    rootNode = patch(rootNode, patches);
    currentView = updatedView;
  }
}

const rootNode = document.getElementById('app');
app(initModel, update, view, rootNode);

```
