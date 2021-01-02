---
title: CentOS7 IP地址配置
date: 2019-07-05 11:35:46
categories:
- 技术
tags:
- 技术
- CentOS
---

## CentOS7 IP地址配置

查看网卡配置情况

```
ls /etc/sysconfig/network-scripts/
vi /etc/sysconfig/network-scripts/ifcfg-en33
```

修改配置文件

```
TYPE=Ethernet
BOOTPROTO=static
DEFROUTE=yes
PEERDNS=yes
PEERROUTES=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_PEERDNS=yes
IPV6_PEERROUTES=yes
IPV6_FAILURE_FATAL=no
NAME=enp0s3
UUID=77218084-6f63-4024-8d13-3de80a05e760
DEVICE=enp0s3
ONBOOT=yes
IPADDR=10.0.0.177
PREFIX=24
GATEWAR=10.0.0.1
DNS1=8.8.8.8
```

重启网卡服务

```
systemctl restart network
```

> 如果是虚拟机，修改网络模式为桥接模式，重新启动虚拟机