---
share: true
created: 2023-10-30T14:29
updated: 2025-11-17T12:36
---
Có thể trong `div` thì không được, nhưng trong `span` thì được. Nếu là CommonMark thì phải có xuống dòng chứ không được để sát:
```html
<div>

*Emphasized* text.

</div>
```

Hoặc dùng thuộc tính `markdown=1` trong thẻ HTML

Nguồn:: [How can I wrap my markdown in an HTML div? - Stack Overflow](https://stackoverflow.com/q/29368902/3416774)

[[Parser là chương trình để biến dữ liệu dạng chữ thành dữ liệu có cấu trúc]]