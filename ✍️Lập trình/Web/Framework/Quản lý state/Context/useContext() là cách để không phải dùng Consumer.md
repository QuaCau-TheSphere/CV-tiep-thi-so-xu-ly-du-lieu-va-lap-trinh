---
share: true
created: 2023-10-30T14:29
updated: 2024-05-06T22:29
---
Bình thường, hàm `createContext()` sẽ cho ta dùng 2 JSX: `Provider` cho đầu vào, và `Consumer` cho đầu ra.
## Đầu vào
```jsx
import { createContext } from 'preact'

const TênContext = createContext('Alice')

export default function App() {
    return (
	    // provide the username value to our subtree:
	    <TênContext.Provider value="Bob">
		    <ComponentCon>
			    ...
			    <ComponentConCháuChắtChútChít />
			    ...
		    <ComponentCon />
	    </TênContext.Provider>
	)
}
```
## Đầu ra
```jsx
import { TênContext } from "../routes/index.tsx";

export default function ComponentConCháuChắtChútChít(){
	return (
	    <TênContext.Consumer>
			{username => (
			  // access the current username from context:
			  <span>{username}</span>
			)}
	    </TênContext.Consumer>
	)  
} 
```

Khi dùng `useContext()`, đầu ra bây giờ trông như sau:
```jsx
import { TênContext } from "../routes/index.tsx";
import { useContext } from "preact/hooks";

export default function ComponentConCháuChắtChútChít(){
	const username = useContext(TênContext)
	return <span>{username}</span>
} 
```

Việc dùng hook này không chỉ làm code ngắn hơn mà nó còn cho ta được lấy giá trị như một biến bình thường mà không phải ở trong JSX
Nó giống như việc [[await với async là cách để viết hàm bất đồng bộ với tư duy khi viết hàm tuần tự]]

Nguồn:: [Context | Preact: Fast 3kb React alternative with the same ES6 API. Components & Virtual DOM.](https://preactjs.com/tutorial/06-context/)
[[createContext() nằm ngoài global, useContext() nằm trong component]] 