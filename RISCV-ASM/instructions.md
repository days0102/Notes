<!--
 * @Author: Outsider
 * @Date: 2022-07-05 20:14:28
 * @LastEditors: Outsider
 * @LastEditTime: 2022-07-07 12:49:06
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



## 逻辑运算指令
|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
and|and rd,rs1,rs2|rs1&rs2->rd|and x5,x6,x7
or|or rd,rs1,rs2|rs1|rs2->rd|or x5,x6,x7
xor|xor rd,rs1,rs2|rs^rs2->rd|xor x5,x6,x7
andi|andi rd,rs,imm|rs&imm->rd|andi x5,x6,10
ori|ori rd,rs,imm|rs|imm->rs|ori x5,x6,20
xori|xori rd,rs,imm|rs^imm->rs|xori x5,x6,10

|伪指令|语法|等价语句|描述|例子
|:--:|:--:|:--:|:--:|:--:|
not|not rd,rs|xori rd,rs,-1|按位取反|not x5,x6

## 移位运算指令

### 逻辑移位 补零
|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
sll|sll rd,rs1,rs2|(rs1<<rs2)->rd|sll x5,x6,x7
srl|srl rd,rs1,rs2|(rs1>>rs2)->rd|srl x5,x6,x7
slli|sll rd,rs1,imm|(rs1<<imm)->rd|slli x5,x6,10
srli|srl rd,rs1,imm|(rs1>>imm)->rd|srli x5,x6,20

### 算术移位（只有右移，补符号位）
|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
sra|sra rd,rs1,rs2|(rs1<<rs2)->rd|sra x5,x6,x7
srai|srai rd,rs1,imm|(rs1>>imm)->rd|srl x5,x6,20


## 内存读写指令(imm为12bit有符号整数)

### 读指令
|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
lb|lb rd,imm(rs)|从内存imm+rs处读取8bit数据(符号拓展)到rd中(符号拓展)|lb x5,40(x6)
lbu|lbu rd,imm(rs)|从内存imm+rs处读取8bit无符号整数(0扩展)到rd中(0扩展)|lbu x5,40(x6)
lh|lh rd,imm(rs)|从内存imm+rs处读取16bit数据(符号拓展)到rd中(符号拓展)|lh x5,40(x6)
lhu|lhu rd,imm(rs)|从内存imm+rs处读取16bit无符号整数(0扩展)到rd中(0扩展)|lhu x5,40(x6)
lw|lw rd,imm(rs)|从内存imm+rs处读取32bit数据到rd中|lw x5,40(x6)

### 写指令
|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
sb|sb rs2,imm(rs1)|将rs2中的8bit数据写入内存imm+rs1处|sb x5,40(x6)
sh|sh rs2,imm(rs1)|将rs2中的16bit数据写入内存imm+rs1处|sb x5,40(x6)
sw|sw rs2,imm(rs1)|将rs2中的32bit数据写入内存imm+rs1处|sb x5,40(x6)


## 条件分支指令

|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
beq|beq rs1,rs2,imm|如果rs1==rs2，跳转到imm地址处|beq x5,x6,100
bne|bne rs1,rs2,imm|如果rs1!=rs2，跳转到imm地址处|bne x5,x6,100
blt|blt rs1,rs2,imm|如果rs1 < rs2(有符号方式)，跳转|blt x5,x6,100
bltu|bltu rs1,rs2,imm|如果rs1 < rs2(无符号方式)，跳转|bltu x5,x6,100
bge|blt rs1,rs2,imm|如果rs1 >= rs2(有符号方式)，跳转|bge x5,x6,100
bgeu|bltu rs1,rs2,imm|如果rs1 >= rs2(无符号方式)，跳转|bgeu x5,x6,100

> 跳转的目标地址计算方法(对齐)：(imm<<1)+pc   
> 具体编程时由标号给出


|伪指令|语法|等价语句|描述|例子
|:--:|:--:|:--:|:--:|:--:|
ble|ble rs1,rs2,offset|如果rs1<=rs2，跳转到offset地址处|ble x5,x6,100
bleu|bleu rs1,rs2,offset|如果rs1<=rs2(无符号)，跳转到offset地址处|bequ x5,x6,100
bgt|bgt rs1,rs2,offset|如果rs1>=rs2，跳转到offset地址处|bgt x5,x6,100
bgtu|bgtu rs1,rs2,offset|如果rs1>=rs2(无符号)，跳转到offset地址处|bgtu x5,x6,100
beqz|beqz rs1,offset|如果rs1==0，跳转到offset地址处|beqz x5,x6,100
bnez|bnez rs1,offset|如果rs1!=0，跳转到offset地址处|bnez x5,x6,100
bltz|bltz rs1,offset|如果rs1<0，跳转到offset地址处|bltz x5,x6,100
blez|blez rs1,offset|如果rs1<=0，跳转到offset地址处|blez x5,x6,100
bgtz|bgtz rs1,offset|如果rs1>0，跳转到offset地址处|bgtz x5,x6,100
bgez|bgez rs1,offset|如果rs1>=0，跳转到offset地址处|bgez x5,x6,100


## 无条件跳转指令

|指令|语法|描述|例子
|:--:|:--:|:--:|:--:|
jal|jal rd,label(20bit)|指令的下一条指令地址存入rd,跳转|jal x1,label
jalr|jalr rd,imm(rs)|12bit的imm符号拓展，(rs+imm)低位置0存到rd,跳转|jarl x1,0(x5)

|伪指令|语法|等价语句|描述|例子
|:--:|:--:|:--:|:--:|:--:|
j|j offset|jal x0,offset||j label
jr|jr rs|jalr x0,0(rs)|jr x5