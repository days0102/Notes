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

## SQL注释
- 单行注释
  1. -- [注释内容] #--后要有空格
- 多行注释
  1. /* 注释内容 */
   
# SQL基本语句
## MySQL在终端中打开监听器
- 配置环境变量或者切换到MySQL目录下
- mysql -u [用户] -p
```SQL
Enter password: *********
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 49
Server version: 8.0.25 MySQL Community Server - GPL

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```
## 修改MySQL监视器的提示符
- prompt [提示的文本]
  - \d : 数据库名
  - \h : 主机名
  - \u : 用户名
- ex : prompt DB:\d
```
mysql>prompt DB:\d> 
PROMPT set to 'DB:\d>'
DB:shop>
```

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

## 显示当前使用的数据库
- SELECT DATABASE();
```SQL
+------------+
| DATABASE() |
+------------+
| shop       |
+------------+
1 row in set (0.00 sec)
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
   (product_id CHAR(4) NOT NULL,  -- NOT NULL非空约束
   product_name CHAR(100) NOT NULL,  
   product_type VARCHAR(32) NOT NULL,  
   sale_price INTEGER ,  
   purchase_price INTEGER,  
   regist_date DATE,  
   PRIMARY KEY (product_id));  -- 主键约束（唯一标识）product_id
```SQL
Query OK, 0 rows affected (0.06 sec)
```

## 显示所有的表
- SHOW TABLES;
```SQL
+----------------+
| Tables_in_shop |
+----------------+
| product        |
+----------------+
1 row in set (0.01 sec)
```

## 表的删除
- DROP TABLE [表名];
- <u>注：删除的表不能恢复</u>
- ex : DROP TABLE Test;
```SQL
Query OK, 0 rows affected (0.03 sec)
```

## 查看表的基本结构
- DESCRIBE [表名];
- DESC [表名]; #简写
- ex : DESCRIBE Product;
```SQL
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| product_id     | char(4)     | NO   | PRI | NULL    |       |
| product_name   | char(100)   | NO   |     | NULL    |       |
| product_type   | varchar(32) | NO   |     | NULL    |       |
| sale_price     | int         | YES  |     | NULL    |       |
| purchase_price | int         | YES  |     | NULL    |       |
| regist_date    | date        | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
6 rows in set (0.01 sec)
```
- 字段含义
  - NULL: 表示该字段是否可以存储空值
  - KEY: 表示该列是否已经编制索引
    - PRI : 该列是主键的一部分
    - UNI : 该列是UNIQUE索引的一部分
    - MUL : 在列中某个给定的值允许出现多次
  - Default: 表示该列是否有默认值，有则显示值是多少
  - Extra: 表示可以获取的与给定列有关的附加信息，如AUTO_INCREMENT等

## 表的更新
### 添加列
- ALTER TABLE [表名] ADD COLUMN <列的定义>;
  - Oracle和SQL Server中不用写COLUMN
    - ALTER TABLE [表名] ADD <列名>;
  - Oracle中同时添加多列时可用括号括起来
    - ALTER TABLE [表名] ADD (<列名>,<列名>,....);
- ex : ALTER TABLE [表名] ADD COLUMN product_name_pinyin VARCHAR(100);
```SQL
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
### 删除列
- ALTER TABLE [表名] DROP COLUMN <列名>;
  - Oracle和SQL Server中不用写COLUMN
    - ALTER TABLE [表名] DROP <列名>;
  - Oracle中同时添加多列时可用括号括起来
    - ALTER TABLE [表名] ADD (<列名>,<列名>,....);
- **删除后无法恢复**
- ex : ALTER TABLE [表名] DROP COLUMN product_name_pinyin VARCHAR(100);
```SQL
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
## 向表中插入数据
- MySQL : 
  - START TRANSACTION;
  - INSERT INTO [表名] VALUES(与列名对应的数据);
    - ex : INSERT INTO Product VALUES('0001','T恤衫','衣服',1000,500,'2020-09-12',NULL);
  - 指定列名插入
    - INSERT INTO [表名] [列名1,列名2......] VALUES(数据1,数据2......);
- SQL Server 和PostgreSQL :
  - BEGIN TRANSACTION;

## 更改表名
- MySQL : 
  - RENAME TABLE [旧表名] to [新表名];
  - ex : 

## 更新数据
- UPDATE [表名] SET [列名]=[值],[列名]=[值],... WHERE [指定更新的记录需要满足的条件];
- ex :
  ```
  mysql> UPDATE Product SET sale_price=3 WHERE product_id=0007; 
  Query OK, 1 row affected (0.01 sec)
  Rows matched: 1  Changed: 1  Warnings: 0
  ```

  