---
share: true
created: 2023-10-30T14:29
updated: 2023-10-30T14:30
---
Nguồn:: [[Viblo]], [Vì sao lại có image `<none>` sau khi build docker?](https://viblo.asia/p/vi-sao-lai-co-image-none-sau-khi-build-docker-L4x5xvBgZBM)

Nếu muốn xoá luôn chúng lúc dựng thì dùng `docker build --rm`. Để xoá hết thì dùng:
```
docker rmi $(docker images -f “dangling=true” -q)
```
