---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
[Why is my variable unaltered after I modify it inside of a function? - Asynchronous code reference](https://stackoverflow.com/q/23667086/3416774)
![](https://wizardzines.com/images/uploads/async-functions.png) 

Việc này và việc viết JSX giống nhau ở chỗ đó là viết cái này theo cách tư duy của cái kia.  [[JSX là cách để viết JS như thể viết HTML]]

[Why async/await is more than just syntactic sugar](https://www.zhenghao.io/posts/await-vs-promise)

---

```javascript
async function myFunc(doAwait) {
    doSomething();
    if (doAwait) {
        await doSomethingAsync();
    }

    return doSomethingElse();
}
```

Would be basically equivalent to this:

```javascript
function myFunc(doAwait) {
    doSomething();
    if (doAwait) {
        return Promise.resolve(doSomethingAsync()).then(doSomethingElse);
    }

    return Promise.resolve(doSomethingElse());
}
```

For complete equivalence, including synchronous exceptions in any of the functions calls, it would be something like this:

```javascript
function myFunc(doAwait) {
    try {
        doSomething();
        if (doAwait) {
            return Promise.resolve(doSomethingAsync()).then(doSomethingElse);
        }

        return Promise.resolve(doSomethingElse());
    } catch(e) {
        return Promise.reject(e);
    }
}
```
Trích từ:: [How do JavaScript engines convert async/await to promises under the hood? - Software Engineering Stack Exchange](https://softwareengineering.stackexchange.com/a/401900/192731)