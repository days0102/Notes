# 用户权限与安全
## 用户
### 创建用户
- CREATE USER [用户名] IDENTIFIED BY [密码] 
  ( DEFAULT TABLESPACE [默认表空间名称] --不指定默认为system  
    TEMPORARY TABLESPACE [默认临时表空间名称] --不指定默认为temp  
    QUOTA [空间大小] ON [表空间] --默认为UNLIMITED  
    [用户配置文件名称] --默认为DEFAULT  
    [PASSWORD EXPIRE] --设置口令为过期，登录时强制修改口令  
    ACCOUNT [LOCK/UNLOCK] --默认为UNLOCK  
    ....... --省略其它  
  );
```SQL
SQL> CREATE USER mytest IDENTIFIED BY l27 DEFAULT TABLESPACE users QUOTA 20M ON users;
SP2-0640: 未连接
SQL> conn system
输入口令: 
已连接。
SQL> CREATE USER mytest IDENTIFIED BY l27 DEFAULT TABLESPACE users QUOTA 20M ON users;

用户已创建。
```
---
### 修改用户
- ALTER USER [用户名] [...]
```SQL
SQL> ALTER USER mytest PASSWORD EXPIRE; --修改用户口令为过期                    

用户已更改。
SQL> conn mytest;
输入口令: 
ERROR:
ORA-28001: the password has expired

更改 mytest 的口令
新口令:
重新键入新口令:
口令已更改
已连接。
```
---
### 删除用户
- DROP USER [用户名] (CASCADE);
- 如果用户已经在数据中创建了数据，则要指定CASCADE关键字，表示删除用户时同时删除用户创建的内容
```SQL
SQL> DROP USER test;
DROP USER test
*
第 1 行出现错误:
ORA-01922: 必须指定 CASCADE 以删除 'TEST'


SQL> DROP USER test CASCADE; 

用户已删除。
```
---
### 管理用户会话
