---
title: CentOS7配置SSHD服务
date: 2019-07-05 17:35:46
categories:
- 技术
tags:
- 技术
- CentOS
---

## CentOS7 配置SSHD服务

查看SSHD配置文件

```
vi /etc/ssh/sshd_config
修改一下参数：
1. 端口、允许监听
2. 允许root登录

# If you want to change the port on a SELinux system, you have to tell
# SELinux about this change.
# semanage port -a -t ssh_port_t -p tcp #PORTNUMBER
#
Port 22
#AddressFamily any
ListenAddress 0.0.0.0
ListenAddress ::
--------------------

# Authentication:

#LoginGraceTime 2m
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10


```

重启服务

```
systemctl restart sshd
```

设置开机自启动

```
systemctl enable sshd.service
```

