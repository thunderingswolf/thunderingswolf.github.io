---
title: Linux基本操作命令
date: 2019-07-05 10:35:46
categories:
- 技术
tags:
- 技术
- CentOS
---

## Linux基本操作命令

教程：https://www.runoob.com/linux/linux-tutorial.html

### 1.用户名密码

```
useradd anomali
passwd anomali
```

### 2.systemctl

```
启动一个服务：systemctl start firewalld.service
关闭一个服务：systemctl stop firewalld.service
重启一个服务：systemctl restart firewalld.service
显示一个服务的状态：systemctl status firewalld.service
在开机时启用一个服务：systemctl enable firewalld.service
在开机时禁用一个服务：systemctl disable firewalld.service
查看服务是否开机启动：systemctl is-enabled firewalld.service;echo $?
查看已启动的服务列表：systemctl list-unit-files|grep enabled

```

### 3.监听端口开放

```
netstat -tlunp
```

### 4.Yum安装

```
yum install net-tools
yum install telnet
yum install iptables-services
```

### 5.linux查找



### 6. linux修改文件所属用户和组

**使用chown命令可以修改文件或目录所属的用户：**

​       命令：chown 用户 目录或文件名

​       例如：chown qq /home/qq  (把home目录下的qq目录的拥有者改为qq用户) 

**使用chgrp命令可以修改文件或目录所属的组：**

​       命令：chgrp 组 目录或文件名

​       例如：chgrp qq /home/qq  (把home目录下的qq目录的所属组改为qq组)

1. 