---
share: true
created: 2023-10-30T14:29
updated: 2024-11-18T20:26
---
```js
const obj = {
  foo() {
    return 'bar';
  },
};

console.log(obj.foo());
	// Expected output: "bar"
```
Cách viết khác:
```js
const obj = {
  foo: function () {
    // …
  },
  bar: function () {
    // …
  },
};

```
[Method - MDN Web Docs Glossary: Definitions of Web-related terms | MDN](https://developer.mozilla.org/en-US/docs/Glossary/Method)
Nguồn:: [Method definitions - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions)