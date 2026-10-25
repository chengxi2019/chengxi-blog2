---
title: note3.MySQL1
date: 2026-10-15 23:29:59
tags:
---
```sql
-- 展示数据库
SHOW DATABASES;
```
-- 创建数据库
CREATE DATABASE name;

-- 无重命名库语句,需复制为新库的同时改名


-- 建库集合，包含数据默认排列类型 
CREATE DATABASE name
  DEFAULT CHARACTER SET utf8mb4
  COLLATE utf8mb4_general_ci;
  
-- 一般情况默认为此，也可省略

DROP DATABASE name;
-- 删除数据库

USE DATABASE name;
-- 使用数据库，用于建表等操作的前置





SHOW TABLES;
-- 展示数据表

CREATE TABLE department (
    dept_id   CHAR(4)     PRIMARY KEY,
    dept_name VARCHAR(30) NOT NULL
)

-- 建表语句，包含两条示例字段

--  字段名     数据格式    PRIMARY KEY主键 
--                        NOT NULL不可为空,NULL
-- 提示：最末尾一个字段后勿写，

AFTER TABLE name ADD COLUMN 插入字段名  数据格式 是否可为空 AFTER 插入位置处的前一个字段名;
-- 在已有的表中插入新字段


DROP TABLE name;
-- 删除数据库

DESC name;
-- 展示数据表内的字段

INSERT INTO department (dept_id, dept_name) VALUES
    ('D001', '软件技术'),
    ('D002', '大数据技术'),
    ('D003', '计算机网络'),
    ('D004', '人工智能技术'),
    ('D005', '数字媒体技术');

-- 插入数据，严格按照格式
-- 对象1（ "字段1" ，"字段2" ），
-- 对象2（ "字段1" ，"字段2" ），
-- 对象3（ "字段1" ，"字段2" ），



--基本查询

-- 万用开头，显示要展示的内容，例：查询未设置电话号码的学生姓名，在此处（select）写入name，在where写入phonenumber
SELECT student_name FROM student3

-- -数值比较
WHERE entrance_score >= 480
-- 文本比较
WHERE major = "软件技术"
-- 文本比较-反向
WHERE not major = "软件技术"
-- OR或，查询OR两侧的值，任一满足即可
WHERE major = "软件技术"
OR    major = "计算机网络"
-- AND与,查询AND两侧的值，必须同时满足条件
WHERE major = "软件技术"
AND entrance_score > 480
-- IN列出(字段名)内的字段
WHERE major IN ("软件技术","计算机网络")
-- BETWEEN列出between .. and .. 范围中符合的值
WHERE scholarship BETWEEN 450 AND 500
-- LIKE模糊查询包含%的内容
WHERE student_name LIKE  '%宁%'
-- LIKE模糊查询,_为任意字符内容，适用于查询已知长度及部分内容
WHERE student_name LIKE  '_敏'
-- is null查询空值
WHERE phone IS NULL
-- is not null查询非空值
WHERE phone IS NOT NULL