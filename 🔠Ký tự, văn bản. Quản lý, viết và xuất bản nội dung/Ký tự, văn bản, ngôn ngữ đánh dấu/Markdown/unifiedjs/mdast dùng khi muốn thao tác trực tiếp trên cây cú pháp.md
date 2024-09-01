---
share: true
created: 2023-10-30T14:29
updated: 2024-08-31T20:48
---
```js title="Tạo cây cú pháp từ markdown"
import {fromMarkdown} from 'mdast-util-from-markdown'
import {toMarkdown} from 'mdast-util-to-markdown'

import {find} from 'unist-util-find'
import {gfm} from 'micromark-extension-gfm'
import {gfmFromMarkdown, gfmToMarkdown} from 'mdast-util-gfm'
import { inspect } from "unist-util-inspect";
const doc = `
// ## List 
// - One
// - Two 
## Tasklist
* [ ] to do
* [x] done
`
const tree = fromMarkdown(doc, {
  mdastExtensions: [gfmFromMarkdown()], // (1)!
  extensions: [gfm()], // (2)!
})
const node = find(tree, {type: 'list'})
console.log(inspect(node))

const out = toMarkdown(node, {extensions: [gfmToMarkdown()]})
console.log(out)
```

1. extensions for this utility to change how tokens are turned into a tree 
2. micromark extensions to change how markdown is parsed

Nguồn:: [mdast-util-from-markdown - unified](https://unifiedjs.com/explore/package/mdast-util-from-markdown/)