<!--
 * @Author: Outsider
 * @Date: 2022-02-14 15:33:00
 * @LastEditors: Outsider
 * @LastEditTime: 2022-02-14 15:44:21
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Docker\Nginx.md
-->

# Docker 使用Nginx

- 拉取最新版本的Nginx
- docker pull nginx

## 使用Nginx配置图片服务器

### 创建一个存放静态资源的目录，在外部的服务器文件目录下(建议不要使用 root 权限，不好使用 xftp 上传文件 )
- mkdir /home/zyy/images
### 创建并编辑 nginx.conf
- vim nginx.conf

### 写入内容
```
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   /images;
            index  index.html index.htm;
        }
    }

    include /etc/nginx/conf.d/*.conf;
}
```

### 运行Nginx镜像
- docker run --name [container_name] -p [out_part]:80 -v [容器外部存放图片的绝对路径]:/images -v [存放nginx.conf文件夹/nginx.conf]:/etc/nginx/nginx.conf -d nginx
```
# --name 实例名
# -p 是端口映射，80是 nginx 容器的默认端口，映射到主机的端口，也就是访问宿主机的端口，就会自动跳转到 nginx 容器的 80 端口，也就是 nginx 的入口
# -v 是挂载目录，它会让容器和宿主机共享目录，我们把静态资源放在 容器外部存放图片的绝对路径，容器内的路径 /images 也会更新静态资源
# 由于容器内没有 vim 和 vi ，甚至没有 yum ，所以我们无法在容器内修改，那么可以选择 将外部的 nginx 配置文件覆盖容器内的配置文件
```
