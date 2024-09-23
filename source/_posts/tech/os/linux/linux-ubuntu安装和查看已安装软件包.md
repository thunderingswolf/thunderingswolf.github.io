---
title: linux/ubuntu安装和查看已安装软件包
date: 2023-11-02 15:37:14
categories:
- tech
- os
- linux
tags: 
- tech
- os
- linux
---

终端通过命令行方式进行的软件包安装、卸载和删除的方法。

一、Ubuntu中软件安装方法

1、APT方式

（1）普通安装：`apt-get install softname1 softname2 …;`

（2）修复安装：`apt-get -f install softname1 softname2... ;(-f Atemp to correct broken dependencies)`

（3）重新安装：`apt-get --reinstall install softname1 softname2...;`

2、Dpkg方式

（1）普通安装：`dpkg -i package_name.deb`

3、源码安装（.tar、tar.gz、tar.bz2、tar.Z）

首先解压缩源码压缩包然后通过tar命令来完成
```
a．解xx.tar.gz：tar zxf xx.tar.gz
b．解xx.tar.Z：tar zxf xx.tar.Z
c．解xx.tgz：tar zxf xx.tgz
d．解xx.bz2：bunzip2 xx.bz2
e．解xx.tar：tar xf xx.tar
```
然后进入到解压出的目录中，建议先读一下README之类的说明文件，因为此时不同源代码包或者预编译包可能存在差异，然后建议使用ls -F --color或者ls -F命令（实际上我的只需要 l 命令即可）查看一下可执行文件，可执行文件会以*号的尾部标志。

一般依次执行
```
./configure
make
sudo make install
```
即可完成安装。

二、Ubuntu中软件包的卸载方法

1、APT方式

（1）移除式卸载：`apt-get remove softname1 softname2 …`;（移除软件包，当包尾部有+时，意为安装）

（2）清除式卸载：
```
apt-get --purge remove softname1 softname2...;(同时清除配置)
apt-get purge sofname1 softname2...;(同上，也清除配置文件)
```
2、Dpkg方式

（1）移除式卸载：dpkg -r pkg1 pkg2 ...;

（2）清除式卸载：dpkg -P pkg1 pkg2...;

三、Ubuntu中软件包的查询方法

Dpkg 使用文本文件来作为数据库.通称在 /var/lib/dpkg 目录下. 通称在 status 文件中存储软件状态,和控制信息. 在 info/ 目录下备份控制文件, 并在其下的 .list 文件中记录安装文件清单, 其下的 .mdasums 保存文件的 MD5 编码.

体验使用数据库的时刻到了:
```
$ dpkg -l Desired=Unknown/Install/Remove/Purge/Hold | Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed |/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) ||/ Name Version Description +++-===========-================-======================================== ii aalib1 1.4p5-28 ascii art library - transitional package ii adduser 3.85 Add and remove users and groups ii alien .63 install non-native packages with dpkg ... ...
```

每条记录对应一个软件包, 注意每条记录的第一, 二, 三个字符. 这就是软件包的状态标识, 后边依此是软件包名称, 版本号, 和简单描述.

第一字符为期望值,它包括:
u 状态未知,这意味着软件包未安装,并且用户也未发出安装请求.
i 用户请求安装软件包.
r 用户请求卸载软件包.
p 用户请求清除软件包.
h 用户请求保持软件包版本锁定.
第二列,是软件包的当前状态.此列包括软件包的六种状态.
n 软件包未安装.
i 软件包安装并完成配置.
c 软件包以前安装过,现在删除了,但是它的配置文件还留在系统中.
u 软件包被解包,但还未配置.
f 试图配置软件包,但是失败了.
h 软件包安装,但是但是没有成功.
第三列标识错误状态,可以总结为四种状态. 第一种状态标识没有问题,为空. 其它三种符号则标识相应问题.
h 软件包被强制保持,因为有其它软件包依赖需求,无法升级.
r 软件包被破坏,可能需要重新安装才能正常使用(包括删除).
x 软包件被破坏,并且被强制保持.
也可以以统配符模式进行模糊查询, 比如我要查找以nano字符开始的所有软件包:
```
$ dpkg -l nano* Desired=Unknown/Install/Remove/Purge/Hold | Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed |/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) ||/ Name Version Description +++-==============-==============-============================================ ii nano 1.3.10-2 free Pico clone with some new features pn nano-tiny <none> (no description available) un nanoblogger <none> (no description available)
```

以上状态说明: 系统中安装了 nano 版本为 1.3.10-2 ;安装过 nano-tiny , 后来又清除了; 从未安装过nanoblogger .

如果觉得 dpkg 的参数过多, 不利于记忆的话, 完全可以使用 dpkg-query 进行 dpkg 数据库查询.

应用范例:

查询系统中属于nano的文件:
```
$ dpkg --listfiles nano
or
$ dpkg-query -L nano
查看软件nano的详细信息:
$ dpkg -s nano
or
$ dpkg-query -s nano
查看系统中软件包状态, 支持模糊查询:
$ dpkg -l
or
$dpkg-query -l
查看某个文件的归属包:
$ dpkg-query -S nano
or
$ dpkg -S nano
```
三、其他应用总结
```
apt-cache search # ------(package 搜索包)
apt-cache show #------(package 获取包的相关信息，如说明、大小、版本等)
apt-get install # ------(package 安装包)
apt-get install # -----(package --reinstall 重新安装包)
apt-get -f install # -----(强制安装, "-f = --fix-missing"当是修复安装吧...)
apt-get remove #-----(package 删除包)
apt-get remove --purge # ------(package 删除包，包括删除配置文件等)
apt-get autoremove --purge # ----(package 删除包及其依赖的软件包+配置文件等（只对6.10有效，强烈推荐）)
apt-get update #------更新源
apt-get upgrade #------更新已安装的包
apt-get dist-upgrade # ---------升级系统
apt-get dselect-upgrade #------使用 dselect 升级
apt-cache depends #-------(package 了解使用依赖)
apt-cache rdepends # ------(package 了解某个具体的依赖,当是查看该包被哪些包依赖吧...)
apt-get build-dep # ------(package 安装相关的编译环境)
apt-get source #------(package 下载该包的源代码)
apt-get clean && apt-get autoclean # --------清理下载文件的存档 && 只清理过时的包
apt-get check #-------检查是否有损坏的依赖
dpkg -S filename -----查找filename属于哪个软件包
apt-file search filename -----查找filename属于哪个软件包
apt-file list packagename -----列出软件包的内容
apt-file update --更新apt-file的数据库

dpkg --info "软件包名" --列出软件包解包后的包名称.
dpkg -l --列出当前系统中所有的包.可以和参数less一起使用在分屏查看. (类似于rpm -qa)
dpkg -l |grep -i "软件包名" --查看系统中与"软件包名"相关联的包.
dpkg -s 查询已安装的包的详细信息.
dpkg -L 查询系统中已安装的软件包所安装的位置. (类似于rpm -ql)
dpkg -S 查询系统中某个文件属于哪个软件包. (类似于rpm -qf)
dpkg -I 查询deb包的详细信息,在一个软件包下载到本地之后看看用不用安装(看一下呗).
dpkg -i 手动安装软件包(这个命令并不能解决软件包之前的依赖性问题),如果在安装某一个软件包的时候遇到了软件依赖的问题,可以用apt-get -f install在解决信赖性这个问题.
dpkg -r 卸载软件包.不是完全的卸载,它的配置文件还存在.
dpkg -P 全部卸载(但是还是不能解决软件包的依赖性的问题)
dpkg -reconfigure 重新配置
```

apt-get install

下载软件包，以及所有依赖的包，同时进行包的安装或升级。如果某个包被设置了 hold (停止标志，就会被搁在一边(即不会被升级)。更多 hold 细节请看下面。

apt-get remove [--purge]

移除 以及任何依赖这个包的其它包。
--purge 指明这个包应该被完全清除 (purged) ，更多信息请看 dpkg -P。

apt-get update

升级来自 Debian 镜像的包列表，如果你想安装当天的任何软件，至少每天运行一次，而且每次修改了
/etc/apt/sources.list 後，必须执行。

apt-get upgrade [-u]

升 级所有已经安装的包为最新可用版本。不会安装新的或移除老的包。如果一个包改变了依赖关系而需要安装一个新的包，那么它将不会被升级，而是标志为 hold。apt-get update 不会升级被标志为 hold 的包 (这个也就是 hold 的意思)。请看下文如何手动设置包为 hold。我建议同时使用 '-u' 选项，因为这样你就能看到哪些包将会被升级。

apt-get dist-upgrade [-u]

和 apt-get upgrade 类似，除了 dist-upgrade 会安装和移除包来满足依赖关系。因此具有一定的危险性。

apt-cache search

在软件包名称和描述中，搜索包含xxx的软件包。

apt-cache show

显示某个软件包的完整的描述。

apt-cache showpkg

显示软件包更多细节，以及和其它包的关系。
