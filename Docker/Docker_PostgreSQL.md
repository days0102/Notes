<!--
 * @Author: Outsider
 * @Date: 2022-01-15 22:36:02
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-15 22:39:24
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Docker\Docker_PostgreSQL.md
-->

## Docker 配置PostgreSQL

### 运行
- docker run --name postgres -e POSTGRES_PASSWORD=[passwowd] -p [本地端口]:5432 -d postgres
  -  POSTGRES_PASSWORD : 指定初始密码

### 进入PostgreSQL镜像
- docker exec -it postgres bash

### psql
- psql -U postgres -W
 - -U:用户
 - -W:使用密码登录