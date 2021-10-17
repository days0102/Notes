# 表
## 查询当前用户的所有表
- select table_name from user_tables;
- select * from all_tables where owner='[用户名]';#用户名大写
## 创建表
- CREATE TABLE [指定表所属的用户名] [表名] 
  ([列名] [数据类型] [列的默认值(可选)]
  [...]
  )[ TABLESPACE 表空间名];
- 