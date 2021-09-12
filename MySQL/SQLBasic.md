# MySQL概要
## SQL书写规则
- SQL语句以分号(;)结尾
- SQL语句关键字不区分大小写
  - 推荐规则: 
    - 关键字大写
    - 表名的所字母大写
    - 其余（列名等）小写
- 插入到表中的数据区分大小写
- SQL语句含有字符串时使用单引号('')将字符串括起来
## 标准SQL命名规则
- 数据库名称、表名和列名等可以使用以下三种字符
  - 半角英文字母
  - 半角数字
  - 下下划线(_)
- 名称必须以半角英文字母作为开头
- 同一个数据库中名称不能重复
## 基本数据类型
- INTEGER型
  - 用来指定存储整数的列的数据类型（数字型），不能存储小数
- CHAR型
  - 用来指定存储字符串的列的数据类型
  - 可以使用CHAR(num)指定字符串的度
  - ex : CHAR(5)   #指定字符串长度5,小于5长度的后面默认补空格。'ABC'为'ABC  '.
- VARVHAR型
  - 可指定字符串长度VARCHAR(num)
  - 可变长字符串
  - ex : VARCHAR(10),'ABC'为'ABC
- DATE型
  - 指定存储日期（年月日）的数据类型
## 查看数据库状态
- status;
```SQL
Connection id:          38
Current database:
Current user:           root@localhost
SSL:                    Cipher in use is TLS_AES_256_GCM_SHA384
Using delimiter:        ;
Server version:         8.0.25 MySQL Community Server - GPL
Protocol version:       10
Connection:             localhost via TCP/IP
Server characterset:    utf8mb4
Db     characterset:    utf8mb4
Client characterset:    gbk
Conn.  characterset:    gbk
TCP port:               3306
Binary data as:         Hexadecimal
Uptime:                 18 hours 34 min 38 sec

Threads: 2  Questions: 7410  Slow queries: 0  Opens: 375  Flush tables: 3  Open tables: 280  Queries per second avg: 0.110
```
# SQL基本语句
## 查看数据库
- SHOW DATABASES;
```SQL
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
```
## 数据库的创建
- CREATE DATABASE [数据库名称];
- ex : CREAT DATABASE shop;
``` SQL
Query OK, 1 row affected (0.01 sec)
```
## 查看数据库定义
1. SHOW CREATE DATABASE [库名];
   - ex : SHOW CREATE DATABASE shop;
```SQL
+----------+--------------------------------------------------------------------------------------------------------------------------------+
| Database | Create Database                                                                                                                |
+----------+--------------------------------------------------------------------------------------------------------------------------------+
| shop     | CREATE DATABASE `shop` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */ |
+----------+--------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```
2. SHOW CREATE DATABASE [库名]\G
   -ex : SHOW CREATE DATABASE shop\G
```SQL
*************************** 1. row ***************************
       Database: shop
Create Database: CREATE DATABASE `shop` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */
1 row in set (0.00 sec)
``` 
## 选择数据库
- USE [库名];
- ex : USE shop;
```SQL
Database changed
```
## 表的创建
- CREATE TABLE <表明>  
  (<列名1> <数据类型> <该列的约束>,  
  <列名2> <数据类型> <该列的约束>,  
  ...........  
  <该表的约束1>,  
  <该表的约束2>,  
  ...........);
- ex :  
  CREATE TABLE Product
   (product_id CHAR(4) NOT NULL,  
   product_name CHAR(100) NOT NULL,  
   product_type VARCHAR(32) NOT NULL,  
   sale_price INTEGER ,  
   purchase_price INTEGER,  
   regist_date DATE,  
   PRIMARY KEY (product_id));
  