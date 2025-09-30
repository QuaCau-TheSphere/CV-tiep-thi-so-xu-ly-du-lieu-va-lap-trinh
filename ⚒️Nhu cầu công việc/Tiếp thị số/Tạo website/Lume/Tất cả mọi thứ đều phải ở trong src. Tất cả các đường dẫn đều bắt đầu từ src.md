---
share: true
created: 2023-10-30T14:29
updated: 2025-05-22T23:42
---
Mặc định `src` nằm ở `.`. Để thay đổi thì thêm cái này trong `_config.ts`:
```js
const site = lume({
  src: "./src",
});
```

Nguồn:: [The \_config file - Lume](https://lume.land/docs/configuration/config-file/#src)