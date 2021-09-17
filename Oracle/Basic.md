# Oracle 基本操作SQLPLUS
## 查看当前用户
- SHOW USER;
## 创建用户
- CREATE USER [用户名] identified by [密码];
- 新创建的用户是没用任何权限的，甚至连登录的权限也没有
## 登录用户
- CONN [用户名];
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