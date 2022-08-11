# riscv 交叉编译

## 编译工具
1. riscv64-linux-gnu-[gcc/ld...]
2. riscv64-unknown-elf-[gcc/ld..]

## 编译参数[可选]
- -march=rv32[ima] -mabi=ilp32
- -march=rv64[ima] -mabi=ip64

## qemu 运行
- qemu-riscv32 [file]
- qemu-riscv64 [file]