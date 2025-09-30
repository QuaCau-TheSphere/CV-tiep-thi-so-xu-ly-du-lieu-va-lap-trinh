---
share: true
created: 2023-10-30T14:29
updated: 2025-05-03T00:20
---
Bởi vì [[Stash là một commit, có cha là commit HEAD và mẹ là commit từ index|stash cũng chỉ là commit]], mà việc apply dễ bị lộn xộn, nhất là khi muốn áp vào một nhánh khác chứ không phải nhánh được stash, nên dùng thẳng commit sẽ hợp lý hơn trong nhiều trường hợp. 

Về mặt kỹ thuật, chỉ khi nào cả 3 điều kiện sau được thoả mãn thì bạn mới nên dùng stash:
- Index rối nùi và bạn cần phải chỉnh
- Working tree rối nùi và bạn cần phải chỉnh
- Bạn không có thời gian để chỉnh và phải tắt sớm
Cần bỏ đống hiện tại khẩn cấp
Tuy nhiên, các lệnh của stash phù hợp với mental model của người dùng về những thứ chỉ được lưu tạm thời: `list`, `show`, `drop`, `pop`, `apply`, `push`, `clear`. Các lệnh của commit phù hợp hơn cho những lưu trữ cố định.

Nguồn:: [‘git stash pop’ considered harmful | Coding Killed the Cat](https://codingkilledthecat.wordpress.com/2012/04/27/git-stash-pop-considered-harmful/)
Nguồn:: [git stash - GIT stashing and switching between branches issue - work from one branch appeared on the other without merging - Stack Overflow](https://stackoverflow.com/a/64577077/3416774)