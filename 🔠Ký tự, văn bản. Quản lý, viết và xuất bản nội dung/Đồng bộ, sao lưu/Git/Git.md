---
share: true
created: 2024-01-27T13:38
updated: 2025-04-30T18:49
---
Git thật hữu dụng, nhưng với những người mới tập làm quen với Git thì sẽ thấy ngộp nếu phải nhảy ngay vào giao diện dòng lệnh. Bạn có thể dùng các chương trình giao diện đồ hoạ như SourceTree hoặc GitKraken, nhưng tuy chúng cũng đã có một bước tiến lớn về sự thân thiện, bạn vẫn có thể vẫn còn bối rối khi vẫn còn quá nhiều nút bấm, và cũng rốt cuộc không biết rốt cuộc nó hoạt động như thế nào.

Trong những nguồn tài liệu cho người mới bắt đầu, mình thấy bài thuyết trình [Git For Ages 4 And Up](https://www.youtube.com/watch?v=3m7BgIvC-uQ) là hấp dẫn hơn cả. Tác giả dùng các món đồ chơi gỗ để minh hoạ duy nhất một điều: [[Tất cả những gì Git làm chỉ để làm một việc là điều khiển các đồ thị]]. Xem xong chắc là đủ để bạn bớt bối rối khi dùng các chương trình giao diện đồ hoạ trên. Nếu bạn muốn học tiếp cách dùng ở giao diện dòng lệnh, trang [Learn Git Branching](https://learngitbranching.js.org/) sẽ cho bạn các giải thích sinh động.

![[Linux.conf.au 2013 -- Canberra, Australia - Git For Ages 4 And Up [3m7BgIvC-uQ - 963x722 - 21m44s].png]]

Đây là một số ý mà mình nghĩ sẽ giúp bạn xây dựng được mental model về Git:
- Nhiều người hay nhầm lẫn GitHub với Git là một. Thực ra chúng khác nhau. Các repo Git chỉ được lưu trên máy của bạn, còn các repo GitHub thì được lưu trên server của GitHub.  Chẳng qua là GitHub cung cấp những cách thức để bạn điều khiển cái repo được lưu trên máy của họ, **như thể bạn đang ngồi ở ngay công ty của họ để làm việc**. [[Website GitHub giống như là để teamview máy tính của GitHub|Việc bạn truy cập vào website của GitHub cũng giống như là bạn đang teamview máy họ vậy.]]
- Các commit trong Git được nối lại với nhau bằng các mã hash. Chính vì vậy nên [[có thể xem Git là một dạng xích khối]] (blockchain). Sự khác biệt nằm ở chỗ các xích khối trong tiền mã hoá được thiết kế để chúng ta có thể tin tưởng lẫn nhau, nên chúng có sẵn thuật toán đồng thuận trong đó. Nếu bạn chỉ dùng một mình thì Git với xích khối không khác gì nhau.
- [[Lệnh sứ là các lệnh dành cho người dùng. Lệnh ống nước là các lệnh lõi để dùng kèm với các lệnh Unix khác|Trong Git có hai loại lệnh: lệnh sứ (porcelain) và lệnh ống nước (plumbing).]] Cần biết rằng, [[Git được sinh ra để giải quyết nhu cầu của Linus, một người viết nhân hệ điều hành]]. Hệ điều hành mà ông này viết, Linux, có triết lý là [[Các chương trình trên Linux hướng đến việc làm tốt đúng một nhiệm vụ duy nhất, và làm tốt việc làm cùng nhau|các chương trình cần được thiết kế sao cho nó làm tốt duy nhất một nhiệm vụ, và làm tốt việc làm cùng nhau]]. Kết quả của việc này là người dùng Linux thường hay nối các lệnh lại với nhau, và kỹ thuật này được gọi là nối ống nước (pipe). Tức là các lệnh ống nước của Git là các lệnh thường hay được dùng để nối với các lệnh Linux khác. Mà mấy cái ống nước này thường bị chôn sâu trong tường, việc thay thế chúng là khó khăn. Tức là người dùng có thể tin tưởng là cho dù Git có nâng cấp phiên bản gì đi nữa thì các lệnh ống nước cũng sẽ không bị thay đổi. Còn mấy cái đồ sứ như bồn cầu, bồn rửa mặt thì dễ dùng và dễ thay đổi, nên nó để dành cho người dùng sử dụng. 

[GitHub Skills](https://skills.github.com/)


[Git Help Desk](https://jhcarl0814.github.io/ClosedAI/git/git.html)
[GitHub - initialcommit-com/git-sim: Visually simulate Git operations in your own repos with a single terminal command.](https://github.com/initialcommit-com/git-sim)

[GitHub - GitAlias/gitalias: Git alias commands for faster easier version control](https://github.com/GitAlias/gitalias)
![15 Lazygit Features In Under 15 Minutes - YouTube](https://www.youtube.com/watch?v=CPLdltN7wgE)

```dataview
LIST rows.file.link
FROM "🔠Ký tự, văn bản. Quản lý, viết và xuất bản nội dung/Đồng bộ, sao lưu/Git" 
WHERE file.name!=this.file.name
GROUP BY split(file.folder, "/")[3]
```