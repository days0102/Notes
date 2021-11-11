<!--
 * @Author: Outsider
 * @Date: 2021-08-26 12:12:53
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-11 18:02:59
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Linux\SSH.md
-->
# 远程登录
## 安装ssh
- apt install openssh-server
## 查看是否安装
- aptitude show openssh-server

## 远程登录
- ssh username@ip
- 如：ssh wz@192.168.1.1


## 端口映射到本地
- ssh -L [remote_port]:localhost:[local_port] username@ip

## 公钥登录（免密）
1. 本地生成公钥
   - ssh-keygen
2. 复制本地公钥到远程主机
   - ssh-copy-id username@ip

### Error
> ssh-copy-id : 无法识别“ssh-copy-id”项
> 执行前先在powershell中定义以下函数
```
function ssh-copy-id([string]$userAtMachine, $args){   
    $publicKey = "$ENV:USERPROFILE" + "/.ssh/id_rsa.pub"
    if (!(Test-Path "$publicKey")){
        Write-Error "ERROR: failed to open ID file '$publicKey': No such file"            
    }
    else {
        & cat "$publicKey" | ssh $args $userAtMachine "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1"      
    }
}
```