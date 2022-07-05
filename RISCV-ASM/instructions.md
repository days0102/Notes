<!--
 * @Author: Outsider
 * @Date: 2022-07-05 20:14:28
 * @LastEditors: Outsider
 * @LastEditTime: 2022-07-05 20:46:47
 * @Description: In User Settings Edit
 * @FilePath: \Notes\RISCV-ASM\instructions.md
-->
# RISCV 汇编指令

## 算术运算指令

|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
add|add rd,rs1,rs2|rs1+rs2->rs3| add x5,x6,x7
sub|sub rd,rs1,rs2|rs1-rs2->rs3| sub x5,x6,x7
lui|lui rd,imm|(imm<<12)->rd (20位的立即数左移12位)|lui x5,0x12345
auipc|auipc rd,imm(20bit)|(imm<<12)+pc->rd(相对pc的偏移值)|auipc x5,0x1234

|伪指令|语法|等价语句|描述|例子
|:--:|:--:|:--:|:--:|:--:|
neg|neg rd,rs|sub rd,x0,rs|-rs->rd(取反)|neg x5,x6
mov|mov rd,rs|addi rd,rs,0|rs->rd|mov x5,x6
nop|nop|nop x0,x0,0|空指令|nop
li|li rd,imm(32bit)||直接加载32位立即数|li x5,0x12345678
la|la rd,addr|addr->rd||la x5,0x12345