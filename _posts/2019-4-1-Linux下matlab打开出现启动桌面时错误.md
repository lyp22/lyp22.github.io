---
published: true
title: Linux下matlab打开出现启动桌面时错误
category: matlab
tags: 
  - matlab
layout: post
---



Ubuntu下matlab程序无法直接打开，出现一个“启动桌面时错误”的弹窗，以及提示一堆java似的错误

# 解决方法

sudo chown [username] -R ~/.matlab/

