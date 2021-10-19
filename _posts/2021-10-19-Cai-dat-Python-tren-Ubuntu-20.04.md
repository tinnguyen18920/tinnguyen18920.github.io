---
title: Cài đặt Python trên Ubuntu 20.04
date: 2021-10-19 07:17:00 AM
last_modified_at: 
tags: python ubuntu
toc: true
---

Mỗi khi tạo một Python project mới, ta cần lưu tâm tới sự tương thích giữa các packages với phiên bản Python. Nên sử dụng phiên bản phù hợp là cần thiết. Bài viết này hướng dẫn cài đặt Python từ source.

## Thêm source package, cài đặt dependencies

Thêm Package `deb-src http://archive.ubuntu.com/ubuntu/ bionic main` vào `sources.list` nếu chưa có. Sau đó cài đặt dependencies bằng câu lệnh.

```shell
sudo apt-get update
# Thay đổi phiên bản theo phiên bản của bạn, nếu xảy ra lỗi thì giảm giần xuống
sudo apt-get build-dep python3.6
```

## Cài đặt Python

Vào trang [Download](https://www.python.org/ftp/python/){:target="_blank"}, tải và giải nén phiên bản Python muốn cài đặt. Đọc file hướng dẫn `README.rst` trong thư mục đã giải nén là tốt nhất.

## Script

`install_python.sh`

```sh
#!/usr/bin/sh
# Script install Python from source
#
# Usage: install_python.sh <python_version>
#
# python_version: the full version is shown on the FTP page
# https://www.python.org/ftp/python/

if [[ $# -eq 0 ]] ; then
    echo 'Missing Python version'
    exit 0
fi

VERSION="$1"
FILE="/etc/apt/sources.list"
SOURCEPACKAGE="deb-src http://archive.ubuntu.com/ubuntu/ bionic main"
DOWNLOAD_URL="https://www.python.org/ftp/python/$VERSION/Python-$VERSION.tgz"
DOWNLOADED_FILE=$(basename "$DOWNLOAD_URL")
EXTRACTED_FOLDER=$(basename "$DOWNLOADED_FILE" .tgz)

if ! grep -q "$SOURCEPACKAGE" "$FILE"; then
  echo "deb-src http://archive.ubuntu.com/ubuntu/ bionic main" | sudo tee -a /etc/apt/sources.list 
fi

sudo apt-get update
sudo apt-get build-dep python3.6


# Download, extract Python
mkdir -p ~/tmp && cd ~/tmp
wget $DOWNLOAD_URL
tar -xzf "$DOWNLOADED_FILE"

# Install Python
cd "$EXTRACTED_FOLDER"
# ./configure --help for usage
./configure
make
sudo make altinstall

# which python3.#
# update-alternative --install /usr/bin/python python $(which python3.#) <priority>
```

References:

[https://devguide.python.org/setup/#install-dependencies](https://devguide.python.org/setup/#install-dependencies){:target="_blank"}



