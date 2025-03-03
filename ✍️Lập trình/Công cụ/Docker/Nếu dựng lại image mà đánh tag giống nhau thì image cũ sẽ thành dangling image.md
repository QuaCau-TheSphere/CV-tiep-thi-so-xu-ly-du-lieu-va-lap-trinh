---
share: true
created: 2023-10-24T18:26
updated: 2025-03-03T18:48
---
Nguồn:: [[Viblo]], [Vì sao lại có image `<none>` sau khi build docker?](https://viblo.asia/p/vi-sao-lai-co-image-none-sau-khi-build-docker-L4x5xvBgZBM)

Nếu muốn xoá luôn chúng lúc dựng thì dùng `docker build --rm`. Để xoá hết thì dùng:
```
docker rmi $(docker images -f “dangling=true” -q)
```
