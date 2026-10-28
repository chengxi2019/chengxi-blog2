---
title: note-ubuntu汇总2
date: 2026-10-18 20:40:46
tags:
    - Linux
    - Ubuntu
---

### 查找命令(命令本体执行文件位置)
考试考，仅此而已，日常不用：
``` bash
which 命令
```

### 在特定位置下寻找特定文件
find 路径 -name 文件名
`find /etc -name "passwd"`


## 权限管理

使用`ls -l`查看文件目前的权限
`drwxrwxr-x 2 chengxi......`

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

## chmod更改权限基本语法：
chmod 用户 增减权限 具体权限 文件名

例：    a     +       rwx   filename

附注：使用 *chmod* 改权限时，a+rwx 之间*没有*空格
### 用户类型说明
符号	含义
u	所有者（user）
g	组用户（group）
o	其他用户（others）
a	所有用户（all）
>未指明默认为所有用户
>你一般属于其他用户

### 常用示例
 
``` bash
为所有用户增加所有权限：
chmod a+rwx filename

为其他用户减少写、执行权限：
chmod o-wx filename

数字方式设置权限（755）：
chmod 755 filename  

755 表示：所有者拥有全部权限（rwx），组用户和其他用户拥有读与执行权限（r-x）
```
>755是最常用的，记忆


### 更改文件所有者（权限）
通常需要使用 sudo 配合  
chown 被给与权限用户 / :组名 文件名  
``` bash
chown ubuntu aa.c
将文件aa.c归属于ubuntu

chown root aa.c
将文件aa.c归属于超级用户组
```
root也就是超级用户
也可同时为一个用户与组赋予权限：
`chown ubuntu:root aa.c`

### tar打包文件
tar -cvf 包名.tar 被压缩文件

### 查看压缩包内容
tar -tf 包名

### 解压缩
tar -xvf 包名

### 解压至指定位置:
tar -xvf 包名 -C 路径

>附：解压路径为空时默认解压至当前目录，
>-C必须为大写，
>-cvf与-xvf仅为打包而不压缩，压缩需gzip或bzip配合

## tar拓展:

### gzip

``` bash
tar -czvf 包名.gz 被压缩文件
tar -xzvf 包名.gz 解压缩文件
```

### bz2

``` bash
tar -cjvf 包名.bz2 被压缩文件
tar -xjvf 包名.bz2 解压缩文件
```

>附注：后缀可以不写，已能够自动识别