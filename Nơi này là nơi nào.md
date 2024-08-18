---
share: true
created: 2023-08-25T15:39
updated: 2024-08-15T13:21
filename: index
alias:
  - Homepage
  - Trang chủ
---
## Tiếp thị số, xử lý dữ liệu và lập trình
Đây là kho thông tin bổ sung cho kho [Obsidian, quản lý dự án và công cụ nghĩ](https://obsidian.quảcầu.cc/?utm_source=Vault+C+Tiếp+thị+số%2C+xử+lý+dữ+liệu+và+lập+trình+(Trang+chủ)&utm_medium=Vault&utm_campaign=&utm_content=&utm_term=), tập trung vào việc xử lý dữ liệu và lập trình. Nó được sinh ra trong quá trình bọn mình viết [Trấn Kỳ](https://tranky.deno.dev/?utm_source=Vault+C+Tiếp+thị+số%2C+xử+lý+dữ+liệu+và+lập+trình+(Trang+chủ)&utm_medium=Vault&utm_campaign=&utm_content=&utm_term=), và cũng được sử dụng như tài liệu hướng dẫn cho nó. Nếu bạn muốn tìm một nguồn tài liệu để học một cách bài bản thì không nên vào đây. Nhưng nếu mục tiêu của bạn là làm xong những công việc khác, mà để làm được chúng trôi chảy bạn phải học lập trình, và bạn muốn tìm những bài viết thật ngắn nhưng đủ để hiểu khái niệm để còn làm việc được tiếp (như khi bọn mình cần phải học để còn viết xong Trấn Kỳ), thì có thể một số thứ trong đây sẽ hữu ích cho bạn.

> [!IMPORTANT] Những thứ được ghi lại trong đây
> - **Những khái niệm thiết yếu trong việc xây dựng mental model, đặc biệt là:**
>     - Những khái niệm cơ bản mà nếu không được giải thích thì không thể tự đoán ra được. Công việc ta cần làm đòi hỏi ta phải làm theo những hướng dẫn mặc định rằng ta đã hiểu được chúng rồi, và không cung cấp thêm lời giải thích hoặc xây dựng đủ bối cảnh để ta có thể đoán ý nghĩa của nó. Thường để hiểu được các khái niệm cơ bản này ta sẽ phải quay lại học bài bản, nhưng lúc đó việc học bài bản lại phân tán sự tập trung của ta khỏi công việc cần làm
>     - Các so sánh, ẩn dụ tới một cái gì đó dễ hiểu, dễ liên tưởng hơn
>     - Sự khác biệt, tương phản hoặc tăng tiến về cường độ của những thứ có vẻ na ná nhau hoặc mâu thuẫn nhau. Phân biệt những cái tên khác nhau cho cùng một thứ, và những thứ khác nhau có cùng một cái tên
>     - Những thuật ngữ dùng không được chuẩn xác. Có những cách dùng từ mà với người đã hiểu rồi thì sự thiếu chính xác cũng không thành vấn đề, thậm chí còn tiện lợi, nhưng người mới học thì thấy loạn (các [misnomer](https://en.wikipedia.org/wiki/Misnomer))
>     - Ý đồ thiết kế ([design rationale](https://en.wikipedia.org/wiki/Design_rationale "Design rationale - Wikipedia")) để hiểu được điểm mạnh, điểm yếu của các giải pháp khác nhau cho cùng một vấn đề, và vì sao các tác giả của chúng chấp nhận những đánh đổi đó
> - **Các lỗi thường gặp mà việc tìm hiểu đòi hỏi phải có hiểu biết sâu về vấn đề (pitfall)**
> - **Những nguồn tốt dể học một cách bài bản**
> - **Những lĩnh vực, hướng tư duy ít được để ý**
> 
> Chúng là những thứ mà bạn ước rằng ngày xưa có ai nói với mình như vậy để mình hiểu ra nhanh. Chúng thể hiện được sự vận động, chuyển động của khái niệm.

Những thứ không được ghi lại:
- Các giới thiệu chi tiết (về công cụ, ngôn ngữ, khái niệm, v.v.) đặc biệt là nếu có nguồn tốt hơn
- Những thứ bạn có thể khám phá ra về sau, mà sự khám phá đó không làm bạn nhức đầu
- Các khái niệm mà chỉ cần nhìn mặt chữ cũng có thể đoán ra được mà không cần tra cứu

Những mẹo vặt tiện lợi thì có lẽ có cái sẽ được ghi lại, có cái không.

Cách sắp xếp thư mục tuỳ vào việc lúc đó não bạn cần gì nhất. Cấu trúc cây thư mục có thể là:
- Những thứ cùng chủ đề, hoặc nếu khác chủ đề thì cũng hay liên hệ với nhau
- Những thứ người mới học hay gặp nó
- Cấu trúc phân loại học thuật 

Bài chi tiết: [Hướng dẫn đọc code cho người thấy việc biết lập trình là quan trọng nhưng không thể biến nó trở thành ưu tiên cao nhất - Obsidian, quản lý dự án và công cụ nghĩ](https://obsidian.quảcầu.cc/📐%20Dự%20án/Các%20buổi%20đáp%20ứng%20nhu%20cầu%20học%20cách%20sử%20dụng%20công%20cụ%20và%20tư%20duy%20lập%20trình%20cho%20nhu%20cầu%20công%20việc/9%20Blog/Theo%20kỹ%20thuật/Hướng%20dẫn%20đọc%20code%20cho%20người%20thấy%20việc%20biết%20lập%20trình%20là%20quan%20trọng%20nhưng%20không%20thể%20biến%20nó%20trở%20thành%20ưu%20tiên%20cao%20nhất?utm_source=Vault+C+Tiếp+thị+số%2C+xử+lý+dữ+liệu+và+lập+trình+(Trang+chủ)&utm_medium=Vault&utm_campaign=C1+Các+buổi+đáp+ứng+nhu+cầu+học+cách+sử+dụng+công+cụ+và+tư+duy+lập+trình+cho+nhu+cầu+công+việc&utm_content=&utm_term=)
