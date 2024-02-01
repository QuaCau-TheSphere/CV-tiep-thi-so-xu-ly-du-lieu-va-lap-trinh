---
share: true
created: 2023-10-30T14:29
updated: 2024-01-20T14:51
---
Fresh is a website framework designed to be used with Deno
Preact is essentially a reactive rendering library
Preact can be used seperately to Fresh
The relationship between Next.JS and React is the same as the relationship between Fresh and Preact 

Preact is just a rendering library and only concerns itself with getting stuff on the screen as fast as possible. It doesn't do routing or any of those other concerns an app typically needs. That's where Fresh comes in. The export default from a route file tells Fresh's file based router that this is a route that you want to use. Then when you go to a route, Fresh basically calls Preact's render() function to render the HTML, so you don't need to do that yourself when working in Fresh 

For simple sites there isn't reall much Preact specific stuff to learn other than that you can compose parts of the HTML by creating functions that return JSX like
```js
function Foo() {
  return <p>Hello world</p>
}

export default function Page() {
  return <div>
    <Foo />
  </div>
}
```
This concept alone gets you pretty far.

In my opinion there is no need to learn Preact before Fresh. That's pointless. Build a site with Fresh and you'll pick up enough Preact knowledge while doing that already

Nguồn:: [Discord](https://discord.com/channels/684898665143206084/991511118524715139/1192090620198662144)
[[Fresh dùng Preact cho UI]]