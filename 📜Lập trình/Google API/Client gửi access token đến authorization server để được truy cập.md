---
share: True
---
Là một đoạn mã dùng để xác thực quyền truy cập, cho phép ứng dụng bên thứ 3 có thể truy cập vào những dữ liệu của người dùng trong một phạm vi nhất định mà nó cho phép. Token này được gửi bởi **Client** như một tham số được truyền vào _hreader_ trong mỗi request khi cần truy cập đến tài nguyên trong **Resource server**.

Nếu để lộ mất _access token_ thì cũng có thể coi như bị lộ _password_ bởi có thể lợi dụng nó để lấy được những tài nguyên mà nó đang bảo vệ. Vì vậy, _access token_ có một thời gian sử dụng nhất định (2 giờ, 2 tháng...) tùy thuộc vào nhu cầu sử dụng cũng như yêu cầu về tính bảo mật. _Access token_ chỉ được sử dụng một lần duy nhất, khi nó hết hiệu lực **Client** sẽ phải gửi lại yêu cầu đến **Authorization server** để lấy một mã _access token_ mới.

Nguồn:: [[Viblo]], [Tìm hiểu đôi chút về OAuth2](https://viblo.asia/p/tim-hieu-doi-chut-ve-oauth2-eW65GvMLlDO)

[[Authorization sinh ra access token để client sử dụng]] 
[[Khi access token hết hạn truy cập, client gửi refresh token đến authorization server để được cấp access token mới]] 