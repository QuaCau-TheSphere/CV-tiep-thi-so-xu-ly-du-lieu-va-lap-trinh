---
share: true
created: 2023-10-30T14:29
updated: 2024-11-25T16:37
---
Kết quả là các lệnh phụ thuộc vào kết quả của tiến trình đó sẽ bị lỗi
```js
readFile("./data.txt", (error, result) => {
  // This callback will be called when the task is done, with the
  // final `error` or `result`. Any operation dependent on the
  // result must be defined within this callback.
});
// Code here is immediately executed after the `readFile` request
// is fired. It does not wait for the callback to be called, hence
// making `readFile` "asynchronous".
```

```js
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(script);
  document.head.append(script);
}

loadScript('https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js', script => {
  alert(`Cool, the script ${script.src} is loaded`);
  alert( _ ); // _ is a function declared in the loaded script
});
```

[[Chương trình là một đoạn mã được lưu trên ổ đĩa. Tiến trình là khi đoạn mã đó được nạp vào RAM và được CPU đọc]]

Chính vì như vậy, những hàm dùng để tương tác với tiến trình khác đều luôn được viết ở dạng bất đồng bộ, kể cả khi việc phiên bản đồng bộ không thay đổi gì. 

Tham khảo:
- [javascript - Why are almost all Puppeteer calls asynchronous? - Stack Overflow](https://stackoverflow.com/q/71368256/3416774)
- [Introduction: callbacks](https://javascript.info/callbacks)