---
share: true
created: 2023-10-30T14:29
updated: 2026-07-06T21:40
---
```tsx
export const Context = createContext('a')
export default function Provider({ children }) {
    const arr = ['b', 'c'] 
    return (
        <Context.Provider value={arr}> 
            {children}
        </Context.Provider>
    )
}
```
Lỗi: `Type 'string[]' is not assignable to type 'string'`
