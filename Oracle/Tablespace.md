# 管理表空间
创建数据库时Oracle会自动创建表空间，如system表空间，如果所有用户使用系统自动创建的表空间，会影响I/O性能
## 创建表空间
- CREATE [TEMPORARY | UNDO] TABLESPACE [表名]   
  (DATAFILE | TEMPFILE [文件名] SIZE [大小] K|M [ REUSE] AUTOEXTEND OFF | ON [ NEXT number K |M MAXSIZE UNLIMITED | number K | M]  
  [...]  
  MININUM EXTENT number K | M  
  [...]
  )