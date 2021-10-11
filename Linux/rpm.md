# rpm软件包管理命令yum(CentOS)

## 包全名和包名
- 包全名：操作没有安装的软件包使用包全名
- 包名：操作已经安装的软件包使用包名。搜索/var/lib/rpm中的数据库
```/var/lib/rpm
[lwz@Aliyun rpm]$ ls
Basenames     Dirnames         Name           Requirename     Transfiletriggername
Conflictname  Enhancename      Obsoletename   Sha1header      Triggername
__db.001      Filetriggername  Packages       Sigmd5
__db.002      Group            Providename    Suggestname
__db.003      Installtid       Recommendname  Supplementname
```
## RPM包依赖
- 树形依赖
- 环形依赖
- 模块依赖
## RPM 安装
- rpm -ivh [包全名]
  - -i (install) 安装
  - -v (verbose) 显示详细信息
  - -h (hash)    显示进度
  - --nodeps     不检测依赖性(可能安装不完全，软件功能缺失)
## RPM包升级
- rpm -Uvh [包全名]
  - U (upgrade) 升级
## RPM卸载
- rpm -e [包名]
  - -i(erase) 卸载
  - --nodeps  不检查依赖项(不完全卸载)
---
## 查询RPM
- rpm -q [包名]
  - -q (query) 查询
- rpm -qa
  - -a (all) 查询所有已安装的rpm包
- rpm -qi [包名]
   - -i (information) 查询软件信息
   - -p (package) [包全名] 查询未安装包信息
- rpm -ql [包名]
   - -l (list) 列表 查询rpm包文件
   - -p (package) 未安装包
- rpm -qf [系统文件名]
   - -f (file) 查询系统文件属于哪个包
- rpm -qR [包名]
  - -R (requires) 查询软件包的依赖项
  - -p (package) 未安装包信息
## RPM包校验（查看软件包文件是否被修改过）
- rpm -V [包名]
  - -V (verify) 检验指定rpm包中的文件
  - 验证内容8个信息是否改变
    - S 文件大小
    - M 文件类型或文件权限(rwx)
    - 5 文件MD5校验（可以看成文件内容）
    - D 设备主从代码
    - L 文件路径
    - U 文件所有者
    - G 文件属组
    - T 文件的修改时间
---
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
## 生成Yum缓存
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
## yum查询
- yum list #查询所有可用的软件包
- yum search [关键字]  #搜索软件包
  
## yum安装
- yum install [包名]
  - -y 自动回答yes
## yum升级
- yum update [包名]
  - -y 
## yum卸载
- yum remove [包名]
  - -y
## 软件组管理命令
- yum grouplist #列出所有可用的软件组列表
- yum groupinstall [软件组名] #安装指定的软件组（软件组名有空格要用""括起来）
- yum groupremove [软甲组名] #卸载软件组（软件组名有空格要用""括起来）