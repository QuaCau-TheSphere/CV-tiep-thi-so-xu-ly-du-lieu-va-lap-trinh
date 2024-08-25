---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
Ví dụ, trong `components/component.tsx`:
```ts
export default function Component(props) {
	return <span>Giá trị của thuộc tính 1 là {props.thuộcTính1}. Giá trị của thuộc tính 2 là {props.thuộcTính2}.</span>
} 
```
([[Props là đối số đầu tiên của hàm component, dùng để truyền giá trị các thuộc tính của nó]])
Trong `routes/index.tsx`:
```ts
import Component from '../components/component.tsx'

export default function Home() {
	return <Component thuộcTính1 = 'hello' thuộcTính2 = 'world' />

// 👉 Giá trị của thuộc tính 1 là hello. Giá trị của thuộc tính 2 là world.
} 
```
Ta thấy trong `index.tsx` hàm `Component()` được dùng như thể đó là HTML.

Khi viết `components/component.tsx` thường người ta sẽ [destructuring](https://viblo.asia/p/ban-ve-js-destructuring-Eb85omNBZ2G "Bàn về JS - Destructuring") luôn `props` để vừa thấy rõ ràng trong `props` đó sẽ có những thuộc tính nào, vừa để đỡ phải viết lại nhiều lần:
```ts
export default function Component({thuộcTính1, thuộcTính2}) {
	return <span>Giá trị của thuộc tính 1 là {thuộcTính1}. Giá trị của thuộc tính 2 là {thuộcTính2}.</span>
} 
```

