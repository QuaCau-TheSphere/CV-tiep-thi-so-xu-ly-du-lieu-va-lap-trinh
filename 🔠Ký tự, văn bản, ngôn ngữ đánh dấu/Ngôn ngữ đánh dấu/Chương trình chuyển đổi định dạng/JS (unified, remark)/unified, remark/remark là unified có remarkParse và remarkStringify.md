---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
Gọi `remark` thế này
```js
const file = await remark()
  .use(remarkPresetLintConsistent)
  .use(remarkPresetLintRecommended)
  .process('1) Hello, _Jupiter_ and *Neptune*!')
```

tương đương với gọi `unified` thế này:
```js
const file = await unified()
  .use(remarkParse)
  .use(remarkStringify)
  .use(remarkPresetLintConsistent)
  .use(remarkPresetLintRecommended)
  .process('1) Hello, _Jupiter_ and *Neptune*!')
```

Nguồn:: [[Stack Overflow]], [Why can remark work independently from unified?](https://stackoverflow.com/a/78913256/3416774)