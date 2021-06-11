---
title: matlab 指定python 路径 64bit
date: 2020-09-03 11:14:52.000
updated: 2020-09-03 11:14:52.000
csdn_url: https://blog.csdn.net/weixin_43531940/article/details/108378726
description: 因为matlab 不支持 32bitpython  和高版本python。而系统默认装是32bit 。anaconda只能虚拟路径。
一：添加anaconda的envs到path 代替系统的32bit
二：装个64bit的python
三：在matlab中指定路径。重启后会变
pyversion(‘C:\ProgramData\Anaconda3\envs\AgeGender\python.exe’)

...
tags: python,anaconda,matlab
categories: python
article_id: 108378726
---
﻿因为matlab 不支持 32bitpython  和高版本python。而系统默认装是32bit 。anaconda只能虚拟路径。
### 一：添加anaconda的envs到path 代替系统的32bit
### 二：装个64bit的python
### 三：在matlab中指定路径。重启后会变

pyversion('C:\ProgramData\Anaconda3\envs\AgeGender\python.exe')
