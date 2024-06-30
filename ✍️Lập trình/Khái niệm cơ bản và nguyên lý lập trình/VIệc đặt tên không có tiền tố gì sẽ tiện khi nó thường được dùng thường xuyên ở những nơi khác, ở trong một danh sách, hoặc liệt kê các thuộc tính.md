---
share: true
created: 2023-10-30T14:29
updated: 2024-06-13T23:30
---
# Liệt kê thuộc tính
```js
const {
	URL: url,
	"Tên nơi đăng": tênNơiĐăng,
	"Loại nơi đăng": loạiNơiĐăng,
	"Tên nền tảng": tênNềnTảng,
	"Mô tả nơi đăng": môTảNơiĐăng,
	"Loại nền tảng": loạiNềnTảng,
	"Vị trí": vịTrí,
} 
```
# Nằm trong một danh sách
```ts
const danhSáchNơiĐăng: NơiĐăng[] = [...] 
for (const nơiĐăng of danhSáchNơiĐăng) 
```
# Dùng thường xuyên ở nơi khác
Tại script `a.js` ta có như sau:
```js
const cấuHình = {
	vịTrí: vậtThểVịTrí
	nơiĐăng: nơiĐăng
} 
```
Do `nơiĐăng` chủ yếu dùng ở ngoài script này nên nó không có tiền tố `vậtThể` trong tên biến. Ngược lại, `vậtThểVịTrí` chủ yếu được dùng trong script này, và bản thân nó cũng cần phải dùng cả key `vịTrí`, nên để phân biệt key với value của entry này thì đặt như vậy cho dễ phân biệt.

Vì để mặc định của không có tiền tố gì là `vậtThể`, nên nếu nó là cấu hình thì nên có tiền tố

# Khi nào thì dùng `vậtThể`
- Khi bỏ đi thì không phải là danh từ. VD, đặt tên là `tiếpThị` thì hơi không lọt. `vậtThểTiếpThị` nghe ổn hơn
Nguồn:: [[Tự ngẫm nghĩ, trải nghiệm]]

# Có viết in hoa các ký tự viết tắt khi dùng camelCase không?
Các biến mặc định thì vẫn có làm vậy. VD: `URL`, `HTMLDocument` Nhưng vì có thể dễ bị lầm với cái mặc định nên có thể viết thường để đỡ phải tìm cách nghĩ một tên biến khác. 
Vấn đề là, chính vì JS đã dùng `URL` rồi, nên các url của mình mà nếu đặt in hoa hết thì sẽ bị trùng, nên không làm vậy được. Nên đành phải dùng `url`. `Url` là để dành cho kiểu, VD: 
```ts
type Url = URL | string
```