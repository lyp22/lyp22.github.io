---
published: true
title: Ubuntu16.04解决问题：E: 无法获得锁 /var/lib/dpkg/lock-frontend - open (11: 资源暂时不可用)
category: linux
tags: 
  - 常用
layout: post
---



在输入sudo apt-get update后发现终端提示：

> E: 无法获得锁 /var/lib/dpkg/lock-frontend - open (11: 资源暂时不可用)
  E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

# 解决方案一：

```
ps -e | grep apt
```

然后执行：`sudo kill` 进程号



 

# 解决方案二：
有一种情况是

```
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```

但我遇到的情况是：E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it? 

```
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock-frontend
```
