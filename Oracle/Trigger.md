<!--
 * @Author: Outsider
 * @Date: 2021-11-29 19:48:04
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-29 20:22:16
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Trigger.md
-->
# 触发器

## DML触发器
### 创建触发器
```SQL
CREATE [OR REPLACE] TRIGGER trigger_name BEFORE|AFTER trigger_event[OF column_name] ON table_name
[FOR EACH ROW]--标识行级触发器，如不指定则是语句触发器
[WITH trigger_condition]
DECLARE

BEGIN

EXCEPTION

END;
```
### 行级触发器
- :old  --更新前的值
- :new  --更新后的值
- old,new --WHEN语句中不能使用冒号

|触发事件|:old|:new|
|:--:|:--:|:--:|
INSERT|未定义，所有字段为NULL|语句完成时被插入的数据|
UPDATE|更新前原始记录|语句完成时更新后的数据|
DELETE|记录被删除前的原始值|未定义，所有字段为NULL|
### 条件谓词
- INSERTING :当触发事件时INSERT操作时该谓词返回TRUE，否则为FALSE
- UPDATING : 当触发事件时UPDATE操作时，谓词返回TRUE，否则返回FALSE
- DELETING : 当触发事件是DELETE操作时，谓词返回TRUE，否则返回FALSE