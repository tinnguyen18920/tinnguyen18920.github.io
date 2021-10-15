---
title: Cài đặt WSL Windows 11
description: Cài đặt WSL trên Windows 11
date: 2021-10-15 09:39:00 AM
last_modified_at: 2021-10-15 09:39:00 AM
toc: false
tags: wsl windows-11
---



## Cài đặt WSL

Mở Windows Powershell hoặc cmd bằng quản trị viên.

![](/assets/img/Screenshot 2021-10-15 081621.png)

Sau đó, thực hiện câu lệnh sau để xem tất cả các distributions có thể cài đặt.

```powershell
wsl --list --online

# Kết quả của câu lệnh trên có dạng
The following is a list of valid distributions that can be installed.
Install using 'wsl --install -d <Distro>'.

NAME            FRIENDLY NAME
Ubuntu          Ubuntu
Debian          Debian GNU/Linux
kali-linux      Kali Linux Rolling
openSUSE-42     openSUSE Leap 42
SLES-12         SUSE Linux Enterprise Server v12
Ubuntu-16.04    Ubuntu 16.04 LTS
Ubuntu-18.04    Ubuntu 18.04 LTS
Ubuntu-20.04    Ubuntu 20.04 LTS
```

Cài đặt Ubuntu 20.04, sau đó khởi động lại để có thể sử dụng WSL.
```powershell
wsl --install -d "Ubuntu-20.04" 
# wsl --install -d "Ubuntu-20.04" && Restart-Computer
```



References:

[https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install){:target="_blank"}





