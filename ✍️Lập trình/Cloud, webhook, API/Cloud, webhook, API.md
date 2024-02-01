---
share: true
created: 2023-11-30T22:51
updated: 2024-01-09T18:55
---

```dataview
LIST rows.file.link
FROM "Cloud, webhook, API" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```
[Launchpad Online - YouTube](https://www.youtube.com/playlist?list=PLOU2XLYxmsILOIxBRPPhgYbuSslr50KVq)
![Difference between cookies, session and tokens - YouTube](https://www.youtube.com/watch?v=GhrvZ5nUWNg)