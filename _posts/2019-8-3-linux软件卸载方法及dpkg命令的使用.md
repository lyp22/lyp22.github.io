---
published: true
title: linux软件卸载方法及dpkg命令的使用
category: linux
tags: 
  - 常用
layout: post
---


# 卸载软件

如果知道软件的具体名称，可以使用

sudo apt-get remove --purge 软件名称

sudo apt-get autoremove --purge 软件名称

不知道要删除软件的具体名称，可以使用

dpkg --get-selections | grep "软件名称"

对于一个带-core的package，可以这样

sudo apt-get purge package-core(带-core的package)

清理残余数据

dpkg -l | grep ^rc | awk '{print $2}' | sudo xargs dpkg -P

# dpkg命令的其他用法

安装.deb包

dpkg -i <.deb 包名>

列出与该包相关联的文件

dpkg -L packge

显示该包的版本

dpkg -l packge

移除软件（保留配置）

dpkg -r packge

移除软件（不保留配置）

dpkg -P packge

查看包的详细信息

dpkg -s packge

列出.deb包的内容

dpkg -c packge

解开.deb包的内容

dpkg -unpack packge.deb

配置包

dpkg -configure packge

搜索所属包的内容

dpkg -S keyword
