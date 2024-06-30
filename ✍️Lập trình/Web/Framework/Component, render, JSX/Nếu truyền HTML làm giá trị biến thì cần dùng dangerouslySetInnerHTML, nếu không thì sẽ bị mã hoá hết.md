---
share: true
created: 2023-10-30T14:29
updated: 2024-05-12T13:26
---
Ví dụ trong `routes/test.tsx`:
```tsx
import { CSS, render } from "https://deno.land/x/gfm/mod.ts";

const markdown = `# Hello, world!`

const body = render(markdown, {
  baseUrl: "https://example.com",
});

export default function a() {
    return <main>
	    {body}
    </main>
} 
```
Thì kết quả sẽ là:

```html
<main>&lt;h1 id=&quot;hello-world&quot;>&lt;a class=&quot;anchor&quot; aria-hidden=&quot;true&quot; tabindex=&quot;-1&quot; href=&quot;#hello-world&quot;>&lt;svg class=&quot;octicon octicon-link&quot; viewbox=&quot;0 0 16 16&quot; width=&quot;16&quot; height=&quot;16&quot; aria-hidden=&quot;true&quot;>&lt;path fill-rule=&quot;evenodd&quot; d=&quot;M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z&quot;>&lt;/path>&lt;/svg>&lt;/a>Hello, world!&lt;/h1></main>
```

Nhưng nếu sử dụng:
```tsx
export default function a() {
  return (
    <main dangerouslySetInnerHTML={{ __html: body }}>
      {body}
    </main>
  );
}
```
thì kết quả trả về sẽ là:
```html
<main><h1 id="hello-world"><a class="anchor" aria-hidden="true" tabindex="-1" href="[#hello-world](view-source:http://localhost:8000/test#hello-world)"><svg class="octicon octicon-link" viewbox="0 0 16 16" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Hello, world!</h1></main>
```

Nguồn:: [dangerouslySetInnerHTML](https://tek4.vn/khoa-hoc/reactjs-tu-co-ban-den-nang-cao/dangerouslysetinnerhtml)