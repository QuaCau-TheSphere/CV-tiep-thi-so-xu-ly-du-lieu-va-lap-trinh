---
share: true
created: 2023-10-30T14:29
updated: 2024-11-30T13:45
---
Auto-waiting or not is irrelevant to whether you need to use `await`. `await` is used whenever there's a network call, a system call, or inter-process communication that needs to talk to another process or the operating system. Node is single-threaded, so for it to operate efficiently, it uses asynchronous code constructs like promises to allow it to perform other tasks while the network call is in flight.

Since the browser you're automating with Puppeteer is a separate process from Node, any CDP call is asynchronous, regardless of whether the call involves waiting for a condition or not. So the only calls that don't need `await` are ones that don't involve CDP calls, like `page.locator()`. Don't mix up the words "wait" and "await"--totally different here! See [Why are almost all Puppeteer calls asynchronous?](https://stackoverflow.com/questions/71368256/why-are-almost-all-puppeteer-calls-asynchronous) for details.

Nguồn:: [javascript - Page.locator() is the recommended way to select and interact with elements. Why does it offer less functionalities than Page.$()? - Stack Overflow](https://stackoverflow.com/a/79210080/3416774)

[[await với async là cách để viết hàm bất đồng bộ với tư duy khi viết hàm tuần tự]]