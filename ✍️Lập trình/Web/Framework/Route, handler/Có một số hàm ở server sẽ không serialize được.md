---
share: true
created: 2023-10-30T14:29
updated: 2024-05-20T12:08
---
Passing props to islands is supported, but only if the props are serializable. Fresh can serialize the following types of values:

- Primitive types `string`, `boolean`, `bigint`, and `null`
- Most `number`s (`Infinity`, `-Infinity`, and `NaN` are silently converted to `null`)
- Plain objects with string keys and serializable values
- Arrays containing serializable values
- Uint8Array
- JSX Elements (restricted to `props.children`)
- Preact Signals (if the inner value is serializable)

Circular references are supported. If an object or signal is referenced multiple times, it is only serialized once and the references are restored upon deserialization. Passing complex objects like `Date`, custom classes, or functions is not supported.

Trích từ:: [Interactive islands | Fresh docs](https://fresh.deno.dev/docs/concepts/islands)
[Why is a function not serializable?](https://stackoverflow.com/q/27926619/3416774)

Hệ quả là [[Route không bao giờ được gửi đến client. Island được chạy ở cả server và client]]