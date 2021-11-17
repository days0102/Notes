<!--
 * @Author: Outsider
 * @Date: 2021-11-16 18:12:48
 * @LastEditors: Outsider
 * @LastEditTime: 2021-11-16 18:56:46
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Markdown\Disk.md
-->
# 磁盘管理
## 交换分区
### 查看分区容量
- free -m
```
              total        used        free      shared  buff/cache   available
Mem:           1818         172          94           1        1551        1487
Swap:             0           0           0
```
### 添加交换分区
1. dd  if=/dev/zero  of=/var/swapfile  bs=1024  count=2097152  
   dd  if=/dev/zero  of=/var/swapfile  bs=1024  count=2048k
2. 对交换文件格式化并转换为swap分区
   mkswap  /var/swapfile
3. 挂载并激活分区
   swapon /var/swapfile
> if(即输入文件,input file)
> of(即输出文件,output
file)。
> dev/zero是Linux的一种特殊字符设备(输入设备)，可以用来创建一个指定长度用于初始化的空文件，如临时交换文件，该设备无穷尽地提供0，可以提供任何你需要的数目。
bs=1024 ：单位数据块（block）同时读入/输出的块字节大小为1024 个字节即1KB，bs(即block
size)。
> count=2048000 ：数据块（block）数量为2048000
，即2048000个1KB。可以计算swap分区的容量为：1KB 2097152=1KB
1024(k)10242=2097152=2G。（dd命令里的单位M表示1024*1024,k表示1024）。

### 删除交换分区
1. 停用交换分区
   swapoff /dev/mapper/centos-swap
2. 删除swap分区文件
   rm /dev/mapper/centos-swap