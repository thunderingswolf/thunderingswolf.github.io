---
title: Docker操作手册
date: 2019-07-11 16:35:46
categories:
- 技术
tags:
- 技术
- Postgres
---

## Docker操作手册



### Docker安装



#### 拷贝文件：

```
docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-
docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH

#将主机/www/runoob目录拷贝到容器96f7f14e99ab的/www目录下。

docker cp /www/runoob 96f7f14e99ab:/www/
#将主机/www/runoob目录拷贝到容器96f7f14e99ab中，目录重命名为www。

docker cp /www/runoob 96f7f14e99ab:/www
#将容器96f7f14e99ab的/www目录拷贝到主机的/tmp目录中。

docker cp  96f7f14e99ab:/www /tmp/



```

