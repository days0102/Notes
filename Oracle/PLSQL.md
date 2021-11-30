<!--
 * @Author: Outsider
 * @Date: 2021-11-29 15:50:39
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-29 19:43:27
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\PLSQL.md
-->
# PL/SQL编程基础

## 块结构
```SQL
DECLARE --定义部分
    declaretions --主要定义常量变量数据类型游标异常处理名称等
BEGIN --执行部分
    executable code
EXCEPTION --异常处理部分
    exceptional handlers
END; --结束标识
```

## 匿名块
- 动态生成，只能执行一次的块
- 没有名字，不能由其他应用程序调用
```SQL
SET SERVEROUTPUT ON--将SQL*PLUS的环境变量设为ON
BEGIN
    --使用Oracle系统包DBMS_OUTPUT的PUT_LINE()输出字符串
    DBMS_OUTPUT.PUT_LINE('!');
END;
```

## 命名块
- 一次编译可以多次执行的PL/SQL程序
- 包括自定义的函数、过程、包、触发器等

## 基本语法
### 字符集
- PL/SQL字符集不区分大小写
### 标识符
- 如果标识符区分大小写、使用预留关键字或包含空格等特殊字符时，需要使用""括起来，称为引证标识符

## 变量
### LOB变量
- %TYPE定义变量
  - v table_column %TYPE 
  - --与table_column列类型一样
- %ROWTYPE
  - v tavle %TYPE 
  - --与table表定义的数据类型一致

## PL/SQL中执行SQL语句
### SELECT
- SELECT experssion INTO variable FROM table WHERE condition;
- 该语句只能返回一行数据，如果返回多行会产生TOO_MANY_ROW异常，如果没有返回数据会产生NO_DATA_FOUND

### DML
- INSERT INTO table[(column...)] VALUES(val..);  --插入一条
- INSERT INTO table[(column...)] AS subquery; --插入多条数据
- UPDATE table SET column=val ... WHERE condition;
- DELETE FROM table WHERE condition;



## 过程Procedure
```SQL
CREATE [OR REPLACE] PROCEDURE procedure_name(argument1 [model1] data_type,...)
IS [AS]
PL/SQL BLOCK;
```
- IN : 默认输入参数
- OUT : 输出参数
- IN OUT : 输入输出参数

### 查看过程源代码
- SELECT text FROM user_source WHERE name='procedure_name';

### 执行过程
- EXEC procedure_name(argument...);
1. 位置传参：调用时按照参数定义顺序依次传参
2. 名称传参：调用时指定参数名，使用=>提供参数
   - EXECT PROCE(name=>'Lin');
3. 组合传参：调用使用位置传参和名称传参