---
share: true
created: 2023-09-03T00:04
updated: 2023-11-10T13:13
---
Nguồn:: [10 things to avoid in docker containers | Red Hat Developer](https://developers.redhat.com/blog/2016/02/24/10-things-to-avoid-in-docker-containers)
Nếu cần lưu trữ dữ liệu, hãy dùng volume. [[Volume là cách để đồng bộ dữ liệu giữa máy chủ và máy ảo]]

Để tự động xoá container sau khi nó chạy xong, dùng `--rm` khi tạo từ image. Nếu kết hợp cờ này với `-it` và bash sẽ hữu ích cho việc debug image:
```
docker run --rm -it [IMAGE] bash
```
