---
tiile: note11-1MySQL阶段总结
time: 2026-10-30 13:16:23
tag:     
---

``` sql

建库
CREATE DATABASE databasename
    DEFAULT CHARACTER SET utf8mb4
     
建表
CREATE TABLE tablename(
    id CHAR(4) NOT NULL ,
    name VARCHAR(20) NOT NULL,
    PRIMARY KEY id
)


有关外键：
CREATE TABLE 父表
    (父表没有什么变化，主要在子表中)；

CREATE TABLE 子表
    (子表字段)
    PRIMARY KEY 主键字段，
    CONSTRAINT  外键名(仅名称不是字段，常以fk开头)
    FOREIGN KEY (子表字段)
    REFERENCES  父表名(父表字段)

>必须先建立父表再建立子表，并在创建子表时建立外键联系

实例：
CREATE TABLE student6(
student_id VARCHAR(20) NOT NULL PRIMARY KEY,
student_name CHAR(20) NOT NULL,
major VARCHAR(10) NOT NULL, 
CONSTRAINT fk_student_major_info 
FOREIGN KEY (major)
REFERENCES major_info1(major)
) 
>注意：在建表时标注外键与附件时**用()将其框住**而不是用.符号分割！！！


在插入数据时只用一对()即可，
INSERT INTO test.student5
VALUES
('S016','张三','男','软件技术','软件2班','2006-03-23',12345678910,480.8,1000)



```