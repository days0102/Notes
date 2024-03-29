<!--
 * @Author: Outsider
 * @Date: 2022-06-02 12:12:20
 * @LastEditors: Outsider
 * @LastEditTime: 2022-06-02 12:37:21
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Cisco\devic.md
-->
# Cisco设备

## 接口

E口：Ethernet以太网接口
F口：FastEthernet高速以太网接口
G空：GigabitEthernet （千兆以太网接口）
S口：Serial高速异步串口

## 网桥

1. 网桥是一种可以连接不同网段的二层网络设备，也相当于二层交换机
2. 网桥一个端口可以连接一个网段
   - 这里的网段不是IP地址的网段，而是物理网段
   - 是位于不同地理位置的不同LAN分段
   - 是基于物理意义上的地理区域进行划分的
   - 基于IP地址的网段和子网是一个三层的概念
  
3. 网桥，二层交换机，每个端口连接可以连接一个网段，但他们所连接的主机都在同一个网络或同一个子网中。

## 二层交换机[[switch]]

1. 二层交换机可以说同时是网桥和集线器的升级换代产品
2. 同时具有集线器一样的集中连接功能，同时也具有网桥的数据交换功能。
3. 可以说交换机是带有交换功能的集线器，或者是多端口的网桥。

## 二层交换机与网桥区别

1. 交换机具有多交换端口
2. 数据转发效率更高
3. 更强的MAC地址自动学习能力

## 二层交换机和集线器的区别

1. OSI工作层次不同
   - 二层交换机：数据链路层
   - 集线器：物理层
2. 数据传输方式不同
   - 集线器：广播传输
   - 二层交换机：对目的节点发送
3. 背板信道占用方式不同
4. 数据通信方式不同
   - 集线器：半双工
   - 二层交换机：全双工