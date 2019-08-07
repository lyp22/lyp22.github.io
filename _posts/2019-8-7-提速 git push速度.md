---
published: true
title: 提速 git push速度
category: git
tags: 
  - git
layout: post
---



# 代理服务器提速

如果你有shadowsocks的socket5代理，那么可以使用下面两条语句提速

前提是你的代理已经在运行

速度提升非常明显，之前几KB变成1-2MB的速度。

``` 
git config --global http.proxy 'socks5://127.0.0.1:1080' 
git config --global https.proxy 'socks5://127.0.0.1:1080'
```
