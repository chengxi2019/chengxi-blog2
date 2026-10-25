---
title: note-ubuntu汇总
date: 2026-10-18 13:53:46
tags:
---
### 打开目录
``` bash
cd /
```

### 回到上一级目录
``` bash
cd ..
```
### 展示当前目录下文件	 -a显示所有文件，包含隐藏文件 -l显示详细信息
```
ls -l -a -h -i          
```
### 树状图展示当前目录文件
``` bash
tree -l 1               
```
-----------------------------

### 新建文件

``` bash
touch name
```

### 新建文件夹

``` bash
mkdir name
```

### 重命名 / 移动文件（mv 既可以重命名也可以移动）

``` bash
mv oldname newname
mv filename /路径
```

### 删除文件

``` bash
rm name
```

### 递归删除文件夹（文件夹内含有文件）

``` bash
rm -r name
```

### 删除前交互确认

``` bash
rm -i name
```

### 输出重定向，不存在则新建文件，覆盖原有内容

``` bash
语句 > 目标文件
```

### 批量创建文件示例

``` bash
file{1..9}.txt
```

### 复制文件

``` bash
cp name newfile
cp name1 name2
```
>复制文件夹时需-r递归以同时复制文件夹下的所有文件
>cp也可在复制时重命名

### 合并文件复制

``` bash
cp name1,name2 newfile
```

### echo 写入内容（覆盖原始内容）

``` bash
echo " " > /
```

### echo 追加内容（在文件末尾新增）

``` bash
echo " " >> /
```

### 查看文件全部内容

``` bash
cat /
```

### 在文件中查找内容，-n 显示行号，-i 忽略大小写

``` bash
grep -n /文件路径 "查找内容"
```

### 管道组合：输出文件内容的同时查找指定内容

``` bash
cat /文件路径 | grep -n "查找内容"
```

### 统计文件内容：‑l 行数 ‑w 单词数 ‑m 字符数

``` bash
wc -l -w -m
```

### Shell 通配符简要说明

> 
> 通配符是 shell 的特殊符号，用来匹配多个文件名，**不属于命令本身，由 shell 解析**

```
*        # 匹配任意长度任意字符（0个或多个字符）
?        # 匹配单个任意字符
[abc]    # 匹配括号内任意一个字符 a / b / c
{a,b,c}  # 批量展开，生成 a b c 多组参数
```

#### 简单示例

```
rm *.txt      # 删除所有 txt后缀文件
rm file?.txt  # ?匹配1个字符，删除 file1.txt file2.txt
touch file{1..5}.txt # 批量创建 file1~file5.txt
```