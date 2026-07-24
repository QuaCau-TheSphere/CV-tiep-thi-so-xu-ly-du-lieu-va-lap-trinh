---
share: true
created: 2023-10-30T14:29
updated: 2026-07-24T21:47
---
```typescript
/**
 * decodeURI() can't decode the `%` character, as it is used in any encoded character
 * @author [Why does decodeURIComponent('%') lock up my browser?](https://stackoverflow.com/a/54310080/3416774)
 */
export function decodeURIComponentSafe(path: string): string {
  return decodeURIComponent(path.replace(/%(?![0-9a-fA-F]+)/g, "%25"));
}
```

[GitHub - jridgewell/safe-decode-uri-component: Safely decode URI components, leaving invalid sequences as they are](https://github.com/jridgewell/safe-decode-uri-component)

Nguồn:: [Why does decodeURIComponent('%') lock up my browser?](https://stackoverflow.com/a/54310080/3416774)

[[encodeURI nên được đặt tên là fixBrokenURI, còn decodeURI nên được đặt là potentiallyBreakMyPreviouslyWorkingURI]]
[[Cách các đường dẫn ở những nơi khác nhau xử lý dấu cách và ký tự phi ASCII]]
