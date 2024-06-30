---
share: true
created: 2023-10-30T14:29
updated: 2024-04-23T01:37
---
Rust’s rich type system is a blessing and a curse. Thinking in Rust types is a dream. Managing Rust’s types can be a nightmare. Your data and function signatures can have generic types, generic lifetimes, and trait constraints. Those constraints can have their own generic types and lifetimes. [Sometimes, you’ll have more type constraints than actual code](https://github.com/rxRust/rxRust/blob/master/src/observable.rs#L1134-L1142).

![](https://miro.medium.com/v2/resize:fit:700/1*Thd-kY7yqSu0qqDq0baV2g.png)

Constraints that outweigh logic

You also need to define all your generics on [every impl](https://github.com/bytecodealliance/wasmtime/blob/038ddfeb6699591b5d82546c9b2d5076097bc9ce/cranelift/entity/src/iter.rs#L29-L58). It’s tedious when writing it the first time. When refactoring though, it can turn a minor change into a cascading mess.

![](https://miro.medium.com/v2/resize:fit:652/1*5yX-BV9ZAoFZ-cSHOCLojg.png)

Simple generic IDs are duplicated over and over again.

It’s hard to make rapid progress when you need to tweak 14 different definitions before you can take a single step forward.

_Edit to address external comments: The problem isn’t the expressibility, the problem is no language or tooling solution to reduce the duplication. There are frequent reasons to have the same constraints or refer to the same generic lists, but there’s no way to alias or otherwise refer to a central definition. I’m not sure there should be, but it doesn’t change the burden of duplication._

Nguồn:: [Was Rust Worth It?. From JavaScript to Rust, three years… | by Jarrod Overson | Medium](https://jsoverson.medium.com/was-rust-worth-it-f43d171fb1b3)
