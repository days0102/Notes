<!--
 * @Author: Outsider
 * @Date: 2021-10-29 21:25:19
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-07 15:23:44
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\View.md
-->
# 视图

## 查看当前用户所有视图
- SELECT * FROM user_views;

## 创建视图
- CREATE [OR REPLACE] [FORCE | NOFORCE] VIEW view_name AS subquery [WITH {CHECK OPTION | READ ONLY} CONSTRAINT cinstraint_name];
- CHECK OPTION : 可以对视图进行DML操作（实质是在基表上操作）
- subquery : 子查询语句

## 删除视图
- DROP VIEW view_name;