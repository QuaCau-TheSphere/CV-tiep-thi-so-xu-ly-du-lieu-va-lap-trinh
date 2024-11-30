---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T13:54
---
title: Processor tự động freeze khi parse, run, runSync, stringify, process, or processSync được gọi
Freeze a processor.

Frozen processors are meant to be extended and not to be configured directly.

When a processor is frozen it cannot be unfrozen. New processors working the same way can be created by calling the processor.

It’s possible to freeze processors explicitly by calling `.freeze()`. Processors freeze automatically when `.parse()`, `.run()`, `.runSync()`, `.stringify()`, `.process()`, or `.processSync()` are called.
Nguồn:: [unified - unified](https://unifiedjs.com/explore/package/unified/#processorfreeze)