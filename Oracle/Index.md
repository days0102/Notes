<!--
 * @Author: Outsider
 * @Date: 2021-10-29 21:15:35
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-29 21:24:59
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Index.md
-->
# 索引

## 创建B树索引
- CREATE [UNIQUE] INDEX index_name ON table_name(column_name [,...]);
- UNIQUE:要求索引列的值必须时唯一的，如果该列已经定义了UNIQUE约束则不需要指定。


## 管理索引
### 重命名索引
- ALTER INDEX index_name RENAME TO new_index_name;

### 合并索引
- ALTER INDEX index_name COALESCE [DEALLOCATE UNUSER];

### 删除使用CREATE INDEX创建的索引
- DROP INDEX index_name;

