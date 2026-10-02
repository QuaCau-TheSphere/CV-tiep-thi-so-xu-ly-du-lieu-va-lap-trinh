---
share: true
updated: 2026-08-27T20:27
created: 2026-07-19T22:35
---
Khái niệm:: 
[Programming paradigm - Wikipedia](https://en.wikipedia.org/wiki/Programming_paradigm)
```dataview
LIST rows.file.link
FROM "✍️Lập trình/Khái niệm cơ bản/Hệ hình lập trình" 
GROUP BY split(file.folder, "/")[3]
WHERE file.name != this.file.name
```