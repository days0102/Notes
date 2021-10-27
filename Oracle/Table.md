<!--
 * @Author: Outsider
 * @Date: 2021-10-08 19:56:42
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-27 15:48:19
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Table.md
-->
# 表

## Oracle中的数据类型
|数据类型|说明|
|:--:|:--:|
|CHAR(长度)|固定长度的字符数据|
|VARCHAR2(长度)|可变长度的字符数据|
|NCHAR(长度)|固定长度的Unicode字符数据|
|NVARCHAR2|可变长度的Unicode字符数据|
|NUMBER<br>NUMBERIC|可变长度数字|
|INT<br>INTEGER<br>SMALLINT|NUMBER 的子类型|
|BINARY_FLOAT|32位浮点数|
|BINARY_DOUBLE|64位浮点数|
|DATE|日期和时间|

---
## 查询当前用户的所有表
- select table_name from user_tables;
- select * from all_tables where owner='[用户名]';#用户名大写
## 创建表
- CREATE TABLE [指定表所属的用户名] [表名] 
  ([列名] [数据类型] [列的默认值(可选)]
  [...]
  )[ TABLESPACE 表空间名];

---
## 管理表
### 增加列
- ALTER TABLE table_name ADD column_name date_type;
### 删除列
- ALTER TABLE table_name DROP COLUMN column_name;
### 修改列的名称
- ALTER TABLE table_name RENAME COLUMN column_name TO new_column_name;
### 修改列的数据类型
- ALTER TABLE table_name MODIFY column_name new_data_type;

### 不使用列
- ALTER TABLE table_name SET UNUSED(column_name,...);
### 使用列
- ALTER TABLE table_name DROP UNUSED COLUMN;

## 重命名表
- ALTER TABLE table_name RENAME TO new_table_name;

## 截断表
- TRUNCATE TABLE table_name;
- 截断表可以把表的所有行删除，截断表无法进行数据撤销
  
## 删除表
- DROP TABLE table_name [CASCADE CONSTRAINTS] [PURGE]
  - CASCADE CONSTRAINTS : 删除表的同时删除所有的这个表的视图、索引等。
  - PURGE : 删除该表后立即释放该表所占用的资源空间。


