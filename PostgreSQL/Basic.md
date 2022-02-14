<!--
 * @Author: Outsider
 * @Date: 2022-01-15 22:53:12
 * @LastEditors: Outsider
 * @LastEditTime: 2022-02-14 10:15:38
 * @Description: In User Settings Edit
 * @FilePath: \Notes\PostgreSQL\Basic.md
-->
## 进入Postgre
- psql

## 创建数据库
- create database [数据库名]
- 可加项 owner [用户]


## Sql更改列的默认值
### 修改/添加列的默认值
- alter table [table_name] alter column [column_name] [defalut_value]

### 删除列的默认值
- alter table [table_name] alter column [column_name] drop defalut