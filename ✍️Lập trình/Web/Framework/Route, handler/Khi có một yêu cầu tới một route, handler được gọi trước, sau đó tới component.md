---
share: true
created: 2023-10-30T14:29
updated: 2024-01-17T13:54
---
Handlers in Fresh are part of the routing mechanism. They are called before the component function is called. Typically they are used to pull data from a database or another API. They can be thought of as a middleware to the current route.

```jsx
export const handler = {   
	async GET(req, ctx) {     
		const data = await loadData();     // This triggers HTML rendering     
		return ctx.render(data);   
	} 
}  
export default function MyPage(props) {
	return <h1>{props.data.name}</h1> 
}
```
If no `handler` export is present, Fresh will add a default one that looks like this behind the scenes:

```js
export const handler = {   
	GET: (req, ctx) => ctx.render() 
}
```

Nguồn:: [Discord](https://discord.com/channels/684898665143206084/1192124376645124310/1192126763011158056)
