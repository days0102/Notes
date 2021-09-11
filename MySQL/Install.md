# MySQL安装
## 下载MySQL_Install_community
---
## 安装选项 :
## Choosing a Setup Type
- 选择Custom(自定义安装)  
![](2021-09-11%20191442.jpg)  
## Select Products
- 选择MySQL Server、MySQL Doucument、Samples and Examples（<u>点中选项后点击绿色箭头</u>）
![](2021-09-11%20191722.jpg)
## 执行安装
---
## 配置MySQL :
## Type and Networking 
- Development computer (开发机器) : 代表典型个人用桌面工作站，占用系统资源比较少(推荐)
- Server computer(服务器) : 代表服务器，MySQL可以和其它应用程序一起运行。MySQL服务器配置成使用适当比例的系统资源
- Dedicated computer(专用服务器) : 只运行MySQL服务器。假定没有运行其它服务程序，MySQL将配置成使用所有可用系统资源。
![](2021-09-11%20200928.jpg)
## Authentication Method (授权方式)
1. MySQL8提供的新的授权方式。采用SHA256基础密码加密方法
2. 传统授权方法(保留5.x版本兼容性)
![](2021-09-11%20201109.jpg)
## Accounts and Roles
- 设置Root密码
- 系统默认用户为Root,若想添加用户可单击Add User按钮添加
## Next ... 完成安装

