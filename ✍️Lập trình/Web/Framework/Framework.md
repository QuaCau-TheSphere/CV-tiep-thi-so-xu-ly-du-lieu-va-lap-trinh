---
share: true
created: 2024-01-12T17:36
updated: 2024-04-27T12:47
---

```dataview
LIST rows.file.link
FROM "✍️Lập trình/Web/Framework" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```

![Every React Concept Explained in 12 Minutes - YouTube](https://www.youtube.com/watch?v=wIyHSOugGGw)