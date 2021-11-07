<!--
 * @Author: Outsider
 * @Date: 2021-11-07 14:13:56
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-07 16:07:30
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Constraints.md
-->

# 表的完整性约束条件

## 查看所有约束
- SELECT * FROM user_constraints;

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
> 唯一约束多个NULL值可以同时存在
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
- 删除主键约束
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
```SQL
studentsex CHAR(2) CHECK(studentsex IN('男','女'));--学生性别列在男女之间选
```
- 删除CHECK约束
  - ALTER TABLE table_name DROP CHECK(column_name);

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

