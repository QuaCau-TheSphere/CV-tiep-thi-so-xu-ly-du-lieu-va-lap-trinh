---
share: true
created: 2023-10-24T18:26
updated: 2024-08-26T15:42
---
```dataview
LIST rows.file.link
WHERE contains(nguồn, "stackoverflow.com")
GROUP BY file.folder
```