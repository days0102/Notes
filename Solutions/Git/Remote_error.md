<!--
 * @Author: Linux_Outsider
 * @Date: 2021-10-26 14:55:49
 * @LastEditors: Linux_Outsider
 * @LastEditTime: 2021-10-26 15:03:42
 * @Description: In User Settings Edit
 * @FilePath: /Notes/Solutions/Git/Remote_error.md
-->
## 远程克隆下来的仓库的无法推送
```
fatal: remote error: 
  You can't push to git://github.com/days0102/Notes.git
  Use https://github.com/days0102/Notes.git
```
## 解决方法
- 本地生成SSH密钥
  - ssh-keygen -t ed25519 -C "you email"
  - 成功后会在.ssh文件夹下生成密钥
```
[lwz@Aliyun Notes]$ ssh-keygen -t ed25519 -C "411883104@qq.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/lwz/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/lwz/.ssh/id_ed25519.
Your public key has been saved in /home/lwz/.ssh/id_ed25519.pub.
The key fingerprint is:
SHA256:Hnjqm9kGO7gtNazko+I0VvuTMcKZ0rYDPo7TwSHyQTo 411883104@qq.com
The key's randomart image is:
+--[ED25519 256]--+
....
```
- 将其添加的GitHub上
## 验证密钥
- ssh -T git@github.com
```
Hi days0102! You've successfully authenticated, but GitHub does not provide shell access.
```

## 查看远程仓库地址
```
[lwz@Aliyun Notes]$ git remote -v
origin  git://github.com/days0102/Notes.git (fetch)
origin  git://github.com/days0102/Notes.git (push)
```
## 将远程仓库地址的git改为http
- git remote set-url [仓库名] [仓库地址]
```
git remote set-url origin http://github.com/days0102/Notes.git
```