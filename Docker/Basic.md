<!--
 * @Author: Outsider
 * @Date: 2021-10-31 18:59:36
 * @LastEditors: Outsider
 * @LastEditTime: 2022-10-22 11:19:21
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


### 容器启动
docker run 

### 查看容器运行状态
- docker ps

### 启动已暂停的容器
- docker start [容器ID或容器名]

### 删除和清理容器
- docker rmi <u>image_name</u>

### 删除和清理镜像
- 删除应用  docker image rm [image_name]:[tag]
- 删除所有引用 docker image rm [image_id]

### 清理none镜像
- docker system prune -f

### 重命名容器
- docker rename [old_name] [new_name]

### 重命名tag镜像
- docker tag [image_id] [repo_name]:[tag]
  ```
  命令会创建一个原镜像的应用作为tag
  
  ```