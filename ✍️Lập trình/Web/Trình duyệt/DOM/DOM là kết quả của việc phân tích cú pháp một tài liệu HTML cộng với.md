---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T14:14
---
[[Cây cú pháp trừu tượng (AST) là kết quả của việc phân tích cú pháp một tài liệu có đánh dấu]]

Nguồn:: [An Introduction to Browser Rendering - YouTube](https://youtu.be/n1cKlKM3jYI?si=5WkAsp9VgCo6V6tZ)
[[DOM property khác HTML attribute]] 
[[Nếu không có DOM, JS sẽ không có bất cứ mô hình hoặc ý niệm nào về trang web, tài liệu HTML, SVG và các thành phần khác]]

One notable difference between DOM and hast is that DOM nodes have references to their parents, meaning that `document.body.matches(':last-child')` can be evaluated to check whether the body is the last child of its parent. This information is not stored in hast, so selectors like that don’t work.
Nguồn:: [GitHub - syntax-tree/unist-util-select: utility to select unist nodes with CSS-like selectors](https://github.com/syntax-tree/unist-util-select)