<!--
 * @Author: Outsider
 * @Date: 2021-10-31 18:59:36
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-23 17:45:37
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Docker\Basic.md
-->
## 使用Docker镜像
### 启动docker服务
- systemctl start docker

### 查看镜像信息
- docker images
- docker image ls
```
[lwz@Aliyun ~]$ sudo docker images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    feb5d9fea6a5   5 weeks ago   13.3kB
```
- TAG : 标签消息
- ID : 镜像ID(唯一标识镜像)，如果两个镜像ID相同则实际指向同一个镜像

### 查看镜像详细信息
- docker inspect <u>image_name</u>

### 搜寻镜像
- docker search <u>keyword</u>

### 查看容器运行状态
- docker ps



### 删除和清理镜像
- docker rmi <u>image_name</u>
- docker image rm <u>image_name</u>
