---
share: true
created: 2023-10-24T18:26
updated: 2024-08-18T15:05
---
Function Nesting Use Cases _(mostly functional idioms, almost certainly incomplete since it's off the top of my head)_:

- closures
- function factory (programmatic function creation based on parameters)
- creating functions by calling functool.partial
- creating functions by using lambda
- any other reasons you need to create functions during call time

Trade-offs:

- functions are strongly coupled
- the code is always called (unless it's in an if block)
- additional code complexity
- additional runtime cost _(potentially, because the inner function get's re-defined with every call to the outer function)_
- much harder to extend
- much harder to introspect on the inner function defintion

Nguồn:: [[✍️Lập trình/Ξ Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [When to use python function nesting?](https://softwareengineering.stackexchange.com/a/237944/192731)
