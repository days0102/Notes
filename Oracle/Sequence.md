<!--
 * @Author: Outsider
 * @Date: 2021-10-30 13:20:54
 * @LastEditors: Outsider
 * @LastEditTime: 2021-10-30 13:37:54
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Oracle\Sequence.md
-->

# 序列

## 创建序列
- CREATE SEQUENCE sequence_name  
  [STRAT WITH start_number]  
  [INCREMENT BY increment_number]  
  [MINVALUE minvalue | NOMINVALUE]  
  [MAXVALUE maxvalue | NOMAXVALUE]  
  [CACHE cache_name | NOCACHE]  -- 内存中预存储的序列号个数，如果不指定数据库突然关闭下次连接是序列号会出现跳号  
  [CYCLE | NOCYCLE]  --是否循环生成序列  
  [ORDER | NOORDER];

## 使用序列
- currval : 获取序列的当前值，sequence_name.currval
- nextval : 获取序列下一个值，sequence_name.nextval

## 删除序列
- DROP SEQUENCE sequence_name;