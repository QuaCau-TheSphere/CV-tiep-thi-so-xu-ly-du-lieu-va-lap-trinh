---
share: true
created: 2023-08-25T14:20
updated: 2024-11-07T12:33
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Khái niệm cơ bản và nguyên lý lập trình" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
![객체지향 프로그래밍? 문과도 이해쌉가능. 10분컷. - YouTube](https://youtu.be/cg1xvFy1JQQ)
![Fetching Title#qvdn](https://youtu.be/pTB0EiLXUC8)
