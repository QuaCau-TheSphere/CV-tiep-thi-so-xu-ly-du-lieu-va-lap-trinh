---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
Nguồn:: [GitHub - mblais/fibery-script-management: Remote script management for Fibery.io automations](https://github.com/mblais/fibery-script-management)
[[VS Code chỉ là code editor, không phải IDE]]

Nếu url có ký tự unicode thì cần unescape nó:
```PowerShell
node --env-file=.env .\fibscripts.js pull --url=https://quacau.fibery.io/fibery/space/Định_kỳ_đóng_phí/database/Hợp_đồng/automations/rule/6799ad300d3901c00626d49e/actions
```
Nguồn:: [No script is pulled even when the url is correct · Issue #2 · mblais/fibery-script-management](https://github.com/mblais/fibery-script-management/issues/2)
Nơi thảo luận: [Beta testers wanted for Fibery script management tool - API & Programming - Fibery Community](https://community.fibery.io/t/beta-testers-wanted-for-fibery-script-management-tool/5466/14)