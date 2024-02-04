---
share: true
created: 2024-01-02T15:35
updated: 2024-02-01T21:39
---
![Rust và Data Engineering? 🤔](https://blog.duyet.net/2021/11/rust-data-engineering.html)
![Why You SHOULDN'T Learn Rust - YouTube](https://youtu.be/kOFWIvNowXo?si=sdHbK6t97OiMDpxb)
![Why You SHOULD Learn Rust - YouTube](https://youtu.be/h-hdFwze-0U?si=3HP3HIMmQDJnA9T4)
```dataview
LIST rows.file.link
FROM "Rust" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[2]
```