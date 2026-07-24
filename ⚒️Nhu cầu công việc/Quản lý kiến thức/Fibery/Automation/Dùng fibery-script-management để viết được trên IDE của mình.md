---
share: true
created: 2023-10-30T14:29
updated: 2026-07-08T15:32
---
Nguồn:: [GitHub - mblais/fibery-script-management: Remote script management for Fibery.io automations](https://github.com/mblais/fibery-script-management)
[[Sự khác biệt giữa IDE và trình soạn thảo văn bản nằm ở việc compile code. Nên chính xác mà nói thì không có IDE để viết JS cho máy khách]]

Nếu url có ký tự unicode thì cần unescape nó:
```PowerShell
node --env-file=.env .\fibscripts.js pull --url=https://quacau.fibery.io/fibery/space/Định_kỳ_đóng_phí/database/Hợp_đồng/automations/rule/6799ad300d3901c00626d49e/actions
```
Nguồn:: [No script is pulled even when the url is correct · Issue #2 · mblais/fibery-script-management](https://github.com/mblais/fibery-script-management/issues/2)
Nơi thảo luận: [Beta testers wanted for Fibery script management tool - API & Programming - Fibery Community](https://community.fibery.io/t/beta-testers-wanted-for-fibery-script-management-tool/5466/14)
