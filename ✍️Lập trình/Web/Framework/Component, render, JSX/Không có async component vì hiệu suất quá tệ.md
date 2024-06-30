---
share: true
created: 2023-10-30T14:29
updated: 2024-05-12T13:26
---
Async route components are not really components. They are route handlers which happen to return JSX and then the JSX gets rendered. You cannot pass them to other components and instantiate them as if they were components, because they're not

Yes, initially I wanted to support that in Fresh 2, but I've made a 180 on that. They seem exciting to use until you realise that they are super bad for performance because it ties data loading to rendering which forces waterfall like loading patterns.

It's pretty bad. It encourages the wrong pattern and prevents future optimizations. In doing so the rendering is always bottlenecked by not just the slowest data request, but the sum of all fast + slow requests combined. It essentially encourages the worst case scenario for performance.

It applies to any form of async component. Async routes in Fresh are fine because they are always at the top and you can control _how_ data is loaded. This leaves open the door for future optimizations like flushing the outer HTML shell already to the client whilst some data is still loading. As soon as you introduce proper async components performance suffers. Doesn't matter where in the tree like if it's a normal component, an island or something else. Picture this: Async component A renders another async component B. Now the request needs to wait first for A to render, and only then can render B after A has completed rendering. Data loading is always the slowest path in a server response, so you basically have to add the cost of A + B. Even if the data is completely independent and could've been loaded in parallel, you cannot do it in this model

Nguồn:: [Discord](https://discord.com/channels/684898665143206084/991511118524715139/1233183397384294510)