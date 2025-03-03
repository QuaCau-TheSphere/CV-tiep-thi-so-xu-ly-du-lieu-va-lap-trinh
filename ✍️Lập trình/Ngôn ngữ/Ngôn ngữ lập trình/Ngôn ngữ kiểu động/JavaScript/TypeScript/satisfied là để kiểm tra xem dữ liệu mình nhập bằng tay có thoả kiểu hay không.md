---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
```ts
type Colors = "red" | "green" | "blue";
type RGB = [red: number, green: number, blue: number];
const palette = {
	red: [255, 0, 0],
	green: "#00ff00",    
	bleu: [0, 0, 255]
//  ~~~~ The typo is now caught!
} satisfies Record<Colors, string | RGB>;
```

Nguồn:: [[freeCodeCamp]], [How to Use the TypeScript satisfies Operator](https://www.freecodecamp.org/news/typescript-satisfies-operator/)
[TypeScript: Documentation - TypeScript 4.9](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-9.html)
[[as, is là những cách để nói cho TS biết là mình hiểu nhiều hơn nó]]