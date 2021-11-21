# 用户权限与安全
## 用户
---
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
---
### 终止用户会话
---
## 用户配置文件
### 创建用户配置文件
- CREATE PROFILE [文件名] LIMIT  
  (...)

### 使用配置文件
- ALTER USER [用户名] PROFILE [配置文件名];

---
## 权限
---
### 系统权限
- 系统权限指整个Oracle系统的操作权限
- 系统权限一般由数据库管理员授予用户，并允许用户将被授予的权限授予其它用户
- GRANT [系统权限,系统权限,...] TO [用户|角色|PUBLIC]   --PUBLIC表示系统中所有的用户  
  (WITH ADMIN OPTION --指定该项被授予的用户可以再将该权限授予其它用户  
  );
```SQL
SQL> GRANT CREATE SESSION TO mytest;
授权成功。
```
### 查看用户的系统权限
- 通过数据词典user_sys_privs查看
  - username: 当前用户的用户名
  - privilege: 当前用户拥有的系统权限
  - admin_option: 当前用户是否有权利将该权限授予其它用户
```SQL
MYTEST	CREATE TABLE	NO
MYTEST	CREATE SESSION	NO
MYTEST	CREATE VIEW	NO
```

### 撤销系统权限
- REVOKE [系统权限,系统权限,...] TO [用户|角色|PUBLIC];
### 撤销系统权限对一些相关对象的影响
1. 假设管理员SYS将SELECT ANY TABLE系统权限授予个用户rose,所以rose是可以查看其他所有用户名下的对象的，此时rose创建了一个过程或视图，在其中使用了用户donna的数据表，那么在撤销了这个权限后，这些过程或视图将无效。
2. 如果系统管理员SYS和SYSTEM都将同一个系统权限授予个rose,如果SYS回收了这个系统权限时，rose还是继续拥有这个系统权限，因为SYSTEM赋予的权限还在生效。
### 撤销系统权限时的级联问题
1. 撤销系统权限时没有级联效果，这与该系统权限是否使用ADMIN OPTION授权无关。
2. 假设数据库管理员SYS使用ADMIN OPTION将系统权限CREATE TABLE赋予了rose,rose马上创建了一个表，并将CREATE TABLE这个权限赋予donna,donna也创建了一个表，此时SYS撤销了rose的CREATE TABLE权限，那么结果是rose原来创建的表仍然存在，但不能再创建表了，而donna的表也仍然存在，而且可以继续创建新表。



## 对象权限
### 对象权限数据词典
- user_tab_privs:已授权的对象权限信息
  - GRANTEE:权限所授予的用户
  - TABLE_NAME:权限所针对的对象
  - GRANTOR:授权者
  - PRIVILEGE:所授予的对象权限
  - GRANTABLE:是否可以将该权限授予其他用户
  - HIERARCHY:权限是否构成层次关系

### 授予对象权限
- GRANT object_privilege,...| ALL [PRIVILEGE] ON <schema.>object_name TO user_name,...|role_name,...|PUBLIC [WITH GRANT OPTION];

### 列对象上的权限（针对INSERT,UPDATE,REFERENCES）
- object_privilege(column_name,...)
```SQL
GRANT UPDATE(a,b) ON emp TO user;--将更新emp表上的a,b列的权限授予user
```
### 撤销对象权限
- REVOKE object_privilege,...|ALL [PRIVILEGE] ON <schema.>object_name FROM user_name,...|role_name,...|PUBLIC;

### 撤销权限时的级联问题
1. 如果对象权限是用WITH GRANT OPTION授予的，则撤销对象权限也将导致级联撤销
   
## 角色
### 创建角色
- CREATE ROLE [角色名] (NO IDENTIFIED | IDENTIFIED BY [密码]);
```SQL
SQL> CREATE ROLE myrole IDENTIFIED BY l27;

角色已创建。
```
### 为角色授予权限
- GRANT [权限,权限,...] TO [角色];

### 将角色授予用户
- GRANT [角色] TO [用户];
