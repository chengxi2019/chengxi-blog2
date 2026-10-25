---
title: note-ubuntu汇总2
date: 2026-10-18 20:40:46
tags:
---

### 查找命令
``` bash
which 命令
```

### 组合：在计算机下查找开头为passwd的文件
``` bash
find / -name "passwd"
```

## 权限管理：chmod
基本语法：
chmod 用户 增减权限 具体权限 文件名
例：    a     +       rwx   filename

### 用户类型说明
符号	含义
u	所有者（user）
g	组用户（group）
o	其他用户（others）
a	所有用户（all）
>未指明默认为所有用户
>你一般属于其他用户

### 权限类型说明
符号	含义     数字法
r	读权限          4
w	写权限（修改）   2
x	执行权限        1
-   没有权限        0
### 数字法

7   所有权限(读取，修改，执行)
6   读取与修改
5   读取与执行
3   修改与执行
1   读取
2   修改（不常见）
0   没有权限

## 常用示例

### 为所有用户增加所有权限：
``` bash

chmod a+rwx filename
为其他用户减少写、执行权限：


chmod o-wx filename
数字方式设置权限（755）：


chmod 755 filename  
755 表示：所有者拥有全部权限（rwx），组用户和其他用户拥有读与执行权限（r-x）
```
>755是最常用的，记忆