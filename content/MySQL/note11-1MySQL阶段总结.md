---
tiile: note11-1MySQL阶段总结
created: 2026-10-30 13:16:23
tag:     
---


在除了字符类型的字段（CHAR,VARCHAR）以外的字段在插入空值时要使用NULL来代替，不可使用' ',这是字符类似专用的

UPDATE 语句用法：
``` sql
UPDATE student5
SET scholarship = 500
WHERE student_id = 'S016'
```

删除语句用法：
``` sql
DELETE FROM test.student5
WHERE student_id IN ('S016','S017','S018','S019')
```

外键的删除与修改，先删除再修改：
``` sql
ALTER TABLE test.student5 DROP FOREIGN KEY fk_student1_major;

ALTER TABLE test.student5 
ADD CONSTRAINT fk_student5_major_correct 
FOREIGN KEY (major) REFERENCES correct_major_table(major);
```
排序与分页
``` sql
SELECT * FROM student5
ORDER BY entrance_score DESC
LIMIT 5,2
```