---
share: true
created: 2023-10-21T20:49
updated: 2025-03-03T18:48
---
Là một đoạn mã dùng để xác thực quyền truy cập, cho phép ứng dụng bên thứ 3 có thể truy cập vào những dữ liệu của người dùng trong một phạm vi nhất định mà nó cho phép. Token này được gửi bởi **Client** như một tham số được truyền vào _hreader_ trong mỗi request khi cần truy cập đến tài nguyên trong **Resource server**.

Nếu để lộ mất _access token_ thì cũng có thể coi như bị lộ _password_ bởi có thể lợi dụng nó để lấy được những tài nguyên mà nó đang bảo vệ. Vì vậy, _access token_ có một thời gian sử dụng nhất định (2 giờ, 2 tháng...) tùy thuộc vào nhu cầu sử dụng cũng như yêu cầu về tính bảo mật. _Access token_ chỉ được sử dụng một lần duy nhất, khi nó hết hiệu lực **Client** sẽ phải gửi lại yêu cầu đến **Authorization server** để lấy một mã _access token_ mới.

Nguồn:: [[Viblo]], [Tìm hiểu đôi chút về OAuth2](https://viblo.asia/p/tim-hieu-doi-chut-ve-oauth2-eW65GvMLlDO)

[[Client nào có thông tin xác thực thì sẽ được nhận token truy cập từ máy chủ cấp quyền]] 
[[Một token truy cập có thể truy cập được một vài API với những quyền nhất định trong một khoảng thời gian nhất định]]
[[Khi token truy cập hết hạn, client gửi refresh token đến máy chủ cấp quyền để được cấp token truy cập mới]] 
