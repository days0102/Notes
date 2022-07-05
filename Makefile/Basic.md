<!--
 * @Author: Outsider
 * @Date: 2022-06-29 21:02:54
 * @LastEditors: Outsider
 * @LastEditTime: 2022-06-29 21:07:35
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Makefile\Basic.md
-->
# Makefile

## 隐式规则命令变量
|变量名|含义|
|:--:|:--:|
|RM|rm -f|
|CC|cc|
CPP|cc -E
CXX|g++
CFALGS|C语言编译器的参数
CPPFLAGS|CPP预处理参数

## 模式规则

% : 任意非空字符串
