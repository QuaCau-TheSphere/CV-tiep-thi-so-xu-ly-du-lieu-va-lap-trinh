---
share: true
created: 2023-10-30T14:29
updated: 2024-04-11T15:59
---
Following up on this, there's also an intermediate approach if you use the `react-hook-form` library which is based on uncontrolled components, but does require state (being an island) due to its `useForm()` hook helper. So in this sense, we could say there's 3 approaches to forms: `uncontrolled -> uncontrolled+state -> stateful`. As Marvin says, I agree that one should always start with `uncontrolled` forms using only HTML. However, there might be cases when you need a bit more control, and that's where the middleground (`uncontrolled+state`) with a library like `react-hook-form` might come into play. For example, in my case, I needed to use PATCH/PUT to interact with my RESTful API and the native HTML `<form>` element only supports GET/POST, so I had to had an onSubmit handler (in an island), in which case you might as well use the `react-hook-form` wrapper which provides some nice features while keeping things uncontrolled👍.

In general, forms have been sort of a pain to deal with (primarily since `<form>` does not support all HTTP methods (for REST APIs), this lead to me prototyping an isomorphic `<FormFetch />` component (check out [the gist](https://gist.github.com/miguelrk/d3ffc311627586d3459fcc75fd7512e7 "the gist
(https://gist.github.com/miguelrk/d3ffc311627586d3459fcc75fd7512e7)")), it's not an island, since client-side code is inlined in a `<script>` tag) which augments the HTML-native `<form>` to allow e.g.

```tsx
<FormFetch id="users.patch" action={`/api/users/${user.id}`} method="patch">
```

by preventing the form's default `submit` event handler, and making a `fetch` request instead (thus no dependencies. 

This worked marvelously. @marvinh. would a built-in component like this e.g. `<Form />` (similar to e.g. `<Head >`) be interesting for fresh? This could be used as a component, no need to place it within an island, so ergonomics are I think great, and it relies only on HTML/Web APIs... In general, this could complement the incoming partials-based improvements for forms in fresh

Nguồn:: [Discord](https://discord.com/channels/684898665143206084/991511118524715139/1227505709391024198)