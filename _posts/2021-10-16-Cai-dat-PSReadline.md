---
title: Cài đặt PSReadline cho Windows Powershell
date: 2021-10-16 07:13:00 AM
last_modified_at: 2021-10-16 07:13:00 AM
tags: powershell
---

`PSReadline` giúp tăng trải nghiệm khi sử dụng Windows Powershell như 

- Tìm kiếm lịch sử
- Gợi ý câu lệnh
- Menu câu lệnh

Sau khi cài đặt như [hướng dẫn](https://github.com/PowerShell/PSReadLine#installation){:target="_blank"}, chèn [sample profile](https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/SamplePSReadLineProfile.ps1){:target="_blank"} vào `$profile` của powershell, chèn thêm câu sau vào cuối tệp

```
Set-PSReadLineOption -PredictionSource History
```





