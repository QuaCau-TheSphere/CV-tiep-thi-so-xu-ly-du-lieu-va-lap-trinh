---
share: true
created: 2023-10-30T14:29
updated: 2026-07-06T21:41
---
Nhu cầu:: 		nc, dy, tl
Nhu cầu dẫn tới:: 		ncdt, ch, mt
Điểm mạnh:: 		đm, dm

Thành quả cần có:: 		tqcc
Thành quả hỗ trợ:: 		tqht
Thành phẩm:: 		tp, kn, xt
Giải pháp gợi ý:: 		gp

Thách thức:: 		tt, kk

Khái niệm:: 		kn
Lý do:: 		ld
Liên quan:: 		lq
Câu hỏi:: 		ch
Nguồn:: 		ng
Trích từ:: 		tt
Xem thêm:: 		xt
Tham khảo:: 		tk
# Code nhanh
## Dataview
```dataview\nLIST\nFROM |\nWHERE\n```		dtv
```dataview\nLIST rows.file.link\nFROM |\nGROUP BY split(file.folder, "/")[3]\nWHERE file.name != this.file.name\n```		dtvv
Các note cũng nói về chủ đề này:\n```dataview \nList\nWhere contains(file.name,split(this.file.name," \(")[0]) and file.path!=this.file.path\n```		cungchude

(#đct-🔥🔥Phảilàmngay or #đct-🔥/muốnlàmngay or #đct-🔥/nênlàmngay)		PNM, dct1
#đct-🍃/sớmphảilàm or #đct-🍃/đợingườinhậnlàm		cc, dct2

## Mermaid
```mermaid\ngantt\n    dateFormat  D/M H:m\n	axisFormat  %d/%m\n    title       Biểu đồ mẫu\n\n    section Phần A\n    Việc 1                 : 5/5 4:30, 3d\n    Việc 2                 : 5d \n    \n    section Phần B\n    Milestone            : milestone, 4/5 04:30\n```		mmgantt
```mermaid\nflowchart TB\n    c1-->a2\n    subgraph one\n    a1-->a2\n    end\n    subgraph two\n    b1-->b2\n    end\n    subgraph three\n    c1-->c2\n    end\n```	 		mmflowchart

[label="|"]		ll

> [!Tip] Phím tắt\n> <kbd>|</kbd>		pt

> [!Tip] Terminal\n> <kbd>|</kbd>		tm
