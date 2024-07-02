---
share: true
created: 2023-10-30T14:29
updated: 2024-06-22T01:37
---
# Thử nhanh
Sau khi cài đặt Git, Deno và clone repo này về thì chạy lệnh sau trên terminal:
```
deno task start
```

# Lấy dữ liệu từ vault, website của bạn
## Chuẩn bị dữ liệu
### Obsidian, Logseq
Vault của bạn cần có một thư mục thiết lập, và trong đó có một note thiết lập có frontmatter như sau:
```yaml
---
Tên vault: xxx
Mã vault: yyy
Mô tả: zzz
URL: ttt
---
```

### WordPress 
[Mở PhPMyAdmin lên và chạy truy vấn SQL](https://youtu.be/VnBdOBKwPes?si=6XjJZ3hsX-WR15jT) dưới đây. Nhớ thay `wp` bằng tên table của bạn.
```sql
SELECT wp_posts.post_title, GROUP_CONCAT(wp_terms.name) AS categories, wp_posts.post_name, wp_posts.post_author, wp_posts.post_excerpt, wp_posts.post_date, wp_posts.post_modified
FROM wp_posts
LEFT JOIN wp_term_relationships ON (wp_posts.ID = wp_term_relationships.object_id)
LEFT JOIN wp_term_taxonomy ON (wp_term_relationships.term_taxonomy_id = wp_term_taxonomy.term_taxonomy_id)
LEFT JOIN wp_terms ON (wp_term_taxonomy.term_id = wp_terms.term_id)
WHERE wp_posts.post_type = 'post' 
AND wp_posts.post_status = 'publish'
GROUP BY wp_posts.ID
```
Xuất kết quả dưới dạng CSV.

## Thiết lập cấu hình
Chỉnh sửa các cấu hình có sẵn trong `Cấu hình và dữ liệu/Nơi đăng` và các đường dẫn trong `Code chạy trên local, server, KV/ĐƯỜNG_DẪN.ts` cho đúng.

## Tạo biến môi trường
Tạo tập tin `.env` với nội dung như sau:
```env
DENO_KV_ACCESS_TOKEN = XXX
KV_UUID = YYY

ORIGIN = https://localhost:8000
CORS_PROXY = https://mywebsite.deno.dev
```

## Tạo dữ liệu 
Đảm bảo tập tin `Code chạy trên local, server, KV/mod.ts` các dòng sau không bị comment:
```ts
import { tạoBàiĐăng, tạoNơiĐăng } from "./Tạo dữ liệu.ts";

await tạoBàiĐăng();
await tạoNơiĐăng();
```
Bắt đầu tạo danh sách bài đăng và nơi đăng bằng việc chạy lệnh sau trên terminal:
```
deno run --allow-all --unstable-kv `Code chạy trên local, server, KV/mod.ts`
```
Sau đó khởi động dự án bằng lệnh sau trên terminal:
```
deno task start
```
Truy cập `http://localhost:8000` để xem kết quả

## Deploy
Dùng Deno Deploy và liên kết tới GitHub của bạn.

# Giấy phép
AGPL: Người sử dụng dịch vụ của bạn có quyền tiếp cận và chia sẻ mã nguồn từ các chương trình bạn tạo ra dựa trên chương trình này. Đọc thêm về [lý do sử dụng giấy phép này](https://doi-thoai.deno.dev/why-affero-gpl.d.1 "Why the GNU Affero GPL - GNU Project - Free Software Foundation").
![Logo AGPL](https://www.gnu.org/graphics/agplv3-with-text-162x68.png) 