---
share: true
created: 2023-10-30T14:29
updated: 2026-07-22T02:42
---
Khái niệm:: 
- Heartbleed would not have happened if the language used could guard against a [Buffer Over-Read](http://cwe.mitre.org/data/definitions/126.html).    
- SQL Injections might not happen if there was a [language enforced way to encode/decode HTML data](http://www.joelonsoftware.com/articles/Wrong.html)
- Sensitive data can be saved to Pagefiles [in some languages](https://stackoverflow.com/questions/728164/securely-erasing-password-in-memory-python/728237#728237) where low-level controls of [securely erasing memory](https://security.stackexchange.com/a/74281/396) aren't available.
- Pointer issues/overflows occur more often in C when compared to managed code
- [Numerical rounding errors](https://stackoverflow.com/q/916081/328397) can occur when using the developer uses the wrong datatype for the wrong data
- Denial Of Service attacks might be reduced if the app is correctly is [multi-threaded](https://stackoverflow.com/a/402944/328397)
- [Code signing](https://stackoverflow.com/q/3655263/328397) may reduce the threat of runtime security issues ([link](https://stackoverflow.com/q/2525/328397), [link](http://en.wikipedia.org/wiki/Data_Execution_Prevention))

Nguồn:: [Are there "secure" languages? (closed)](https://security.stackexchange.com/q/55723/94500)
