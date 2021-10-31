<!--
 * @Author: Outsider
 * @Date: 2021-10-30 13:56:55
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-31 15:30:40
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\SQLBasic.md
-->
# SQL语言基础
## DML
|DML语言|功能|
|:--:|:--:|
|SELECT|从表或视图中检索数据行|
|INSERT|插入数据到表或视图|
|UPDATE|更新|
|DELETE|删除|
|CALL|调用过程|
|MERGE|合并（插入或修改）|
|COMMIT|将当前事务所做的更改永久化（写入数据库）|
|ROLLBACK|取消上次提交以来的所有更改|
## DDL
|DDL语言|功能|
|:--:|:--:|
|CREATE|创建数据库结构|
|ALTER|修改数据库结构|
|DROP|删除数据库结构|
|RENAME|更改数据库对象的名称|
|TRUNCATE|删除表中的所有内容|
## DCL
DCL语言|功能
:--:|:--:
GRANT|授予其他用户对数据库结构的访问权限
REVOKE|收回用户访问数据库结构的权限

## SELECT
- SELECT [ALL | DISTINCT ] 
  {* | expression | column1_name [,...] }   
  FROM {table1_name | (subquery)} [alias]  
  [, {table2_name | (subquery)} [alias]...  ]
  [WHERE condition]  
  [CONNECT BY condition [ START WITH condition]]  
  [GROUP BY expression [...] ]  
  [HAVING condition [,...]]  
  [ { UNION | INTERSECT | MINUS }]  
  [ORDER BY expression [ ASC | DESC] [,...]]  
  [FOR UPDATE [OP [schema.]table_name | view] column] [NOWAIT];
- DISTINCT ：去掉重复值
- alias ：别名
- START WITH ：查询的开始条件
- GROUP BY ：将列分组
- HAVING ：对分组了的列进行筛选
- UNION | INTERSECT | MINUS ：分别标识联合、交和差操作
- ORDER BY ：查询结果的排序
- ASC ：升序
- DESC ：降序
- [FOR UPDATE [OP [schema.]table_name | view] column] [NOWAIT] ：查询时将表锁住不让其他用户进行DML操作


## WHERE条件中可以使用的操作符
比较符|说明
:--:|:--:
=|等于
<>、!=|不等于
<=|小于等于
\>=|大于等于
\>|大于
<|小于
ANY|与一个列表中的任何值比较
ALL|与一个列表中的所有值比较
BETWEEN|指定条件在两个值之间（包含边界值）
LIKE|匹配字符样式
IN|匹配的一个列表值
IS NULL|匹配空值

## ORDER BY 
- 用于对查询结果进行排序
- 可以同时对多列进行排序

## GROUP BY 
- 将表中的列进行分组
- 列中有多少种不同的数据就会分成多少组
- 对列分组后可以使用聚合函数进行数据统计

## HAVING
- 如果使用了GROUP BY ，则HAVING将应用于GROUP BY子句创建的组
- 如果使用了WHERE而没有使用GROUP BY，则HAVING 将应用于WHERE子句的输出，这个输出被看作一个组
- 如果没有使用WHERE子句和GROUP BY子句，则HAVING将应用于FROM子句的输出，这个输出被看作一个组

## DISTINCT
- 用于限定检索结果不出现重复的数据

