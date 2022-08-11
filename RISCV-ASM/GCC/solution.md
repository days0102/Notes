<!--
 * @Author: Outsider
 * @Date: 2022-08-12 07:09:52
 * @LastEditors: Outsider
 * @LastEditTime: 2022-08-12 07:26:26
 * @Description: In User Settings Edit
 * @FilePath: \Notes\RISCV-ASM\GCC\solution.md
-->
## [ /lib/ld-linux-riscv64-lp64d.so.1: No such file or directory ]
### backgroud
- 文件 标准C文件
- 编译 riscv64-linux-gnu-gcc file.c -o file.o
  - riscv64-linux-gnu-gcc file.c -o file.o -static [解决方案]
- 运行 qemu-riscv64 file.or
- 错误提示
  - /lib/ld-linux-riscv64-lp64d.so.1: No such file or directory

- 原因
  - 交叉编译时使用的是动态链接，运行时会寻找动态链接库
  - 所需要的动态库一般安装编译器时会附带在编译器包含的路径下
  - 运行环境在 qemu 环境中，在 qemu 虚拟机与本地带有的编译器的机器含有的文件不相同或查找的文件的路径不相同，即 qemu 虚拟机无法查找本地机器的文件，所以 qemu 无法找到动态库
- 解决
  - 在编译时使用静态链接
  - -static