---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
```js
const obj = {
    purposeOfLife: 42,
}
Object.getOwnPropertyDescriptor(obj, 'purposeOfLife')
```
Kết quả:
```js
{
    value: 42,
    writable: true,
    enumerable: true,
    configurable: true
}
```
[Enumerability and ownership of properties - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Enumerability_and_ownership_of_properties)
Nguồn:: 