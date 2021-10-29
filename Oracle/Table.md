<!--
 * @Author: Outsider
 * @Date: 2021-10-08 19:56:42
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-29 21:02:18
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


## 表的完整性约束
|约束|说明|
|:--:|:--:|
|NOT NULL|非空约束，不允许存储空值|
|PRIMART KEY|主键约束，唯一表示表中的一行|
|UNIQUE|唯一约束，指定列只能存储唯一的值|
|CHECK|检查约束，指定列必须满足某种条件|
|FOREIGN KEY|外键约束，引用另一个表中的一列或本表中的一列|

### NOT NULL 约束
> 指定该列的数据不能为空值
- 添加NOT NULL 约束
  - 创建表示添加，在添加列时标注
     - column_name data_type [CONSTRAINT constraint_name] NOT NULL;
     - constraint_name为指定的约束名称
   - 已创建的表中添加NOT NULL 约束
     - ALTER TABLE table_name MODIFY column_name [CONSTRAINT constraint_name] NOT NULL;
- 删除NOT NULL 约束
  - ALTER TABLE table_name MODIFY column_name
  NULL;

### UNIQUE约束
> 唯一约束，要求约束的列的值不能重复或列组合中的值不全相同。
- 添加UNIQUE约束
  - 创建表示添加，在添加列时标注
     - column_name data_type [CONSTRAINT constraint_name] UNIQUE;
     - constraint_name为指定的约束名称
  - 已创建的表中添加NOT NULL 约束
     - ALTER TABLE table_name ADD  [CONSTRAINT constraint_name] UNIQUE(column_name);
- 删除UNIQUE约束
  - ALTER TABLE table_name DROP UNIQUE(column_name);

### PRIMARY KEY约束
> 主键约束用于唯一标识一行记录。约束的列或列组合不能有重复值，也不能有空值。
- 添加PRIMARY KEY约束
  - 创建表时添加，在添加列时标注
     - column_name data_type [CONSTRAINT constraint_name] PRIMARY KEY;
     - constraint_name为指定的约束名称
  - 已创建的表中添加NOT NULL 约束
     - ALTER TABLE table_name ADD  [CONSTRAINT constraint_name] PRIMARY KEY(column_name);
- 删除UNIQUE约束
  - ALTER TABLE table_name DROP PRIMARY KEY;
  - 使用指定约束名的方式删除
  - ALTER TABLE table_name DROP CONSTRAINT constraint_name;
    - 如果在添加约束时使用CONSTRAINT指定了约束名constraint_name,则可以直接使用
    - 如果没有使用使用CONSTRAINT指定constraint_name，则约束名由Oracle自动创建
    - Oracle自动创建的约束名可以通过user_cons_column和user_constraints数据字典查看
      - DESC user_cons_columns;
      - DESC user_constraints;
```SQL
SQL> DESC user_cons_columns; 
 名称                                      是否为空? 类型
 ----------------------------------------- -------- ----------------------------
 OWNER                                     NOT NULL VARCHAR2(30)
 CONSTRAINT_NAME                           NOT NULL VARCHAR2(30)
 TABLE_NAME                                NOT NULL VARCHAR2(30)
 COLUMN_NAME                                        VARCHAR2(4000)
 POSITION                                           NUMBER
 ```

 ### CHECK约束
 > 检查约束用于指定一个条件，符合条件的数据才允许赋值
 - 添加CHECK约束
  - 创建表示添加，在添加列时标注
     - column_name data_type [CONSTRAINT constraint_name] CHECK(check_condition);
     - constraint_name为指定的约束名称
  - 已创建的表中添加CHECK约束
     - ALTER TABLE table_name ADD  [CONSTRAINT constraint_name] CHECK(check_condition);
<!-- - 删除CHECK约束
  - ALTER TABLE table_name DROP CHECK(column_name); -->

### FOREIGN KEY约束
>外键约束，用于引用本表中或另一个表的一列或一组列
>外键约束特点：
>- 被引用的列或列组应该具有主键约束或唯一约束
>- 引用列的取值只能为被引用列的值或null值
>- 引用列中存储了被引用列中的值，不能直接删除被引用列的值
- 添加FOREIGN KEY约束
  - 创建表时添加
    - colunm_name data_type [CONSTRAINT constraint_name] REFERENCES table_name(column_name) 
    - REFERENCES关键字用于定义引用列指向被引用列column_name
  - 已创建表后添加
  - ALTER TABLE table_name1 ADD [CONSTRAINT constraint_name] FOREION KEY(column_name1) REFENCES table_name2(column_name2);

## 禁止或激活约束
- 创建表时设置
  - column_name date_type [CONSTRAINT constraint_name] constraint_type <u>DISABLE  |  ENABLE</u>;
- 已创建表后设置
  - ALTER TABLE table_name <u>ENABLE | DISABLE</u> CONSTRAINT constraint_name;
  - ALTER TABLE table_name MODIFY CONSTRAINNT constraint_name <u>ENABLE | DISABLE</u>;

