---
share: true
created: 2023-10-30T14:29
updated: 2024-11-24T20:58
---
```js
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(script);
  document.head.append(script);
}

loadScript('https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js', script => {
  alert(`Cool, the script ${script.src} is loaded`);
  alert( _ ); // _ is a function declared in the loaded script
});
```
Nguồn:: [Introduction: callbacks](https://javascript.info/callbacks)
