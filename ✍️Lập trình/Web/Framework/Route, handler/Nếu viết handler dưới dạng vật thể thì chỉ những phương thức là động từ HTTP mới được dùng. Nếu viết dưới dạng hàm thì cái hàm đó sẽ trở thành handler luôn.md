---
share: true
created: 2024-03-24T10:24
updated: 2024-08-14T21:32
---
If you pass an object, then it will only call the property with the relevant HTTP verb. If it's a function then the function is treated as the handler itself.
marvinh.: The basic explanation of what a handler is:

```tsx
const handler = {
  GET(req) {
    return new Response("hello this is GET")
  }
}

// Somewhere inside Fresh
Deno.serve(req => {
  const method = req.method;
  if (handler[method) {
    return handler[method](req)
  }

  return new Response("not found", { status: 404 })
})
 
```
marvinh.: req.body is a readable stream. Preact doesn't support rendering readable streams inside JSX, so it will be skipped during rendering
