# Linux网络问题(Ubuntu)
## ens33网卡无法找到（原来有，现在无法找到）
>问题描述
- ifconfig 没有显示ens33
- ifconfig 显示ens33
- nmcli device show 显示ens33
- 设置-网络没有显示有线连接
>解决方法
1. service network-manager stop # 先停止服务
2. rm -rf /var/lib/NetworkManager/NetworkManager.state # 删除文件
3. service network-manager start #重启服务器

---