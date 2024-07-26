---
share: true
created: 2023-09-16T13:22
updated: 2024-07-13T17:02
---
| Từ khoá | Nhãn = loại chiều = loại món đồ | Chiều | Tên nhãn |
| ---- | ---- | ---- | ---- |
| cá | Thực phẩm | Món đồ | Loại món đồ |


Chiều là nguyên cái cục.
```ts
interface KhaiBáoChiều {
    'Tên chiều': TênChiều,
    'Dữ liệu tự nhận dạng': DữLiệuTựNhậnDạng,
    'Ký tự để nhập trực tiếp'?: {Từ: string[], Nhãn: string[]},
    'Tên gọi đầu ra'?: {Từ: string, Nhãn: string}
}
```
