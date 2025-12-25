---
share: true
created: 2023-10-30T14:29
updated: 2025-10-11T10:07
---
Nếu tệp được thay đổi cùng lúc trên hai thiết bị và nội dung có sự khác biệt, tệp có thời điểm chỉnh sửa cũ hơn sẽ được xem là gây xung đột và được đổi tên thành `<filename>.sync-conflict-<date>-<time>-<modifiedBy>.<ext>`. 
Nếu có cùng thời điểm chỉnh sửa thì tệp ở trên thiết bị có ID lớn hơn sẽ được xem là gây xung đột.

If the conflict is between a modification and a deletion of the file, the modified file always wins and is resurrected without renaming on the device where it was deleted.

Nguồn:: https://docs.syncthing.net/users/syncing.html