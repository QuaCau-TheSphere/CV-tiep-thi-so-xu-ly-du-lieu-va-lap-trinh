---
share: true
created: 2023-10-09T14:46
updated: 2024-07-21T13:05
title: "Có 4 loại object chính: blob, tree, commit, annotated tag"
---
[[Có thể hiểu blob là hash của một file, tree là hash của một folder, còn commit thực ra chỉ là hash của folder tổng]] 

Git sử dụng 1 database được xây dựng trên 4 objects (đối tượng) chính:

- **Blob**: key-value của file
- **Tree**: key-value của folder, trong tree chứa pointer trỏ đến tree và blob
- **Commit**: chứa pointer trỏ đến tree
- **Annotated Tag**: 1 pointer trỏ đến commit

![](https://giangtester.com/wp-content/uploads/2021/09/image-3-1024x563.png)
![](https://giangtester.com/wp-content/uploads/2021/09/image-4-1024x557.png)

- Blue là blob
- Green là tree
- Orange là commit

Git lưu **blob, tree, commit** ở đâu? —> ở folder `.git\objects` nhé
Nguồn:: [[[Bản chất của git | GiangTester Blog](https://giangtester.com/ban-chat-cua-git/) ]]

![Git Internals - Git Objects - YouTube](https://www.youtube.com/watch?v=MyvyqdQ3OjI)
