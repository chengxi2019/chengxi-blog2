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
    REFERENCES  (父表字段)

必须先建立父表再建立子表，并在创建子表时建立外键联系
```