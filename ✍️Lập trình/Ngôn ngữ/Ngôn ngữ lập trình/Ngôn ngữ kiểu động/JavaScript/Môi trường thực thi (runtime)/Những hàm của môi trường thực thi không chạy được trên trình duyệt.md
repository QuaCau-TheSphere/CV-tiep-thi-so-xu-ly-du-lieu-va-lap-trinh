---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
[[Code giống như các nốt nhạc, bộ máy giống như nhạc công, còn môi trường thực thi giống như nhạc cụ|Nếu xem code giống như các nốt nhạc trên một tờ giấy, thì engine giống như nhạc công, còn môi trường thực thi giống như nhạc cụ]]. Trình duyệt là một môi trường thực thi. Node, Deno, Bun cũng là những môi trường thực thi. Nhưng [[JavaScript vốn được sinh ra để chạy trên trình duyệt và không được dùng để làm việc với lượng code lớn|JS vốn được sinh ra để chạy trên trình duyệt]], nên nó không quan tâm gì đến máy.

`Deno.readTextFile()` là một hàm của Deno cung cấp sẵn. Hàm này sẽ không chạy được trên trình duyệt. Bởi vì trình duyệt thì không biết gì về Deno, Node, v.v. Muốn dùng các hàm do các môi trường thực thi này cung cấp thì phải chạy trên server chứ không chạy trên client được. Cũng vì lý do này mà [[Các hàm được môi trường thực thi cung cấp không hoạt động được ở island]], vì [[Route là code viết cho server. Island là code viết cho client|island là code viết cho client]].

Hệ quả của việc này là bạn [[Nên tách bạch code hỗ trợ cho client và server vào những mô đun khác nhau]], vì nếu không thì sẽ dễ dùng hàm cho server khi viết island. Chỉ dùng không lẫn hàm là không đủ, mà còn phải là không lẫn file. [[Khi import một hàm thì cả file chứa hàm đó sẽ được chạy. Các import của file đó cũng sẽ chạy theo, dù là để import vào một hàm khác mình không import]]. 

[[Web API là những API được trình duyệt cung cấp, không phải của bộ máy]]
[[Runtime là lúc chạy, runtime environment là môi trường thực thi. Nhưng nhiều lúc runtime environment được gọi tắt là runtime]]
[[Trong JavaScript, khi nói đến runtime thường mọi người chỉ nghĩ đến Node hoặc Deno, và đối lập với trình duyệt. Dù tất cả đều không phải là runtime mà là runtime environment]]