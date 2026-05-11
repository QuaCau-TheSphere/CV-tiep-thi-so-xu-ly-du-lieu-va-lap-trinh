---
share: true
created: 2023-09-22T14:54
updated: 2026-05-11T21:47
---
```dataview
LIST rows.file.link
FROM "🔠Ký tự, văn bản, ngôn ngữ đánh dấu/Tiếng Việt, Unicode, emoji/Lý thuyết Unicode" 
GROUP BY split(file.folder, "/")[3]
WHERE file.name != this.file.name
```

![Plain Text - Dylan Beattie - NDC Copenhagen 2022 - YouTube](https://youtu.be/gd5uJ7Nlvvo)
![Accidental Emoji Expert: Tom Scott at An Evening of Unnecessary Detail](https://youtu.be/5OPkGQoPeHk?si=Y2mZenbD8oXLf8fA) 
