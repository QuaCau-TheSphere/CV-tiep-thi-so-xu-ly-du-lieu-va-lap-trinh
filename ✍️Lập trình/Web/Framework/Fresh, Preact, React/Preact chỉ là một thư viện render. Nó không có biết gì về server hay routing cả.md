---
share: true
created: 2023-10-30T14:29
updated: 2024-01-25T19:12
---
One important thing to remember: **Preact is just a rendering library and only concerns itself with getting stuff on the screen as fast as possible.**

The consequences of this are:

- Preact doesn't do routing or any of those other concerns an app typically needs
- Preact has no idea of a server and has no concept of how to pass data from the server to the client

That's where Fresh comes in:

- The export default from a route file tells Fresh's file based router that this is a route that you want to use. Then when you go to a route, Fresh basically calls Preact's render() function to render the HTML, so you don't need to do that yourself when working in Fresh
- Fresh introduces the notion of Server and a Client that Preact isn't aware of

What Fresh gives you compared to using Preact alone is:

- routing automatic
- bundling of islands and the machinery to make them interactive on page load (remember Preact is just a JS lib not a build tool)
- a serialization layer that supports preact signals to transfer island props to the browser
- an API layer
- dev stuff like reloading the page when a component changes
- a server in general

All in all Fresh is a somewhat minimal wrapper around Preact. It's a similar relationship as Next.js has with React.

Nguồn:: [fresh/docs/latest/concepts/jsx-and-preact.md at ddff9a6324be4d35dd6065f3503c5d5b42a1b574 · denoland/fresh · GitHub](https://github.com/denoland/fresh/blob/ddff9a6324be4d35dd6065f3503c5d5b42a1b574/docs/latest/concepts/jsx-and-preact.md)

[[Render là quá trình chuyển đổi dữ liệu và code sang HTML]]