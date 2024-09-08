---
share: true
created: 2023-10-30T14:29
updated: 2024-09-06T22:54
---
key-value. Triple store là key-predicate-value
It's more conducive to real work to convert triples like:
```
Anakin (this is an ID that I've elected to make quite readable, not an arbitrary stril)
  hasMentor
    Palpatine

Anakin
  AKA
    Darth Vader

Anakin
  hasName
    Anakin Skywalker
```
to something structured like
```js
{
  @id: "Anakin",
  name: [
    "Anakin Skywalker",
    "Darth Vader"
  ],
  hasMentor: {
    "@id": "Palpatine"
  },
}
```
My `AKA` and `hasName` thing is real weird but then again actual data often does have strange choices like that so just take it as realism

Nguồn:: 
[[Thế mạnh của RDF triplestore là tạo ra những liên kết mới không có sẵn lúc nhập vào]]