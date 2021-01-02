---
layout: 'n'
title: Hexo博客搭建
date: 2021-01-01 22:09:43
tags: 
- Hexo
- Next
---
## hexo建站

参考hexo官网：<https://hexo.io/zh-cn/docs/>

## next主题

参考next官网：<http://theme-next.iissnan.com/>

## 使用技巧

### 源码和部署程序管理

1. 创建仓库，[https://thunderingswolf.github.io](https://thunderingswolf.github.io)

2. 创建两个分支：master 与 hexo

3. 设置hexo为默认分支，放置网页源文件（只需手动git管理该分支即可）；执行git add .、git commit -m "..."、git push origin hexo提交网站相关的文件

4. 修改_config.yml中的deploy参数，分支应为master；执行hexo g -d时，将自动部署至master分支；thunderingswolf.github.io指向master分支

>>总结：仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页

### 多台电脑协作流程

1. 安装hexo基础环境(node.js\git\hexo)，参考官网: https://hexo.io/zh-cn/docs/
2. 使用`git clone git@github.com:thunderingswolf/thunderingswolf.github.io.git`拷贝仓库
3. 【可选】下载最新主题：`git clone https://github.com/iissnan/hexo-theme-next themes/next` ,如无需经常更新可一并存放至 hexo分支中
4. 本地对博客进行修改（添加新博文、修改样式等等）
5. 依次执行git add .、git commit -m "..."、git push origin hexo指令将改动推送到GitHub（此时当前分支应为hexo）
6. 执行hexo g -d发布网站到master分支



### 附录：ssh配置

1. github ssh免密配置：<https://www.jianshu.com/p/9317a927e844>
2. 多远程仓库ssh配置：<https://www.jianshu.com/p/ddd3122cb351>