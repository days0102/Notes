<!--
 * @Author: Outsider
 * @Date: 2022-07-07 13:53:48
 * @LastEditors: Outsider
 * @LastEditTime: 2022-07-07 13:58:54
 * @Description: In User Settings Edit
 * @FilePath: \Notes\RISCV-ASM\function.md
-->
# 函数调用

|伪指令|语法|等价语句|描述|例子
|:--:|:--:|:--:|:--:|:--:|
jal|jal offset|jal x1,offset|x1保存返回地址|jal label
jalr|jalr rs|jalr x1,0(rs)||jalr label
call|call offset|auipc x1,offset[31:12]+offset[11];jalr x1,ofsset[11:0] (x1)||call fun
ret|ret|jalr x0,0(x1)|返回|ret