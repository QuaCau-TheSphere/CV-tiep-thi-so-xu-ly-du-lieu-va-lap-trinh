---
share: true
created: 2023-10-30T14:29
updated: 2024-03-24T20:23
---
 Fresh takes whatever you pass into ctx.render(arg) and sets it on props.data. There is no code to ensure that it is correct or anything. It just passes it along. If nothing is passed to ctx.render() then props.data will be undefined
```tsx
import { Handlers, PageProps } from "$fresh/server.ts"
export const handler: Handlers = {
	GET(req, ctx) {
        return ctx.render({req}) 
    }
}
export default function App(props: PageProps){
    return <h1>
        {props.data.req.url} 
    </h1>
} 
```
[[Route cần có ít nhất một handler hoặc một component]]. [[Props là đối số đầu tiên của hàm component, dùng để truyền giá trị các thuộc tính của nó]]