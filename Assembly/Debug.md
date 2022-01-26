<!--
 * @Author: Outsider
 * @Date: 2022-01-23 17:29:10
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-23 18:26:19
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Assembly\Debug.md
-->

# Dos下Debug的使用

|命令|作用|
|:--:|:--:|
|R|查看、改变寄存器内容|
|D|查看内存中的内容|
|E|改写内存中的内容|
|U|将内存中的机器指令翻译成汇编指令|
|T|执行一条机器指令|
|A|以汇编指令格式在内存中写入机器指令|

## R命令
- r : 查看寄存器内容
- r [寄存器] : 修改寄存器的内容

## D命令
- d [段地址:偏移地址] : 查看段地址:偏移地址位置内存内容
  
## E命令
- d [段地址:偏移地址] : 改写多个内存单元
- d [段地址:偏移地址] [改写内容] : 改写一个内存单元
