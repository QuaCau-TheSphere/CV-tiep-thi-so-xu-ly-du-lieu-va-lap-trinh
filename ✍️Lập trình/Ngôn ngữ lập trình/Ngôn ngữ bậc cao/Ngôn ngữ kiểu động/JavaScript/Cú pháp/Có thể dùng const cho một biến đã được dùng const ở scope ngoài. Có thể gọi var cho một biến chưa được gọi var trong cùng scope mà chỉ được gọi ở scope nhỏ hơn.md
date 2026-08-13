---
share: true
updated: 2026-08-13T21:38
created: 2026-08-13T21:33
---
Khái niệm:: 
JavaScript does not have a script scope, that's a term made up by Google. 

JavaScript originally had only two scopes, local and global. Local was the scope inside a function and global was the scope outside a function. Note, however, that in JS, `var` identifiers could not exist in "thin air", they always had to be attached to some kind of object. In a local scope, they were attached to the current function (which is why they are available everywhere in the function, no matter in which block they are defined), and in a global scope, they were attached to `window`. This is also why there was no block scope originally, because a block is not an object and *therefore* you couldn't attach a variable to it.

As JS evolved from a primitive website control language to a standalone programming language, which is actually correctly called ECMAScript (but the name JavaScript cannot be killed, it seems), things had to change. The first change was that the existence of `window` was no longer a requirement, since there may not even be a window object in your application. But when defining a global `var`, it still had to be attached to some object. This was the birth of `globalThis`. Note that in a global context, `this` always refers to `globalThis`, but inside an object function, it refers to the object, that's why there is `globalThis`. Also note that in a browser context, `globalThis` actually refers to the same object as `window`, but `globalThis` is always there, `window` only in a browser-based context.

Another change was that there could now be variables that were not attached to an object at all, but only to a scope. This allowed for block scoped variables, which is the third official scope of the language. You declare these variables as `let` or `const`.

But what if you create a block-scoped variable in a global context? Whether you declare a global variable with `var` or with `let`/`const` is irrelevant, in the language model they are both global variables in global scope. The only difference is that when you use `var` this variable is attached to `globalThis` and when you use `let`/`const` it isn't. When a global variable is attached to `globalThis`, Google calls it "global scope", and when it isn't, Google calls it "script scope", but that distinction doesn't exist anywhere in the language specification. Again, they are both global scope variables, just one is attached to a global object and the other one is not.

My recommendation is: just never use `var`. There is no reason why you would ever need to use it. Any code can be written to work just fine using `let` and `const`, and if you really need to attach something to `globalThis`, you can always do so explicitly by writing `globalThis.whatever = ...`. By not using `var`, there is no longer a local scope, and there is no distinction between global and script scope. You end up with only two scopes: block scope and global scope.

Nguồn:: ![If You Cannot Name All 5 JS Scopes You Need To Watch This Video - YouTube](https://www.youtube.com/watch?v=SQP9VV5b9IM)

[[Biến được tạo mà không có từ khoá khai báo (var, let, const) luôn là biến toàn cục, kể cả khi được tạo trong hàm]]