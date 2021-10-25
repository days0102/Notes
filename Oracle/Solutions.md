<!--
 * @Author: Outsider
 * @Date: 2021-10-25 15:27:03
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-25 16:06:41
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Solutions.md
-->
# Oracle问题解决方法
---
## 对表空间 'SYSTEM' 无权限
```SQL
在行: 3 上开始执行命令时出错 -
CREATE TABLE Student
(
  Sno CHAR(9) PRIMARY KEY,--完整性约束条件
  Sname CHAR(20) UNIQUE,
  Ssex CHAR(3), 
  Sage SMALLINT, 
  Sdept CHAR(20)
)
错误报告 -
ORA-01950: 对表空间 'SYSTEM' 无权限
01950. 00000 -  "no privileges on tablespace '%s'"
*Cause:    User does not have privileges to allocate an extent in the
           specified tablespace.
*Action:   Grant the user the appropriate system privileges or grant the user
           space resource on the tablespace.

```
## 解决办法
- GRANT CONNECT,RESOURCE TO [用户];
  - CONNECT和RESOURCE是系统内置的两个角色
  - CONNECT ：拥有CONNECT权限的用户只可以登录Oracle，不可以创建实体，不可以创建数据库结构。
  - RESOURCE ：拥有Resource权限的用户只可以创建实体，不可以创建数据库结构。
```markdown
CONNECT角色：    --是授予最终用户的典型权利，最基本的  
   
   ALTER    SESSION    --修改会话  
   CREATE    CLUSTER    --建立聚簇  
   CREATE    DATABASE    LINK    --建立数据库链接  
   CREATE    SEQUENCE    --建立序列  
   CREATE    SESSION    --建立会话  
   CREATE    SYNONYM    --建立同义词  
   CREATE    VIEW    --建立视图  

RESOURCE角色：    --是授予开发人员的  
   
   CREATE    CLUSTER    --建立聚簇  
   CREATE    PROCEDURE    --建立过程  
   CREATE    SEQUENCE    --建立序列  
   CREATE    TABLE    --建表  
   CREATE    TRIGGER    --建立触发器  
   CREATE    TYPE    --建立类型
```

