---
share: true
created: 2023-10-30T14:31
updated: 2025-03-03T18:48
alias:
  - Môi trường thực thi đối với code cũng giống như nhạc cụ đối với nốt nhạc
  - Nếu xem code giống như các nốt nhạc trên một tờ giấy, thì bộ máy giống như nhạc công, còn môi trường thực thi giống như nhạc cụ
---
Nếu như một lập trình viên là một nhạc sĩ, thì cái script họ viết ra chính là cái sheet nhạc. Một bản nhạc được phát ra khi nhạc công nhìn vào văn bản nhạc và thao tác trên nhạc cụ. Tương tự, một chương trình chạy được khi *bộ máy* đọc code trong *môi trường thực thi*. Bộ máy là thứ có thể đọc và hiểu code, còn môi trường thực thi là toàn bộ những thứ mà bộ máy dùng để tương tác với môi trường bên ngoài.

Nếu như đây là code của một chương trình:
![|300](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjW6umUr-rqk6ZG5yrJrofzju5iJL3Uy_X7YQEH7Mx2PfS3kxey6cgIKUVdLVVyDAprlND4sCFc9d5twCihMVYsGv_iN5Eqp-tt2g_Xcvhhlt1PS9tlePGUso4OMNfAVIGgIlIt5wlVOKk/s1600/Croatian+Rhapsody_0001.png)
Thì đây là chương trình đó khi nó có bộ máy (nhạc công) và môi trường thực thi (nhạc cụ):
![Maksim Mrvica - Croatian Rhapsody (LIVE) - YouTube](https://www.youtube.com/watch?v=3aTEjyzWKFQ)

Có nhiều cách thức để ta ký hiệu âm thanh xuống trang giấy, cũng như có nhiều cách thức để lưu một ý tưởng vào ổ đĩa. JavaScript là một cách để lưu ý tưởng, Python là một cách khác. Cái code mà bạn thường nghe nói tới chính là cái cách để bạn ký hiệu những ý tưởng của mình. Chúng chỉ là những ký hiệu, giống như những dòng chữ này. 

Để chạy được những ký hiệu này, chúng cần tới bộ máy, thứ có thể đọc và hiểu chúng. Có nhiều loại môi trường thực thi khác nhau cho JavaScript, và đây là những môi trường thực thi bạn thường được nghe đến: Firefox, Chrome, Safari, Opera, Edge, Node, Deno, Electron. Như bạn thấy, 5 cái đầu chính là các trình duyệt chứ chẳng phải là gì xa lạ. Còn Electron chính là cái để viết ra phiên bản desktop cho Obsidian, Notion, Slack, VS Code, Discord, Dropbox, Figma, v.v. Trừ Firefox, Safari và Edge ra, thì tất cả các môi trường thực thi còn lại đều dùng V8, một bộ máy do Google viết ra.

Node là một môi trường thực thi cho JavaScript. [[Sau một thập kỷ phát triển, tác giả của Node đã viết Deno để khắc phục những thiếu sót của Node]]. Có thể xem bài diễn thuyết [10 điều tôi hối hận về Node.js](https://www.youtube.com/watch?v=M3BM9TB-8yA "10 Things I Regret About Node.js - Ryan Dahl - JSConf EU - YouTube") của tác giả. (Tác giả không giải thích cái tên Deno có nghĩa là gì, nhưng nhiều người đoán nó là viết ngược lại của Node.)

Xem thêm:: [[Stack Overflow]], [What is the difference between JavaScript Engine and JavaScript Runtime Environment - Stack Overflow](https://stackoverflow.com/questions/29027845/what-is-the-difference-between-javascript-engine-and-javascript-runtime-environm)

[[Runtime là lúc chạy, runtime environment là môi trường thực thi. Nhưng nhiều lúc runtime environment được gọi tắt là runtime]]