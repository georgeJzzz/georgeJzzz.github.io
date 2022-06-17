---
title: linux部署脚本sh
date: 2022-06-17 15:11:22
index_img: https://www.linuxmi.com/wp-content/uploads/2020/10/Garuda-Linux-Golden-Eagle-201007-2020-10-11-09-03-15-1024x576.png 
tags:
- 部署脚本
- 一键脚本
categories:
  - Bash

# python 安装
```bash
#!/bin/sh

# install python
apt-get install -y python3 python3-pip \
        && ln -s /usr/bin/pip3 /usr/local/bin/pip \
        && ln -s /usr/bin/python3 /usr/local/bin/python

# install python dependencies
pip install -r /app/install/requirements.txt
```
# golang 安装
```bash
#!/bin/sh

curl -OL https://golang.org/dl/go1.16.7.linux-amd64.tar.gz \
&& tar -C /usr/local -xvf go1.16.7.linux-amd64.tar.gz \
        && ln -s /usr/local/go/bin/go /usr/local/bin/go
```
# 依赖deps 安装
```shell
#!/bin/sh

# ensure directory mode of /tmp
chmod 777 /tmp

# update
apt-get update

# common deps
apt-get install -y curl git net-tools iputils-ping ntp ntpdate nginx wget dumb-init cloc unzip

# chromedriver deps
apt-get install -y libglib2.0-0 libnss3 libx11-6 # chromedriver deps
```
# chromedriver 安装
```shell
#!/bin/sh

# deps
apt-get install -y unzip xvfb libxi6 libgconf-2-4

# chrome
curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add
bash -c "echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' >> /etc/apt/sources.list.d/google-chrome.list"
apt-get update
apt-get -y install google-chrome-stable
echo `google-chrome --version`

# chromedriver
wget https://chromedriver.storage.googleapis.com/102.0.5005.61/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
mv chromedriver /usr/local/bin/chromedriver
chown root:root /usr/local/bin/chromedriver
chmod +x /usr/local/bin/chromedriver
```
# rod.sh 
```shell
#!/bin/sh

cat <<EOF > go.mod
module rod_github

go 1.16

require github.com/go-rod/rod v0.107.1
EOF

cat <<EOF > main.go
package main

import "github.com/go-rod/rod"

func main() {
    _ = rod.New().MustConnect()
}
EOF

go mod tidy
go run main.go

rm -f go.mod
rm -f go.sum
rm -f main.go
rm -f screenshot.png
```

Seaweedfs 文件存储
```bash
#!/bin/sh

wget https://github.com/crawlab-team/resources/raw/main/seaweedfs/2.79/linux_amd64.tar.gz \
  && tar -zxf linux_amd64.tar.gz \
  && cp weed /usr/local/bin
```
# Linux换国内源
[🍮换源脚本以及docker安装脚本](https://ymtb2m.yuque.com/georgejz/xrolmg/evg4mw?view=doc_embed&inner=F6vUZ)

# Docker安装
[🍮换源脚本以及docker安装脚本](https://ymtb2m.yuque.com/georgejz/xrolmg/evg4mw?view=doc_embed&inner=NkTfL)
