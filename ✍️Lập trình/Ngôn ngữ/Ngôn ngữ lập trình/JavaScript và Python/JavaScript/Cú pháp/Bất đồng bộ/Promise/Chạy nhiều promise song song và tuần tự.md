---
share: true
updated: 2024-11-27T21:19
created: 2024-11-27T21:18
---
- If you want to run than in parallel, then we use `.map()` to kick everything off, then `Promise.all()` to gather them back up again.
- If you want to run them sequentially, create a fake Promise to start then chain. Then call `.reduce()` to run each promise run in sequence.
- 
Nguồn:: [How to run async JavaScript functions in sequence or parallel](https://jrsinclair.com/articles/2019/how-to-run-async-js-in-parallel-or-sequential/)