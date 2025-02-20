# Cloning and transforming state

## The guideline

**Read [the guideline](https://github.com/mate-academy/js_task-guideline/blob/master/README.md) before start**

## Task description:

Write a `transformStateWithClones` function that takes a `state` object and an `actions` array,
applies each action to the previos `state` to calculate the next state,
and returns an array with states recieved after each action.

Each `action` is an object describing `state` changes. Depending on a value of its `type` property you should do the next:
- `clear` - create an empty state object;
- `addProperties` - add all `key: value` pairs given in `extraData` property to the new `state`;
- `removeProperties` - remove all keys given in the `keysToRemove` array from the `state`. (ignore not existing)

**IMPORTANT!** DON'T modify the initial `state` object in any way!

Napisz funkcję `transformStateWithClones`, która przyjmuje obiekt `state` i tablicę `actions`,
stosuje każdą akcję do poprzedniego `state`, aby obliczyć następny stan,
i zwraca tablicę ze stanami otrzymanymi po każdej akcji.

Każda `action` jest obiektem opisującym zmiany `state`. W zależności od wartości jego właściwości `type` powinieneś wykonać następujące czynności:
- `clear` - utwórz pusty obiekt state;
- `addProperties` - dodaj wszystkie pary `key:value` podane we właściwości `extraData` do nowego `state`;
- `removeProperties` - usuń wszystkie klucze podane w tablicy `keysToRemove` ze `state`. (ignoruj ​​nieistniejące)

**WAŻNE!** NIE modyfikuj w żaden sposób początkowego obiektu `state`!

Example 1:

```js
const state = {
  foo: 'bar',
  bar: 'foo',
};

const stateHistory = transformStateWithClones(state, [
  {
    type: 'addProperties',
    extraData: { name: 'Jim', hello: 'world' },
  },
  {
    type: 'removeProperties',
    keysToRemove: ['bar', 'hello'],
  },
  {
    type: 'addProperties',
    extraData: { another: 'one' },
  },
]);

console.log(stateHistory);
// [
//   { foo: 'bar', bar: 'foo', name: 'Jim', hello: 'world' },
//   { foo: 'bar', name: 'Jim' },
//   { foo: 'bar', name: 'Jim', another: 'one' },
// ]
```

Example 2:

```js
const state = {
  foo: 'bar',
  bar: 'foo',
};

const stateHistory = transformStateWithClones(state, [
  {
    type: 'addProperties',
    extraData: { yet: 'another property' },
  }
  { type: 'clear' },
  {
    type: 'addProperties',
    extraData: { foo: 'bar', name: 'Jim' },
  },
]);

console.log(stateHistory);
// [
//   { foo: 'bar', bar: 'foo', yet: 'another property' },
//   {},
//   { foo: 'bar', name: 'Jim' },
// ]
```
