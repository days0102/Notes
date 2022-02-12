<!--
 * @Author: Outsider
 * @Date: 2022-02-04 12:20:15
 * @LastEditors: Outsider
 * @LastEditTime: 2022-02-04 12:22:44
 * @Description: In User Settings Edit
 * @FilePath: \Notes\PostgreSQL\AutoIncrement.md
-->


## PostgreSQL 序号自动增长

### 语法
- column_name [serial | smallserial | bigserial]

```SQL
create table table_name(
    id serial
);
```