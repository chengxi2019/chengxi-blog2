---
title: note3.MySQL1
date: 2026-10-15 23:29:59
tags:
    - sql
    - createdatabase
    - createtable
---

## 数据库

### 展示数据库
`SHOW DATABASES;`  

### 创建数据库
`CREATE DATABASE name;`  

### 无重命名库语句,需复制为新库的同时改名


### 建库集合，包含数据默认排列类型

``` sql
CREATE DATABASE name
DEFAULT CHARACTER SET utf8mb4
COLLATE utf8mb4_general_ci;
```  

>一般情况默认为此，也可省略

### 删除数据库
`DROP DATABASE name;`  

### 使用数据库，用于建表等操作的前置
`USE DATABASE name;`  


## 数据表

### 展示数据表
`SHOW TABLES;`  


### 建表语句，包含两条示例字段
``` sql
CREATE TABLE department (
    dept_id   CHAR(4)     PRIMARY KEY,
    dept_name VARCHAR(30) NOT NULL
)
```

对照格式  
字段名     数据格式    PRIMARY KEY主键  
字段名     数据格式    NOT NULL不可为空,NULL  
>
>提示：最末尾一个字段后勿写，  


### 在已有的表中插入新字段

``` sql
ALTER TABLE student
ADD COLUMN student_id INT NOT NULL AFTER class_id;
```

对照格式：  
``` sql
ALTER TABLE name 
ADD COLUMN 插入字段名  数据格式 是否可为空 AFTER 插入位置的前一个字段名;
```

### 删除数据表
`DROP TABLE name;`  

### 展示数据表内的字段
`DESC name;`  

### 插入数据
示例：  
``` sql
INSERT INTO department (dept_id, dept_name) VALUES
    ('D001', '软件技术'),
    ('D002', '大数据技术'),
    ('D003', '计算机网络'),
    ('D004', '人工智能技术'),
    ('D005', '数字媒体技术');
```  
插入数据，严格按照格式  
对象1（ "字段1" ，"字段2" ），  
对象2（ "字段1" ，"字段2" ），  
对象3（ "字段1" ，"字段2" ），  

## 基本查询

### SELECT万用开头，选择要展示的内容
select查询关键字，查询均已此为基础，
`SELECT student_name FROM student3`  
 

### Where关键字
>where写在from之后！！！  
从select的结果中筛选出符合的结果  
只可以筛选静态结果  

### 基本比较
数值比较
`WHERE entrance_score >= 480`  

文本比较
`WHERE major = "软件技术"`  

文本比较-反向
`WHERE not major = "软件技术"`  


### 逻辑比较
OR或，查询OR两侧的值，任一满足即可
`WHERE major = "软件技术" OR major = "计算机网络"`  

AND与,查询AND两侧的值，必须同时满足条件
`WHERE major = "软件技术" AND entrance_score > 480`  

### IN列出仅指定字段符合条件的
`WHERE major IN ("软件技术","计算机网络")`  

### BETWEEN列出between .. and .. 范围中符合的值
`WHERE scholarship BETWEEN 450 AND 500`  

### LIKE模糊查询
查询包含% %的内容:
`WHERE student_name LIKE  '%宁%'`

查询时_表示为任意字符:
`WHERE student_name LIKE  '_敏'`  
>适用于已知长度及部分内容的情况

### is null查询空值，非空值
`WHERE phone IS NULL`  
`WHERE phone IS NOT NULL`
