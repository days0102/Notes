<!--
 * @Author: Outsider
 * @Date: 2022-04-21 19:39:50
 * @LastEditors: Outsider
 * @LastEditTime: 2022-04-21 19:45:59
 * @Description: In User Settings Edit
 * @FilePath: \Notes\GCC\Gdb\Multi.md
-->

# 多进程和多线程调试

## 多进程调试

### gdb配置

|配置|参数|说明|
|:--:|:--:|:--:|
set detach-on-fork|[on(默认),off]|
set follow-fork-mode|[parent(默认),child]

