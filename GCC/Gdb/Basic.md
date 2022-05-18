<!--
 * @Author: Outsider
 * @Date: 2022-02-22 15:21:20
 * @LastEditors: Outsider
 * @LastEditTime: 2022-05-11 21:06:40
 * @Description: In User Settings Edit
 * @FilePath: \Notes\GCC\Gdb\Basic.md
-->


# GDB使用

## 生成测试程序
- gcc -g [文件名] -o [可执行文件] 

## 启动Gdb调试
- gdb [可执行文件]

## Gdb命令

|命令|含义|
|:--:|:--:|
| (list)|列出调试程序的代码
|b (break) |打断点
| n (next) |单步执行，遇到不进入函数
| s (step) | 单步执行，遇到函数进入函数
| c (continue)| 继续执行
| q (quit) | 退出
| r (run) | 运行程序
| info break|查看断点信息
| p [变量] | 查看变量值
| finish  |退出函数
|bt|查看堆栈
q|退出gdb
help|查看帮助
info reg| 查看寄存器状态


## 其他命令
|命令|含义|
|:--:|:--:|
|shell|进入shell,使用exit退回gdb|
|shell [shell_command]|直接运行shell命令