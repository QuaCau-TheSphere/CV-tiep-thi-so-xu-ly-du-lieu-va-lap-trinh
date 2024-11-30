---
share: true
created: 2023-10-24T18:26
updated: 2024-11-23T14:06
---
[[Phương thức phải gắn lên một vật thể cụ thể nào đó để có tác dụng]]
[[Lớp là một cái khuôn để tạo các vật thể cho nhanh]]

```js
const obj = {
  foo() {
    this.a = 0
  },
};

console.log(obj.a); // undefined
obj.foo()
console.log(obj.a); // 0
```
