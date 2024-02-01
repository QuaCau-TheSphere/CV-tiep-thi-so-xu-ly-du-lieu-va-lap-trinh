---
share: true
created: 2023-10-30T14:29
updated: 2024-01-15T23:28
---
Khi phải dùng Consumer:
```jsx
import { createContext } from 'preact'

const Username = createContext()

export default function App() {
  return (
    // provide the username value to our subtree:
    <Username.Provider value="Bob">
	  <Username.Consumer>
		{username => (
		  // access the current username from context:
		  <span>{username}</span>
		)}
	  </Username.Consumer>
    </Username.Provider>
  )
}
```

Khi dùng `useContext()`:
```jsx
import { createContext } from 'preact'
import { useContext } from 'preact/hooks'

const Username = createContext()

export default function App() {
  const username = useContext(Username) // "Bob"
  return (
    <Username.Provider value="Bob">
	  <span>{username}</span>
    </Username.Provider>
  )
}
```
Nguồn:: [Context | Preact: Fast 3kb React alternative with the same ES6 API. Components & Virtual DOM.](https://preactjs.com/tutorial/06-context/)
[[createContext() nằm ngoài global, useContext() nằm trong component]] 