<!--
 * @Author: Outsider
 * @Date: 2021-11-23 17:37:25
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-23 18:00:48
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Docker\Docker_Oracle.md
-->
## Docker下安装Oracle
1. 拉取镜像
- docker pull registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g
2. 启动容器
- 默认启动 docker run -d -it -p 1521:1521 --name oracle11g --restart=always registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g
- 持久化启动 docker run -d -it -p 1521:1521 --name oracle --restart=always --mount source=oracle_vol,target=/home/oracle/app/oracle/oradata registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g
3. 进入容器
- docker exec -it [image_id | image_name] bash
4. Linux切换至root
- su
5. 修改/etc/profile
- 添加
```
export ORACLE_HOME=/home/oracle/app/oracle/product/11.2.0/dbhome_2
export ORACLE_SID=helowin
export PATH=$ORACLE_HOME/bin:$PATH
```
- source /etc/profile
6. 切换至oracle,登录sqlplus
- su - oracle

- sqlplus /nolog

- conn /as sysdba