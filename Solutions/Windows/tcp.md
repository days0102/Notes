<!--
 * @Author: Outsider
 * @Date: 2022-10-20 11:19:09
 * @LastEditors: Outsider
 * @LastEditTime: 2022-10-20 12:39:38
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Solutions\Windows\tcp.md
-->
## dial tcp 127.0.0.1:9999: bind: An operation on a socket could not be performed because the system lacked sufficient buffer space or because a queue was full.

```
为遵守 Internet 号码分配机构 (IANA) 的建议，Microsoft 增加了 Windows Vista 和 Windows Server 2008 中传出连接的动态客户端端口范围。新的默认起始端口为 49152，新的默认结束端口为 65535。这是对使用默认端口范围 1025 到 5000 的早期版本的 Windows 的配置进行了更改。
```

### 您可以使用以下netsh命令查看运行 Windows Vista 或 Windows Server 2008 的计算机上的动态端口范围：

- netsh int ipv4 show dynamicport tcp
```
协议 tcp 动态端口范围
----------------------
启动端口        : 49152
端口数          : 16384
```
- netsh int ipv4 show dynamicport udp
- netsh int ipv6 show dynamicport tcp
- netsh int ipv6 show dynamicport udp


>  笔记
为每个传输（TCP 或 UDP）单独设置范围。端口范围现在真正是一个具有起点和终点的范围。如果在内部网络上使用防火墙，部署运行 Windows Server 2008 的服务器的 Microsoft 客户可能会遇到影响服务器之间 RPC 通信的问题。在这些情况下，我们建议您重新配置防火墙以允许服务器之间的流量在 49152 到 65535 的动态端口范围内。此范围是服务和应用程序使用的众所周知的端口的补充。或者，可以在每台服务器上修改服务器使用的端口范围。您可以使用 netsh 命令调整此范围，如下所示netsh int <ipv4|ipv6> set dynamic <tcp|udp> start= number num= range：
此命令设置 TCP 的动态端口范围。起始端口号，端口总数为range。

### 以下是示例命令：

- netsh int ipv4 set dynamicport tcp start=10000 num=1000
- netsh int ipv4 set dynamicport udp start=10000 num=1000
- netsh int ipv6 set dynamicport tcp start=10000 num=1000
- netsh int ipv6 set dynamicport udp start=10000 num=1000
  
这些示例命令将动态端口范围设置为从端口 10000 开始，到端口 10999（1000 个端口）结束。可设置的最小端口范围为 255。可设置的最小起始端口为 1025。最大结束端口（基于配置的范围）不能超过 65535。要复制 Windows Server 2003 的默认行为，请使用1025 作为起始端口，然后使用 3976 作为 TCP 和 UDP 的范围。这导致起始端口为 1025，结束端口为 5000。



###
```
··· netsh int ipv4 set dynamicport tcp start=49152 num=16384
··· netsh int ipv4 set dynamicport tcp start=29152 num=36384
```