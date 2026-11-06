---
title: note11-6索引
time: 2026-11-06 23:26:22
tag:
---

建立索引可以提升在数据量极大的库中检索数据时的时间  

>快速记忆：建与删都用ON，仅SHOW用FROM

### 建索引

格式：`CREATE INDEX 索引名 ON 库名.表名(字段名)`  

### 查索引

格式：`SHOW INDEX FROM 表名`  

### 删索引

格式：`DELETE INDEX 索引名 ON 库名.表名`  

### EXPLAIN

作用：用来看 MySQL 到底打算怎么执行这条 SQL 的？  
>知道就可以了，要用就直接写在最前面  

格式：`EXPLAIN 语句`