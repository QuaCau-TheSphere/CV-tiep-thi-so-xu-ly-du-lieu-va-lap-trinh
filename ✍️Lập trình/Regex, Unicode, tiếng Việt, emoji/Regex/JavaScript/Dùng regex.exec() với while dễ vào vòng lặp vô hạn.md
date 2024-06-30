---
share: true
created: 2023-09-23T21:42
updated: 2024-04-23T01:40
---
Để tránh vào vòng lặp vô hạn, 
- Do _not_ place the regular expression literal (or [`RegExp`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) constructor) within the `while` condition — it will recreate the regex for every iteration and reset [`lastIndex`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/lastIndex).
- Be sure that the [global (`g`) flag](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions#advanced_searching_with_flags) is set, or `lastIndex` will never be advanced.
- If the regex may match zero-length characters (e.g. `/^/gm`), increase its [`lastIndex`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/lastIndex) manually each time to avoid being stuck in the same place.

Nguồn:: [[MDN]], [RegExp.prototype.exec() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec#examples "RegExp.prototype.exec() - JavaScript | MDN")
