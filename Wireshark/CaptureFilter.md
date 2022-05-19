<!--
 * @Author: Outsider
 * @Date: 2022-04-10 15:17:34
 * @LastEditors: Outsider
 * @LastEditTime: 2022-05-18 21:07:17
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Wireshark\CaptureFilter.md
-->

# 捕捉过滤器

## 过滤表达式

### 限定符

- type(类型)
  1. host : 主机名或主机地址标识符
  2. net : 网络号标识符
  3. port : TCP/UDP端口号标识符
- dir(方向)
  1. src : 源
  2. dst : 目的
- proto(协议类型)
  1. ether : 以太网帧
  2. ip : IP数据包
  3. arp : ARP帧

    tcp dst port 135   
    dst为dir限定符  
    port为type限定符  
    tcp为proto限定符  

### 以太网过滤器

- ether host [Ethernet host]
  - 捕捉源于或发往Ethernet host 的以太网帧
- ether src [Ethernet host]
  - 捕捉源于Ethernet host 的以太网帧
- ether broadcast 
  - 捕捉以太网广播流量
- ether multicast
  - 捕捉以太网多播流量
- ether proto [protocol]
  - 捕捉protocol以太网协议类型编号的以太网流量
- vlan [vlan_id]
  - 捕捉vlan_id指定的VLAN流量

### 配置主机和网络过滤器

- ip 
  - 只抓ipv4流量
- ipv6
  - 只抓ipv6流量
- host [host]
  - 只抓指定host的IP流量
  - host可为主机名或IP地址
- dst host [host]
  - 只抓发往host的IP流量
  - host可为主机名或IP地址
- gateway [host]
  - 只抓穿host而过的流量
  - host必须为主机名
- net [net]
  - 抓取net标识的ipv4/ipv6网络号的流量
- dst net [net]
  - 抓取发往net标识的ipv4/ipv6网络号的流量
- net [net] mask [netmask]
  - 抓取net和mask标识的ipv4网络号的流量
- net [net]/[len]
  - 抓取net和mask标识的ipv4网络号的流量
- broadcast
  - 抓取IP广播包
- multicast
  - 只抓IP多播包
- ip proto [protocol_code]
  - 只抓IP包头协议字段为protocol_code的包
  - TCP数据包protocol_code=6
  - UDP数据包protocol_code=17
  - ICMP数据包protocol_code=1
- ip6 proto [protocol]
  - 只抓ipv6包头下一包头字段为protocol的ipv6包
- icmp[icmptype]==[identifier]
  - icmp[icmptype]==0  ;ICMP echo reply数据包
  - 只抓取特定类型的ICMP数据包
  - identifier为ICMP头部的类型字段值
- ip[2:2]==[number]
  - ip[2:2]表示第2字节后两字节，即第3第4字节（IP包头第3第4字节为IP包总长度）
  - 抓取特定长度的IP数据包
- ip[8]==[number]
  - 抓取特定TTL的数据包
- ip[12:4]==ip[16:4]
  - 抓取源和目的相同的包
- ip[9]==[number]
  - 抓取指定协议类型的数据包

### 配置TCP/UDP及端口过滤

- port [port]
  - 抓取port指明的端口号数据
- src post [port]
  - 抓取源于port指明端口号的数据
- tcp portange [p1]-[p2]
  - 抓取p1到p2端口范围的tcp或udp数据包
- tcp dst portange [p1]-[p2]
  - 抓取发往p1到p2端口范围的tcp或udp数据包
- tcp-urg
  - 抓取紧急指针标记位置1的TCP数据包
- tcp-rst
  - 抓取RESET标记位置1的TCP数据包
- tcp-ack
  - 抓取ACK标记位置1的TCP数据包
- tcp-syn
  - 抓取SYN标记位置1的TCP数据包
- tcp-psh
  - 抓取PUSH标记位置1的TCP数据包
- tcp-fin
  - 抓取FIN标记位置1的TCP数据包

## 复合型过滤器

### 操作符

- ！ 或 not
- && 或 and
- || 或 or

    tcp port 23 and host 192.168.1.1