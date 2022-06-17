---
title: linux部署脚本sh
date: 2022-06-17 15:11:22
index_img: https://image.baidu.com/search/detail?ct=503316480&z=undefined&tn=baiduimagedetail&ipn=d&word=%E9%83%A8%E7%BD%B2.png&step_word=&ie=utf-8&in=&cl=2&lm=-1&st=undefined&hd=undefined&latest=undefined&copyright=undefined&cs=519521377,1872512981&os=2240382411,743765763&simid=519521377,1872512981&pn=2&rn=1&di=7108135681917976577&ln=1879&fr=&fmq=1655454444047_R&fm=&ic=undefined&s=undefined&se=&sme=&tab=0&width=undefined&height=undefined&face=undefined&is=0,0&istype=0&ist=&jit=&bdtype=0&spn=0&pi=0&gsm=0&objurl=https%3A%2F%2Fgimg2.baidu.com%2Fimage_search%2Fsrc%3Dhttp%253A%252F%252Fwww.zhangyutong.net%252Fuploads%252Fimg%252F20191125%252F1574666456299317.png%26refer%3Dhttp%253A%252F%252Fwww.zhangyutong.net%26app%3D2002%26size%3Df9999%2C10000%26q%3Da80%26n%3D0%26g%3D0n%26fmt%3Dauto%3Fsec%3D1658046442%26t%3D131a7947022e54eb8802d8fc7dd38f32&rpstart=0&rpnum=0&adpicid=0&nojc=undefined&dyTabStr=MCw1LDEsNiw0LDMsNyw4LDIsOQ%3D%3D
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
