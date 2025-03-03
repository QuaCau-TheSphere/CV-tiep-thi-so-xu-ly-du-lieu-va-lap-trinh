---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
## `args`
```js
console.log(args)
{
  steps: [],
  currentEntities: [
    {
      'Số tiền mỗi kỳ': 400000,
      'Created By': { Name: 'Quả Cầu', Id: 'a3a22e29-e2df-4cf4-a3ae-525c38cff2ad' },
      'Public Id': '1',
      Id: 'fc9fa60e-ca46-412c-b7cf-501edeb063fd',
      'Các lần thiết lập phí': '2025-02-01: quý, 300000\n2025-04-01: năm, 300000\n',
      'Creation Date': '2025-01-29T03:58:08.738Z',
      'Modification Date': '2025-02-02T05:56:11.327Z',
      Rank: 2722894683359780,
      Name: 'A sensational sample entity 🎈',
      Description: {
        Secret: '48a3c000-1af8-4e4e-9316-eb85b590402b',
        Id: '499a3077-2c5c-454e-b045-691da9929419'
      },
      'Chu kỳ': { Name: 'Năm', Id: '7ca663a0-ddf5-11ef-94da-85a334dec488' },
      'Tổng phí': 30000000,
      Type: 'Định kỳ đóng phí/Hợp đồng'
    }
  ],
  currentUser: {
    'Public Id': '1',
    Id: 'a3a22e29-e2df-4cf4-a3ae-525c38cff2ad',
    Email: 'quacau.thesphere@gmail.com',
    'Active?': true,
    'Admin?': true,
    'Creation Date': '2024-04-19T08:23:53.707Z',
    'Guest?': false,
    'Modification Date': '2025-02-01T14:24:07.234Z',
    Rank: 7617515970756159,
    Name: 'Quả Cầu',
    Role: 'role/admin',
    'Ui Preferences': {},
    Type: 'fibery/user'
  }
}
```

`arg` cung cấp `currentEntities` chứ không phải `currentEntity` vì có trường hợp người dùng nhập nhiều dữ liệu cùng lúc. Chính vì như vậy nên trong script mẫu mới phải dùng `for`:
```js
for (const entity of args.currentEntities) {
}
```

## `context`
Chứa duy nhất phương thức `getService()` để lấy một trong ba dịch vụ: `fibery`, `http`, `utils`.

- `fibery` dùng để  service to perform some operations on your Fibery workspace.
  ```js
  const fibery = context.getService("fibery");
  ```
- `http` to make arbitrary requests on the web.
  ```js
  const http = context.getService("http");
  ```
- `utils` cung cấp những công cụ hỗ trợ thường dùng