---
share: true
created: 2023-10-24T18:26
updated: 2025-10-09T12:25
---
The issue itself is that Chromium uses a lot of memory. And electron basically just runs Chromium. Except that since each Electron-based app ships its own very isolated copy of Chromium, the following problems occur:

- The operating system cannot share memory between different Electron processes. Normally if you start many processes of the same binary, the memory is shared and only copied on write. Since each Electron app is a different binary (even though they are 99% identical) they each eat memory.

- The above applies to disk size as well. Electron apps are usually huge, and 99% of the binary is the same as all your other electron apps.

This is mostly why I'm against electron. If electron worked like the JVM and each app shared a runtime, many issues would be solved, including many electron apps running old, and vulnerable versions of Chromium. Now it's only updated if the developers decide to ship a new version.

Nguồn:: [I always read about how Electron is very resource-intensive, but I'm curious as ... \| Hacker News](https://news.ycombinator.com/item?id=18733989)
[Friendly reminder: this is your RAM and this is Chrome](https://www.reddit.com/r/pcmasterrace/comments/f2tqgc/friendly_reminder_this_is_your_ram_and_this_is/)