## memory compression如何关闭

开始菜单右键选择“windows powershell(管理员)”输入以下命令
关闭内存压缩：Disable-MMAgent -mc
重启生效

启用：
开启内存压缩：Enable-MMAgent -mc
重启还原

查看当前状态：Get-mmagent