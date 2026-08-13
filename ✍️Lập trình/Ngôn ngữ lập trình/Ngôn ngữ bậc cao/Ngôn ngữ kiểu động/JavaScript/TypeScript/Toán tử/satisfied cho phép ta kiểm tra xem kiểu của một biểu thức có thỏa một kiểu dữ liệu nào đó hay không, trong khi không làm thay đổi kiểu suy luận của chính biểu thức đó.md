---
share: true
created: 2023-10-30T14:29
updated: 2026-08-09T00:45
---
Các lập trình viên TypeScript thường gặp một tình huống khó xử: họ muốn đảm bảo rằng một biểu thức *phù hợp với một kiểu dữ liệu* nào đó, nhưng đồng thời cũng muốn *giữ lại kiểu cụ thể nhất của biểu thức đó* để phục vụ cho quá trình suy luận kiểu (type inference).

Ví dụ:
```ts
// Mỗi thuộc tính có thể là một chuỗi hoặc một bộ ba RGB.
const palette = {
    red: [255, 0, 0],
    green: "#00ff00",
    bleu: [0, 0, 255]
//  ^^^^ sai chính tả
};
// Ta muốn dùng được các phương thức của chuỗi cho 'green'...
const greenNormalized = palette.green.toUpperCase();
```

Hãy để ý rằng ta đã viết `bleu`, trong khi đáng lẽ phải là `blue`. Lỗi chính tả này có thể được phát hiện bằng cách thêm chú thích kiểu (type annotation) cho `palette`, nhưng làm như vậy sẽ khiến ta mất đi thông tin kiểu cụ thể của từng thuộc tính.

```ts
type Colors = "red" | "green" | "blue";
type RGB = [red: number, green: number, blue: number];

const palette: Record<Colors, string | RGB> = {
    red: [255, 0, 0],
    green: "#00ff00",
    bleu: [0, 0, 255]
//  ~~~~ Lỗi chính tả giờ đã được phát hiện chính xác.
};

// Nhưng giờ lại xuất hiện một lỗi không mong muốn ở đây: 'palette.green' "có thể" là kiểu RGB, nên phương thức 'toUpperCase' không tồn tại trên kiểu 'string | RGB'.
const greenNormalized = palette.green.toUpperCase();
```

Toán tử mới *`satisfies`* cho phép ta *kiểm tra xem kiểu của một biểu thức có thỏa một kiểu dữ liệu nào đó hay không trong khi không làm thay đổi kiểu suy luận của chính biểu thức đó*.

Ví dụ, ta có thể dùng `satisfies` để kiểm tra rằng tất cả các thuộc tính của `palette` đều tương thích với kiểu `string | number[]`:

```ts
type Colors = "red" | "green" | "blue";
type RGB = [red: number, green: number, blue: number];

const palette = {
    red: [255, 0, 0],
    green: "#00ff00",
    bleu: [0, 0, 255]
//  ~~~~ Lỗi chính tả giờ đã được phát hiện!
} satisfies Record<Colors, string | RGB>;

// Phương thức toUpperCase() vẫn có thể sử dụng!
const greenNormalized = palette.green.toUpperCase();
```

`satisfies` có thể được dùng để phát hiện nhiều loại lỗi khác nhau. Chẳng hạn, ta có thể đảm bảo rằng một đối tượng có *đầy đủ các thuộc tính của một kiểu nào đó và không có thuộc tính thừa*:

```ts
type Colors = "red" | "green" | "blue";

// Đảm bảo rằng đối tượng chỉ có đúng các khóa trong 'Colors'.
const favoriteColors = {
    "red": "yes",
    "green": false,
    "blue": "kinda",
    "platypus": false
//  ~~~~~~~~~~ Lỗi - "platypus" chưa từng được khai báo trong 'Colors'.
} satisfies Record<Colors, unknown>;

// Mọi thông tin về các thuộc tính 'red', 'green' và 'blue' vẫn được giữ nguyên.
const g: boolean = favoriteColors.green;
```

Đôi khi ta *không quan tâm đến việc tên các thuộc tính có khớp hay không*, mà chỉ quan tâm rằng *giá trị của từng thuộc tính* phải thuộc một kiểu dữ liệu nhất định.

Trong trường hợp đó, `satisfies` cũng có thể được dùng để đảm bảo rằng tất cả các giá trị của các thuộc tính trong một đối tượng đều tuân theo một kiểu xác định.

```ts
type RGB = [red: number, green: number, blue: number];

const palette = {
    red: [255, 0, 0],
    green: "#00ff00",
    blue: [0, 0]
    //    ~~~~~~ Lỗi!
} satisfies Record<string, string | RGB>;

// Thông tin kiểu của từng thuộc tính vẫn được giữ nguyên.
const redComponent = palette.red.at(0);
const greenNormalized = palette.green.toUpperCase();
```

Ở ví dụ trên, thuộc tính `blue` có giá trị `[0, 0]`, chỉ gồm hai phần tử thay vì ba phần tử như kiểu `RGB` yêu cầu, nên `satisfies` sẽ báo lỗi. Tuy nhiên, TypeScript vẫn giữ lại kiểu cụ thể của từng thuộc tính (`red` là tuple RGB, `green` là `string`), nhờ đó các phương thức như `.at()` hay `.toUpperCase()` vẫn được suy luận và sử dụng bình thường.

Nguồn:: [TypeScript: Documentation - TypeScript 4.9](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-9.html)
![This Amazing TypeScript Feature Has NO Docs! - YouTube](https://youtu.be/Xm_VGeTpS2Q?si=1RWFaWLnO97SL225)
[How to Use the TypeScript satisfies Operator](https://www.freecodecamp.org/news/typescript-satisfies-operator/)

[[as, is là những cách để nói cho TS biết là mình hiểu về code nhiều hơn nó]]
[[Khi dùng switch với số lượng case nhỏ, hãy dùng default với return satisfies never để đảm bảo là nếu mình có bổ sung thêm case mới thì cũng không quên xét]]
