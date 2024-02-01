---
share: true
created: 2023-10-30T14:29
updated: 2024-01-04T21:06
---
[[Khi có một yêu cầu tới một route, handler được gọi trước, sau đó tới component]]
Nếu không có handler nào thì Fresh sẽ tự động thêm một cái mặc định này:

```tsx
export const handler = {
  get(req, ctx) => ctx.render()
}
```
Fresh takes whatever you pass into ctx.render(arg) and sets it on props.data. There is no code to ensure that it is correct or anything. It just passes it along. If nothing is passed to ctx.render() then props.data will be undefined

Nguồn:: [Routes | Fresh docs](https://fresh.deno.dev/docs/concepts/routes)