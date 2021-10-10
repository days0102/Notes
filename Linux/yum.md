# 软件包管理命令yum(CentOS)
## 配置Yum源
- Yum源的配置文件在/etc/yum.repos.d/目录中
```
[root@Aliyun yum.repos.d]# cd /etc/yum.repos.d/
[root@Aliyun yum.repos.d]# ll
total 60
-rw-r--r-- 1 root root  728 Aug 24 16:04 CentOS-Linux-AppStream.repo
-rw-r--r-- 1 root root  713 Aug 24 16:04 CentOS-Linux-BaseOS.repo
-rw-r--r-- 1 root root 1139 Aug 24 16:04 CentOS-Linux-ContinuousRelease.repo
-rw-r--r-- 1 root root  318 Aug 24 16:04 CentOS-Linux-Debuginfo.repo
-rw-r--r-- 1 root root  741 Aug 24 16:04 CentOS-Linux-Devel.repo
-rw-r--r-- 1 root root  226 Aug 24 16:04 CentOS-Linux-epel.repo
...
```
## 下载Yum源文件
- wegt [源文件地址]
```
[root@Aliyun yum.repos.d]# wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo
--2021-10-10 15:59:23--  https://mirrors.aliyun.com/repo/Centos-8.repo
Resolving mirrors.aliyun.com (mirrors.aliyun.com)... 14.215.172.219, 14.215.172.221, 14.215.172.217, ...
Connecting to mirrors.aliyun.com (mirrors.aliyun.com)|14.215.172.219|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2595 (2.5K) [application/octet-stream]
Saving to: ‘/etc/yum.repos.d/CentOS-Base.repo’

/etc/yum.repos.d/CentOS-Base. 100%[===============================================>]   2.53K  --.-KB/s    in 0s      

2021-10-10 15:59:24 (65.3 MB/s) - ‘/etc/yum.repos.d/CentOS-Base.repo’ saved [2595/2595]
```
## 生成缓存
- yum makecache
```
[root@Aliyun yum.repos.d]# yum makecache
Repository extras is listed more than once in the configuration
CentOS-8 - Base - mirrors.aliyun.com                                                   15 MB/s | 7.5 MB     00:00    
CentOS-8 - Extras - mirrors.aliyun.com                                                 32 kB/s |  10 kB     00:00    
CentOS-8 - AppStream - mirrors.aliyun.com                                              18 MB/s | 9.3 MB     00:00    
CentOS Linux 8 - AppStream                                                            115 kB/s | 4.3 kB     00:00    
CentOS Linux 8 - BaseOS                                                                99 kB/s | 3.9 kB     00:00    
Extra Packages for Enterprise Linux 8 - x86_64                                        112 kB/s | 4.7 kB     00:00    
MySQL Connectors Community                                                            3.4 kB/s | 2.6 kB     00:00    
MySQL Tools Community                                                                 3.3 kB/s | 2.6 kB     00:00    
MySQL 5.7 Community Server                                                            3.4 kB/s | 2.6 kB     00:00    
Metadata cache created.
```