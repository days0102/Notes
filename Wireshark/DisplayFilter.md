<!--
 * @Author: Outsider
 * @Date: 2022-05-18 21:08:52
 * @LastEditors: Outsider
 * @LastEditTime: 2022-05-19 13:00:36
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Wireshark\DisplayFilter.md
-->
# 显示过滤器

    [not] Expression [and|or] [not] Expression

- Expression 任意原词形式的过滤器表达式
  - ip.src==192.168.1.1
  - tcp.falgs.syn==1
  - tcp.analysis.retransmission



## Ethernet 过滤器
    eth.addr==<MacAddr>
    eth.dst==<MacAddr>
    eth.type==<Protocol Type(0xnnnn)>


## ARP 过滤器
    arp.opcode==<Value>
        arp.opcode=1 ARP请求帧
        arp.opcode=2 ARP应答帧

    arp.src.hw_mac==<MacAddr>


## IP过滤器
    ip.addr==<IPAddr>
    ip.dst==<IPAddr>
    ip.ttl==<Value>
    ip.len==<Value>
    ip.version==<4/6>

## TCP和UDP过滤器
    1.端口过滤器  
    tcp.port==<value>
    udp.port==<value>
    tcp.dstport==<value>
    udp.srcport==<value>


    2.头部过滤器
    tcp.analysis.retransmission  显示重传的数据包
    tcp.analysis.duplicate_ack   显示确认多次的TCP数据包
