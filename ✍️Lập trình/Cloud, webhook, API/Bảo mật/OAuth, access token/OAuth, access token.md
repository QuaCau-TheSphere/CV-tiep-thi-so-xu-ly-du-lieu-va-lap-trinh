---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
## Google API
Thứ được tải về bằng tay
```json
{
  "installed": {
    "client_id": Để authorization server biết đây là client nào,
    "project_id": "gtm-pjx4b43k-n2jmm",
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://oauth2.googleapis.com/token",
    "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
    "client_secret": Để authorization server đảm bảo rằng clien này chính là client đó,
    "redirect_uris": [
      "http://localhost"
    ]
  }
}
```
[[Client ID là để máy cấp quyền biết client nào là client nào, còn client secret là để nó đảm bảo rằng client này chính là client đó]]

Thứ được tạo ra khi đã xác thực:
```json
{
  "type": "authorized_user",
  "client_id": Để authorization server biết đây là client nào,
  "client_secret": Để authorization server đảm bảo rằng clien này chính là client đó,
  "refresh_token": 
}
```