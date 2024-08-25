---
share: true
created: 2023-12-19T22:34
updated: 2024-08-18T15:05
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Ngôn ngữ/Ngôn ngữ lập trình/JavaScript và Python/Python" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[5]
```
![Transforming Code into Beautiful, Idiomatic Python - YouTube](https://youtu.be/OSGv2VnC0go?si=rFkJawTXPhVZdgXG)