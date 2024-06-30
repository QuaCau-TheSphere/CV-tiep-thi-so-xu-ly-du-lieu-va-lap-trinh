---
share: true
created: 2023-10-30T14:29
updated: 2024-05-10T20:47
---
I suggest reading the caveats [in the documentation](https://react.dev/reference/react/useState#usestate). An unconditional state setter call in a component function is always a bad idea, whether with a string or something else, and it isn't _always_ guaranteed React won't call the component function again as a result, even when you call it with the same value, though it usually won't.
```js
console.log("a" === "a");
console.log({ x : "a" }  === { x : "a"}); //Why is this false when above is true
```

```javascript
setState(prev => {
  if (prev.keyOne === true && prev.keyTwo === 'someKey')  {
    return prev; // Same object, so render is skipped
  } else {
    return { keyOne: true, keyTwo: 'someKey' };
  }
});
```

If you have some favorite library for checking deep equality (Eg, [lodash](https://lodash.com/docs/4.17.15#isEqual) or [ramda](https://ramdajs.com/docs/#equals)), you could shorten it to something like the following. This will be particularly useful if there are a lot of properties you would otherwise need to check:

```javascript
setState(prev => {
  const next = { keyOne: true, keyTwo: 'someKey' };
  return R.equals(prev, next) ? prev : next;
});
```
Nguồn:: [Why is React rerendering the component when the states are the same?](https://stackoverflow.com/a/73808292/3416774)