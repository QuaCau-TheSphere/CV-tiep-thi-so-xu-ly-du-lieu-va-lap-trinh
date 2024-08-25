---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
Lý do:: [[Phải viết hook trong component. Không viết trong loop hoặc if được]]
[[Giá trị trả về của useContext() là giá trị được truyền vào thuộc tính value của provider]]
```jsx
import { createContext } from 'preact'
import { useContext } from 'preact/hooks'

const TênContext = createContext()

export default function App() {
  return (
    <TênContext.Provider value={giáTrịĐượcTruyềnVàoProvider}>
	  <User />
    </TênContext.Provider>
  )
}

function User() {
  const username = useContext(TênContext) // Nếu giáTrịĐượcTruyềnVàoProvider = 'Bob' thì username = 'Bob'
  return <>{username}</>
}
```

Ví dụ:
```tsx
export const TênContext = createContext('sdf') 

export default function CấuHìnhProvider({ children }) {
    return (
        <ContextCấuHình.Provider value={giáTrịĐượcTruyềnVàoProvider} >
            {children} 
        </ContextCấuHình.Provider>
    )
} 

function Component(){
  const [giáTrịĐượcTruyềnVàoProvider] = useContext(TênContext)
} 
```
[Context – Preact Tutorial](https://preactjs.com/tutorial/06-context/)