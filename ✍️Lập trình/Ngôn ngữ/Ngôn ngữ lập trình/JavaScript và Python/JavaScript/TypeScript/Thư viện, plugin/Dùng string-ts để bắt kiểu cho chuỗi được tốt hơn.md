---
share: true
created: 2023-10-30T14:29
updated: 2024-03-22T16:37
---
## 😬 The problem

When you are working with literal strings, the string manipulation functions only work at the runtime level and the types don't follow those transformations. You end up losing type information and possibly having to cast the result.

```ts
const str = 'hello-world'
const result = str.replace('-', ' ') // you should use: as 'hello world'
//    ^? string
```

## 🤓 The solution

This library aims to solve this problem by providing a set of common functions that work with literal strings at both type and runtime level.

```ts
import { replace } from 'string-ts'

const str = 'hello-world'
const result = replace(str, '-', ' ')
//    ^ 'hello world'
```
Nguồn:: [GitHub - gustavoguichard/string-ts: Strongly typed string functions](https://github.com/gustavoguichard/string-ts?tab=readme-ov-file#charat)