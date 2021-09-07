# Linux驱动开发环境
## Linux内核(Ubuntu)
>使用命令查看内核版本
- uname -r
>Linux内核源码
- [官网](https://www.kernel.org)
- Linux系统文件：/usr/src/
>如果内核版本破折号后有内容，则官网没有相应的版本下载，要使用发行版供应商提供的内核版本
---
## 编译内核
1. 解压Linux内核文件，进入解压后的目录
2. make oldconfig
    >问题：flex : not found  
    解决：安装flex
    >- apt install flex
    ---
    >问题：bison : not found 
    解决：安装bison
    >- apt install bison  

    完成：
    ![](2021-08-29%20111608.jpg)

3. 