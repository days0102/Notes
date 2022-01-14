<!--
 * @Author: Outsider
 * @Date: 2022-01-14 23:19:54
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-14 23:22:47
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Linux\User.md
-->

# 用户管理

## Ubuntu
### 指定用户登录方式
- usermod -s [登录方式] [用户]
  - 登录方式一般有 /bin/sh /bin/bash ...

### 使用sudo 
- 修改/etc/sudoers文件
- 添加: [用户名] ALL=(ALL:ALL) ALL