# Linux环境下的MySQL(CentOS)
## 设置MySQL开机自启动
- systemctl enable mysqld.service
##  查看是否设置自启动
- systemctl list-unit-files | grep mysqld
```
[root@Aliyun yum.repos.d]# systemctl list-unit-files | grep mysqld
mysqld.service                             enabled
```
## 启动MySQL服务
- systemctl start mysqld.service