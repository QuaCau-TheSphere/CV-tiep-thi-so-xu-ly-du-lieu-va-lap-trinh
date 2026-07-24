---
share: true
updated: 2026-07-23T20:54
created: 2026-07-23T20:53
---
```dataview
LIST rows.file.link
FROM "🛜Mạng máy tính/Giao thức/IP, DNS, DHCP"
GROUP BY split(file.folder, "/")[3]
WHERE file.name != this.file.name
```