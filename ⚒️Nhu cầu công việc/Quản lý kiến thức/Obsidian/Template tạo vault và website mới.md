---
share: true
created: 2023-10-30T14:29
updated: 2024-08-25T21:01
---
## Tạo kho mới
`Ξ Thiết lập/Ξ Thiết lập.md`:
```yaml
Tên vault: Tiếp thị số, xử lý dữ liệu và lập trình
Mã vault: C2
Mô tả: Những thứ giúp xây dựng mental model khi phải code một cái gì đó
URL: https://{{subDomain}}.quảcầu.cc
Git URL: {{gitUrl}}
```

Enveloppe:

## Tạo web mới
- [ ] `_data.yaml`
- [ ] CNAME

## GitHub
```
git add -A 
git commit -m "Khởi tạo"
git tag Cấutrúc0.0.1

gh repo create --public
git remote add origin {{gitUrl}}
git push -u origin main
```
## đối ⊷ thoại
## Cloudflare