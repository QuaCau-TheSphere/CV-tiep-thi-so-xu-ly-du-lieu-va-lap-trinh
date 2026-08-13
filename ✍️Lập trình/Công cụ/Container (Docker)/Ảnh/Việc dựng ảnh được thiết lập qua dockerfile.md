---
share: true
created: 2023-10-24T18:26
updated: 2026-08-06T15:36
---
Nguồn:: ![Learn Docker in 7 Easy Steps - Full Beginner's Tutorial - YouTube](https://youtu.be/gAkwW2tuIqE?si=hvz8xyWfGNlOUCqr)

Ví dụ:
```docker
FROM image_cơ_sở
WORKDIR /app
COPY package.json ./
RUN npm install
COPY ./ .
EXPOSE 80
CMD lệnh_khi_image_được_chạy

```
[[Mỗi một dòng trong dockerfile sẽ tương ứng với một bước khi dựng ảnh, cũng là một ảnh tạm]]
[[Container chỉ là một tiến trình. Nó không có nhân hệ điều hành, mà lấy ở hệ điều hành gốc luôn]]. [[Ảnh là template để chạy container]] 
