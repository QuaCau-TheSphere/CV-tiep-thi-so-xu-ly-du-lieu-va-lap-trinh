---
share: true
created: 2023-10-30T14:29
updated: 2024-03-22T16:37
---

> [!attention] Chỉ dùng cho app, không dùng trên thư viện
> `ts-reset` is designed to be used in application code, not library code. Each rule you include will make changes to the global scope. That means that, simply by importing your library, your user will be unknowingly opting in to `ts-reset`.

[Links to why typescript chose to opt in for these weird quirks · total-typescript/ts-reset · Discussion #129 · GitHub](https://github.com/total-typescript/ts-reset/discussions/129)

Nguồn:: [TS Reset - Official Docs | Total TypeScript](https://www.totaltypescript.com/ts-reset)