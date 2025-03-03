---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T14:15
---
[[Property nghĩa gốc là tài sản. Attribute nghĩa gốc là thêm vào]] 
Nguồn:: [[MDN]], [What is the difference between properties and attributes in HTML?](https://stackoverflow.com/q/6003819/3416774)
Đây là attribute:
```html
<a href='...'
```


One notable difference between DOM and hast is that DOM nodes have references to their parents, meaning that `document.body.matches(':last-child')` can be evaluated to check whether the body is the last child of its parent. This information is not stored in hast, so selectors like that don’t work.
Nguồn:: [GitHub - syntax-tree/unist-util-select: utility to select unist nodes with CSS-like selectors](https://github.com/syntax-tree/unist-util-select)