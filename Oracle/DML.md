<!--
 * @Author: Outsider
 * @Date: 2021-11-07 16:17:39
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-07 16:38:47
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\DML.md
-->
# 数据操纵

## 数据插入INSERT
- INSERT INTO table_name[(column1,column2...)] VALUES(values1,valuess2...);
  - 列与值要相对应
  - 省略的列名会自动设置成默认值（没有设默认值则为NULL）

## 从其他表中插入数据
- INSERT INTO table_name1(cloumn1,clumn2...) SELECT column1,column2... FROM table_name2;
  - SELECT语句可以使用WHERE子句等SQL语法

## 数据删除
- DELETE FROM table_name;
  - 清空表

- DELETE FROM table_name WHERE condition;
  - 删除指定数据

## 数据更新
- UPDATE table_name SET column_name=column_value；
  - 更新所有数据
- UPDATE tale_name SET column_name=column_value WHERE condition;
  - 更新指定数据