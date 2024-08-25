---
share: true
created: 2023-10-21T20:49
updated: 2024-08-18T15:05
---
Được sinh ra bởi **Authorization server**, cùng lúc với _access token_ nhưng lại khác nhau về chức năng. _Refresh token_ sẽ được gửi đi để lấy về một _access token_ mới khi nó hết hạn, cũng chính vì vậy nó có thời gian hiệu lực lâu hơn _access token_. Với _access token_ thời gian hiệu lực có thể là 2 giờ thì _refresh token_ có thể lên đến 10 giờ.

Việc có mặt của _refresh token_ giúp cho **Client** có thể lấy lại được _access token_ mà không cần phải nhận xác thực lại từ phía người dùng. Nếu người dùng đăng xuất, _refresh token_ cũng sẽ bị xóa theo.

Nguồn:: [[Viblo]], [Tìm hiểu đôi chút về OAuth2](https://viblo.asia/p/tim-hieu-doi-chut-ve-oauth2-eW65GvMLlDO)
