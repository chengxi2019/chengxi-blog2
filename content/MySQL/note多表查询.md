---
title:
created:
tags:
---

# 多表连接查询

作用:把分散在多张表里的数据，通过它们之间共同的字段（关联键）横向拼接成一张大宽表  
就是依据两张表里的相同类型的字段把两张表连在一起，这样方便一起查询信息  

比如:有表A记录商品id，门店位置，有表B记录门店位置，门店供货商  
此时依据门店位置相连两表，直接一步即可查询商品id与对应的门店供货商  

由此可知：**多表连接本身并不直接输出数据**，需要配合其他语句使用  

分为：**内连接，左连接，右连接**  

使用AS为表起别名并不是语法强制，而是为了消除同名冲突，同时缩减代码长度  

继续之前，先明确什么是**左右表**：  
多表连接基本格式：  
``` sql 
SELECT s.student_id,s.student_name,s.major,m.college_name FROM student5 AS s
INNER JOIN major_info AS m ON s.major = m.major
ORDER BY student_id
```
- 位于`FROM`后的为左表(先出现的为左表)例如`student5`  
- 位于`JOIN`后的为右表(后出现的为右表)例如`major_info`  


### 内连接INNER JOIN
作用：只有两张表都能对应起来的才会被展示  
即两张表作为连接的字段都要可以左右对应，而只有左或者只有右都不会显示(最严格)  
``` sql
...
INNER JOIN 右表 ON 左表.字段 = 右表.字段
...
```

### 左连接LEFT JOIN
作用：保留左表信息，如有数据无右表对应信息，右表字段处显示`NULL`  
``` sql
...
LEFT JOIN 右表 ON 左表.字段 = 右表.字段
...
```

### 右连接RIGHT JOIN
作用：保留右表信息，如有数据无左表对应信息，左表字段处显示`NULL`  
``` sql
...
RIGHT JOIN 右表 ON 左表.字段 = 右表.字段
...
```