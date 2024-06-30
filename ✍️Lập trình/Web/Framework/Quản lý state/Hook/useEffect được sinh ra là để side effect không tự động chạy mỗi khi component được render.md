---
share: true
created: 2023-10-30T14:29
updated: 2024-05-10T23:17
---

`side-effect` có thể hiểu là một khái niệm miêu tả các tính toán bên trong một hàm ảnh hưởng đến các đối tượng bên ngoài không thông qua đối số. Mình cho một ví dụ như thế này

```jsx
let a = 10;

function calculate() {
 a++;
}

// Lúc này a sẽ bằng 11 chứ không phải bằng 10 
// Khi hàm cal() được invoke, nó đã tác động đến biến bằng cách + lên 1 đơn vị mà không thông qua cách truyền tham số
// Đây tạm gọi là side-effect
calculate(); // a = 11; 
```

Trích từ:: [Tìm hiểu về React hook useEffect - Codestus.com](https://codestus.com/posts/tim-hieu-ve-react-hook-useeffect)

---

Một component React sử dụng các props và/hoặc state để tính toán kết quả đầu ra. **Nếu component thực hiện các tính toán không nhắm mục đích là giá trị đầu ra, thì các tính toán này được đặt tên là side effect**.

Ví dụ về các `side effect` là lấy data, thao tác DOM trực tiếp, sử dụng các hàm hẹn giờ như setTimeout (), v.v.

**Component rendering và logic của `side effect` là độc lập. Sẽ là một sai lầm nếu thực hiện các `side effect` trực tiếp trong phần thân của Component , vốn chủ yếu được sử dụng để tính toán kết quả đầu ra**.

Tần suất hiển thị của component không phải là điều bạn có thể kiểm soát - nếu React muốn hiển thị component, bạn không thể dừng nó.  

```js
function Greet({ name }) {
  const message = `Hello, ${name}!`; // Calculates output
  // Bad!
  document.title = `Greetings to ${name}`; // Side-effect!
  return <div>{message}</div>;       // Calculates output
}
```

Làm thế nào để tách rendering khỏi `side effect`? Hãy dùng  
`useEffect()` - hook chạy các `side effect` độc lập với việc rendering.  

```jsx
import { useEffect } from 'react';
function Greet({ name }) {
  const message = `Hello, ${name}!`;   // Calculates output
  useEffect(() => {
    // Good!
    document.title = `Greetings to ${name}`; // Side-effect!
  }, [name]);
  return <div>{message}</div>;         // Calculates output
}
```

`useEffect()` hook chấp nhận 2 đối số: `useEffect(callback[, dependencies]);`
- `callback` là hàm chứa logic của `side effect`. `callback` được thực thi ngay sau khi các thay đổi được đẩy vào DOM.
- `dependencies` là một mảng tùy chọn của các `dependencies` . `useEffect()` chỉ thực thi lệnh gọi lại nếu các `dependencies` thay đổi giữa các lần hiển thị.

> Đặt logic của side effect vào hàm callback, sau đó sử dụng đối số dependencies để kiểm soát thời điểm bạn muốn side effect chạy. Đó là mục đích duy nhất của useEffect().

[![Image 1](https://res.cloudinary.com/practicaldev/image/fetch/s--NH2FkXJU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/22swjdpn18jt1w900zsn.PNG)](https://res.cloudinary.com/practicaldev/image/fetch/s--NH2FkXJU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/22swjdpn18jt1w900zsn.PNG)

Ví dụ: trong đoạn code trước đó, bạn đã thấy `useEffect()` đang hoạt động:  

```jsx
useEffect(() => {
  document.title = `Greetings to ${name}`;
}, [name]);
```

Cập nhật tiêu đề document là `side effect` vì nó không trực tiếp tính toán kết quả đầu ra của component. Đó là lý do tại sao cập nhật tiêu đề document được đặt trong một hàm callback và được cung cấp cho `useEffect()`.

Ngoài ra, bạn không muốn bản cập nhật tiêu đề document thực thi mỗi khi component Greet hiển thị. Bạn chỉ muốn nó được thực thi khi prop name thay đổi - đó là lý do bạn cung cấp tên làm dependency cho `useEffect (callback, [name])`.

### 2. Đối số Dependencies

Đối số `Dependencies` của `useEffect(callback, dependencies)` cho phép bạn kiểm soát thời điểm **side effect** chạy. Khi `Dependencies` là:

#### A) Không có: Side effect chạy sau mỗi lần rendering

```jsx
import { useEffect } from 'react';
function MyComponent() {
  useEffect(() => {
    // Runs after EVERY rendering
  });  
}
```

#### B) Array rỗng []: side-effect chạy một lần sau lần hiển thị đầu tiên.

```jsx
import { useEffect } from 'react';
function MyComponent() {
  useEffect(() => {
    // Runs ONCE after initial rendering
  }, []);
}
```

#### C) Có props hoặc state [prop1, prop2, ..., state1, state2]: side-effect chỉ chạy khi bất kỳ giá trị phụ thuộc nào thay đổi.

```jsx
import { useEffect, useState } from 'react';
function MyComponent({ prop }) {
  const [state, setState] = useState('');
  useEffect(() => {
    // Runs ONCE after initial rendering
    // and after every rendering ONLY IF `prop` or `state` changes
  }, [prop, state]);
}
```

Trích từ:: [Giải thích đơn giản về React.useEffect () - DEV Community](https://dev.to/buiminh15/giai-thich-don-gian-ve-reactuseeffect--2k4f)