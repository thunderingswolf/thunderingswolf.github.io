---
title: DigtalOcean使用
date: 2019-09-19 16:01:53
tags:
---







注册账号

测速：

创建主机

安装ssh

安装docker

安装shadowserver





```shell
192.167.72.157 19891
167.71.110.173

sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo systemctl enable docker
docker pull shadowsocks/shadowsocks-libev

docker run -e PASSWORD=xyzy@topsec -p 18388:8388 -p 18388:8388/udp -d shadowsocks/shadowsocks-libev

docker run -d -p 18388:18388 -p 18388:18388/udp --name ss-libev -v /etc/shadowsocks-libev:/etc/shadowsocks-libev teddysun/shadowsocks-libev
```



非docker方式

```
https://www.linuxbabe.com/linux-server/setup-your-own-shadowsocks-server-on-debian-ubuntu-centos

https://blog.csdn.net/alex_bean/article/details/86500662

https://blog.csdn.net/weixin_43599336/article/details/85970601
```

