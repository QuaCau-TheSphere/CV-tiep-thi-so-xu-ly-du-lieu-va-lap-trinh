---
share: true
created: 2023-10-30T14:29
updated: 2024-11-21T14:52
---
Nguồn:: [Một số kỹ thuật tăng tốc Puppeteer khi scraping](https://viblo.asia/p/mot-so-ky-thuat-tang-toc-puppeteer-khi-scraping-1Je5E680KnL)

# Làm sao để bấm được nút Next khi đăng bài trên Facebook?
Mình dùng Puppeteer để tự động hoá việc đăng bài và cũng làm gần xong rồi, duy chỉ có cái nút Next là nó không bấm được. Mình đoán là do lúc up hình thì nó bị disable một lúc trong lúc hình load, nhưng `locator` thì cũng có chờ chứ không phải là không. Không biết các bạn xử lý thế nào? 
```ts
import * as log from "jsr:@std/log";
import { openBrowser } from "./Puppeteer.ts";
import { Page } from "npm:puppeteer";
import { getEnv } from "./utils.ts";

export async function openBrowser(url: string) {
  log.info(`Start browser. Open ${url}`);
  const browser = await puppeteer.launch({
    headless: false,
    userDataDir: "./user_data",
  });
  const page = await browser.newPage();
  await page.goto(url);
  return page;
}

async function login(page: Page) {
  const loginSelector = "::-p-text(login)";
  const needsLogin = await page.$(loginSelector);

  if (needsLogin) {
    log.info("Login to Facebook");

    const email = getEnv("FACEBOOK_PROFILE_EMAIL");
    const password = getEnv("FACEBOOK_PROFILE_PASSWORD");

    await page.keyboard.type(email);
    page.keyboard.press("Tab");
    await page.keyboard.type(password);
    page.keyboard.press("Enter");
  }
}

async function createPost(page: Page, text: string) {
  log.info("Open post dialog");
  await page.locator("::-p-text(What's on your mind)").click();
  await page.keyboard.type(text);
}

async function uploadPhoto(page: Page, imagePaths: (string | undefined)[]) {
  if (imagePaths.length > 0) {
    log.info("Select photo button");
    await page.locator('*[aria-label="Photo/video"][role="button"]').click();
    const a = await page.$('input[accept="image/*,image/heif,image/heic,video/*,video/mp4,video/x-m4v,video/x-matroska,.mkv"]');
    await a?.uploadFile(imagePaths[0]!);
  }
}

const url = getEnv("FACEBOOK_PROFILE_URL");
const page = await openBrowser(url!);

await login(page);
await createPost(page, text);
await uploadPhoto(page, imagePaths);

log.info("Click next");

const nextButtonSelector = '*[aria-label="Next"][role="button"]';
setTimeout(() => {}, 5000);
await page.locator(nextButtonSelector).click();
// (await page.waitForSelector(nextButtonSelector, { timeout: 60000 }))?.click();
await page.locator('*[aria-label="Post"][role="button"]').click();
```