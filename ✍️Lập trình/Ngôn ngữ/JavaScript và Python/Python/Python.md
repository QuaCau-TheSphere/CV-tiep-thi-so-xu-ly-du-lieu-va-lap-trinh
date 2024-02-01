---
share: true
created: 2023-12-19T22:34
updated: 2024-02-01T21:39
---

```dataview
LIST rows.file.link
FROM "Python" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
![Transforming Code into Beautiful, Idiomatic Python - YouTube](https://youtu.be/OSGv2VnC0go?si=rFkJawTXPhVZdgXG)