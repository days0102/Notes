# PowerShell使用SSH时出现的问题
## ssh远程登录时不成功
```
C:\Users\LWZ>ssh root@120.78.176.147
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:gvK6lZgQovTYTYLnkjh0Wx6/+4t4xWAp0mAwoxBbiaw.
Please contact your system administrator.
Add correct host key in C:\\Users\\LWZ/.ssh/known_hosts to get rid of this message.
Offending ED25519 key in C:\\Users\\LWZ/.ssh/known_hosts:6
ECDSA host key for 120.78.176.147 has changed and you have requested strict checking.
Host key verification failed.
```
**产生原因**
- 服务器地址重置了或服务器重新安装了
- 即主机的密钥更改了，远程主机发送的密钥与本机的密钥不一致
**解决方法**
- ssh-keygen -R [服务器地址]
```
C:\Users\LWZ>ssh-keygen -R 120.78.176.147
# Host 120.78.176.147 found: line 5
# Host 120.78.176.147 found: line 6
C:\Users\LWZ/.ssh/known_hosts updated.
Original contents retained as C:\Users\LWZ/.ssh/known_hosts.old
```