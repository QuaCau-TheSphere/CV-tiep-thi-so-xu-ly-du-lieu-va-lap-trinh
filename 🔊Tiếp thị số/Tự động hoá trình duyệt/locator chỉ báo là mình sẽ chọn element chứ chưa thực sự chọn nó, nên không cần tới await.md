---
share: true
created: 2023-10-30T14:29
updated: 2024-11-21T16:01
---
Khi nào có việc gì phải dùng tới element thì mới chọn nó luôn. Điều này sẽ tiện nếu lúc báo element chưa xuất hiện

Nguồn:: [javascript - Page.locator() is the recommended way to select and interact with elements. Why does it offer less functionalities than Page.$()? - Stack Overflow](https://stackoverflow.com/a/79210080/3416774)


```typescript
import { Page } from "npm:puppeteer";

// Initiate
const browser = await puppeteer.launch({
headless: false,
userDataDir: "./user_data",
args: minimal_args.concat(args),
});
const page = await browser.newPage();
await page.goto("https://facebook.com/");

// Create a post
await page.locator("::-p-text(What's on your mind)").click();
await page.keyboard.type(text);

// Click the next button
const nextButtonSelector = '*[aria-label="Next"][role="button"]';
await (await page.$(nextButtonSelector))!.click(); // this works
// await page.locator(nextButtonSelector).click(); // timeout

// Click the post button
await page.locator('*[aria-label="Post"][role="button"]').click();
```