---
share: true
created: 2023-10-30T14:29
updated: 2024-06-22T01:37
---
Mô tả vấn đề: có nhiều loại thông tin không phải lúc nào cũng được ghi, và không phải cứ thay đổi là khác nhau. VD: cùng một bài đăng, nhưng URL có thể đã thay đổi khi đổi đường dẫn, tiêu đề có thể đã được viết lại, nội dung có thể đã được cập nhật, vault và dự án có thể đã được cấu trúc lại. Tất cả mọi thứ đều có thể đã khác, nhưng ta vẫn xem chúng là giống nhau. Đây là nghịch lý con tàu Theseus điển hình.
 
Hàm này sẽ xác định sự giống nhau dựa vào các tiêu chí chính và các tiêu chí phụ.

Các tiêu chí chính: tiêu đề, URL, mô tả bài đăng, và toàn bộ nội dung bài đăng. Đây là các thành phần bắt buộc phải có khi viết bài. Chỉ cần trùng một trong 4 tiêu chí này thì mặc định là bài đăng giống nhau. Nhưng nếu không trùng hết tất cả thì cũng chưa chắc là khác nhau.

Nếu khác định dạng bài đăng (VD một cái là markdown, một cái là HTML) thì mặc định là bài đăng khác nhau.

Nếu các tiêu chí chính đều khác nhau và cùng định dạng bài đăng thì bắt đầu xét tới các tiêu chí phụ: Vault, id, mã bài đăng, tên dự án, mã dự án. Chúng là những thông tin thường hay bị bỏ qua khi viết. Tuy nhiên, chúng lại có đặc điểm là ít bị thay đổi hơn là các tiêu chí chính. Nếu có quá nửa số tiêu chí phụ khác nhau thì xét là bài đăng khác nhau. Còn không thì xét là giống nhau.