# Oracle 基本操作SQLPLUS
## Oracle数据词典
Oracle数据词典是存储在数据库中所有对象信息的知识库
- USER视图: 用来记录用户对象的信息，以user_为前缀
- ALL视图: 记录用户对象的信息以及被授权访问的对象信息，以all_为前缀
- DBA视图: 记录数据库实例的所有对象的信息，以dba_为前缀
- V$视图: 记录与数据库活动相关的性能统计动态信息，以v$为前缀
- GV$视图: 记录分布式环境下所有实例的动态信息，以gv$为前缀
```SQL
SQL> SELECT table_name,owner FROM dba_tables WHERE /*table_name表示表名，owner表示拥有者*/owner='TEST'; 

TABLE_NAME
------------------------------------------------------------
OWNER
------------------------------------------------------------
ADDRESSBOOK
TEST 
```
## 查看当前用户
- SHOW USER;
## 创建用户
- CREATE USER [用户名] identified by [密码];
- 新创建的用户是没用任何权限的，甚至连登录的权限也没有
## 登录用户
- CONN [用户名];
## 退出用户
- DISCONN;
## 授予用户权限
- 登录system用户
- 使用GRANT授予权限
- GRANT CONNECT TO [用户名];
```
SQL> GRANT CONNECT TO test;

授权成功。
```
## 查看当前用户的权限
- SELECT * FROM SESSION_PRIVS;
## 授予用户权限
- GRANT CREATE TABLE TO [用户];/*授予创建表的权限*/
// - GRANT ALL TO [用户];/*授予所有的权限给用户*/
- GRANT UNLIMITED TABLESPACE TO [用户];/*授予用户使用表的权限*/

## 查看用户表的结构
- DESC [用户].[表名];
```SQL
SQL> DESC test.Addressbook;  
 名称                                      是否为空? 类型
 ----------------------------------------- -------- ----------------------------
 REGIST_NO                                 NOT NULL NUMBER(38)
 NAME                                      NOT NULL VARCHAR2(128)
 ADDRESS                                   NOT NULL VARCHAR2(256)
 TEL_NO                                             CHAR(10)
 MAIL_ADDRESS                                       CHAR(20)
```

