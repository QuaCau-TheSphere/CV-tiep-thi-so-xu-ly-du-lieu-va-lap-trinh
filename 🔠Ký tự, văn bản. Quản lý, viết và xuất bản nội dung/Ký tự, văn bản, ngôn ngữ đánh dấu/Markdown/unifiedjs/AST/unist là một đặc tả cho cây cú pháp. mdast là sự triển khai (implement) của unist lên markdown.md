---
share: true
created: 2023-10-30T14:29
updated: 2024-11-18T22:22
---
unist is not intended to be self-sufficient. Instead, it is expected that other specifications implement unist and extend it to express language specific nodes. For example, see projects such as **[hast](https://github.com/syntax-tree/hast)** (for HTML), **[nlcst](https://github.com/syntax-tree/nlcst)** (for natural language), **[mdast](https://github.com/syntax-tree/mdast)** (for Markdown), and **[xast](https://github.com/syntax-tree/xast)** (for XML).

unist relates to [JSON](https://datatracker.ietf.org/doc/html/rfc7159) in that compliant syntax trees can be expressed completely in JSON. However, unist is not limited to JSON and can be expressed in other data formats, such as [XML](https://www.w3.org/TR/xml/).

unist relates to [JavaScript](https://262.ecma-international.org/9.0/) in that it has a rich [ecosystem of utilities](https://github.com/syntax-tree/unist#list-of-utilities) for working with compliant syntax trees in JavaScript. The five most used utilities combined are downloaded thirty million times each month. However, unist is not limited to JavaScript and can be used in other programming languages.

unist relates to the [unified](https://github.com/unifiedjs/unified), [remark](https://github.com/remarkjs/remark), [rehype](https://github.com/rehypejs/rehype), and [retext](https://github.com/retextjs/retext) projects in that unist syntax trees are used throughout their ecosystems.

unist relates to the [vfile](https://github.com/vfile/vfile) project in that it accepts unist nodes for its message store, and that vfile can be a source _[file](https://github.com/syntax-tree/unist#file)_ of a syntax tree.

Trích từ:: [GitHub - syntax-tree/unist: Universal Syntax Tree used by @unifiedjs](https://github.com/syntax-tree/unist)