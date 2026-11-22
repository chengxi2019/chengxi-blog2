---
title: note11-20视图view
created: 2016-11-20T10:36:23
tag:
  - 
---

# 视图VIEW

作用：视图就是一个能代替复杂查询、保护底层数据、且拥有表一样查询体验的“虚拟表”。  
补充：具有表的一部分作用，但不完全是表  
视图与表不能重名  

### 建立视图
基本语句：  
``` sql
CREATE VIEW 视图名称 AS
SELECT 字段列表 FROM 数据来源表
...;
```
>不要忘记**AS**  
>几乎就是包含了一个查询语句

### 更改视图ALTER
**注意：**与其他不同的是，更改视图时需要写重新写完整的建表语句！  
``` sql
ALTER VIEW 视图名称 AS
SELECT 字段列表 FROM 数据来源表
...;
``` 

### 使用视图：
**注意：**视图不能像函数直接使用SELECT，仍然与查表一样需要完整的SELECT与FROM  
``` sql
SELECT 字段列表 FROM 视图名
...;
```


### 查删语句

- 查当前存在的视图：
沿用**查表语句**:`SHOW TABLES`  
进阶：`SHOW FULL TABLES WHERE Table_type = 'VIEW';`  

- 删除视图:
`DROP VIEW 视图名`  

- 查看建视图语句：
`SHOW CREATE VIEW 视图名`  

