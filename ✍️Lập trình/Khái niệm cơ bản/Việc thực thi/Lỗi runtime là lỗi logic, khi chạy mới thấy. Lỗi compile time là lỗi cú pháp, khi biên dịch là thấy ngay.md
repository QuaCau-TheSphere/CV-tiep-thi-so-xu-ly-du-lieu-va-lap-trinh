---
share: true
created: 2023-10-30T14:29
updated: 2026-08-10T16:08
---
Nguồn:: [câu hỏi thắc mắc về run time , compile time và translation time - programming - Dạy Nhau Học](https://daynhauhoc.com/t/cau-hoi-thac-mac-ve-run-time-compile-time-va-translation-time/5686)

![](https://www.monkeyuser.com/2017/compile-vs-runtime-error/70-runtime-vs-compile-time-errors.png)
[[Vì lỗi compile time là lỗi cú pháp, và vì language server giúp bắt lỗi cú pháp, nên nó khiến cho code editor trở thành IDE mà không cần có compiler]]

[Can all compiler errors be caught by language server?](https://software.codidact.com/posts/296487)
One example is an assignment to a variable where the expression is a symbol. When that symbol is the name of a variable of the correct type, then that's fine. If the symbol is something that doesn't result in an expression or an expression of the wrong type (depending on language), then it's a compile-time error. However, it is still _syntactically_ correct.