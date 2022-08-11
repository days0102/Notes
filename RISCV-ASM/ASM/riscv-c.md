<!--
 * @Author: Outsider
 * @Date: 2022-07-07 14:11:58
 * @LastEditors: Outsider
 * @LastEditTime: 2022-07-07 14:16:35
 * @Description: In User Settings Edit
 * @FilePath: \Notes\RISCV-ASM\riscv-c.md
-->
# C语言+汇编

```C
asm [volatile] (
    "汇编指令"
    :[输出操作数列表]
    :[输入操作数列表]
    :[可能影响的寄存器或存储器]
);
```

- 汇编指令用双引号括起来，多条指令用;或\n分开
- 多个操作数用,分开