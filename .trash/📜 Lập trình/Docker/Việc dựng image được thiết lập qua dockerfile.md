---
share: true
created: 2023-10-30T14:29
updated: 2023-10-30T14:30
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
[[Mỗi một dòng trong dockerfile sẽ tương ứng với một step khi dựng image]]
[[Container chỉ là một process]]. [[Image là template để chạy container]] 
