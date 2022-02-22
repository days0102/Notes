<!--
 * @Author: Outsider
 * @Date: 2022-02-22 15:21:20
 * @LastEditors: Outsider
 * @LastEditTime: 2022-02-22 15:51:34
 * @Description: In User Settings Edit
 * @FilePath: \Notes\GCC\Gdb\Basic.md
-->


# GDB使用

## 生成测试程序
- gcc -g [文件名] -o [可执行文件] 

## 启动Gdb调试
- gdb [可执行文件]

## Gdb命令
- l (list) : 列出调试程序的代码
- b (break) : 打断点
- n (next)  : 单步执行，遇到不进入函数
- s (step)  : 单步执行，遇到函数进入函数
- c (continue) : 继续执行
- q (quit)  : 退出