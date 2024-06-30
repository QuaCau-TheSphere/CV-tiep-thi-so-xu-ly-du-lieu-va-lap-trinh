---
share: true
created: 2023-11-10T13:13
updated: 2024-04-24T13:52
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Công cụ/Docker" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```

[Hết dung lượng disk do chạy Docker trong thời gian dài](https://viblo.asia/p/het-dung-luong-disk-do-chay-docker-trong-thoi-gian-dai-oK9Vyze94QR#comment-bXP4WgPr47G)

Tiếng Pháp, phụ đề tiếng Anh: [Understanding Docker in a visual way - YouTube](https://www.youtube.com/playlist?list=PLmw3X80dPdlyRV2EUKnFOvBACs_tcArd0)