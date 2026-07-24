---
share: true
created: 2023-10-30T14:29
updated: 2026-07-06T21:40
---
Khái niệm:: 
The superficial answer (because the full answer probably fills thousands of research papers) is that security problems almost all come from interactions, so you'd need to trace through all possible paths through code, which runs afoul of the Halting Problem (that you can't know in advance if a program will end). For example, cross-site scripting/XSS (not really "cross-site," but that's the term) happens when a website accepts unvalidated input, doesn't sanitize it, and later uses it in a context where something (like a browser) might interpret it as code, usually separate parts of the application or separate applications sharing a database.

Sometimes it's something simple like accessing an uninitialized variable, but we stop considering those security problems, because the compiler and static-checkers warn about them as normal semantic problems.

Trích từ:: [Software Development](https://software.codidact.com/comments/thread/11869#comment-29453)

Nguồn:: [I love this. I’m in appsec and bring up the halting problem all the time to deve... \| Hacker News](https://news.ycombinator.com/item?id=39834683)
