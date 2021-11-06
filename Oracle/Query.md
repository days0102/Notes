<!--
 * @Author: Outsider
 * @Date: 2021-10-31 15:40:17
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-06 19:06:56
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Query.md
-->

# SQL查询

## SQL多表连接查询

### EXISTS查询


### 内连接
- FROM join_table1 jion_type join_table2 [ON (join_condition)] [join_type ... ON join_condition , ...];
- join_table : 参与连接的表名
- join_type : 连接类型
  - INNER JOIN : 内连接
  - OUTER JOIN : 外连接
  - CROSS JOIN : 交叉连接
- join_condition : 连接条件
> 等值连接：连接条件使用=运算符比较被连接的值  
> 不等连接：连接条件使用=运算符之外比较被连接的值  
> 自然连接：使用NATURAL JOIN而不需要指定连接条件  

### 笛卡儿积
- SELECT column_name1,column_name2 [,...] FROM table_name1,table_name2 [,...];

### 集合的并运算(UNION)
-  select_statement UNION [ALL] select_statement [UNION [ALL] select_statement] [...]
-  select_statement为查询的SELECT语句
-  指定ALL则包括指定的行，不指定则重复的行只保留一行
- 进行集合的并运算要所选属性列相同

### 集合的交运算(INTERSECT)
-  select_statement INTERSECT select_statement [UNION select_statement] [...]
-  select_statement为查询的SELECT语句
- 进行集合的交运算要所选属性列相同

### 集合的差运算
-  select_statement MINUS select_statement [MINUS select_statement] [...]
-  select_statement为查询的SELECT语句
- 进行集合的差运算要所选属性列相同