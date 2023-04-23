### 为端口配置IP

interface <u>接口</u> 进入接口配置
ip address <u>ip</u> <u>mask</u>

### 静态路由

ip route <u>网络号</u> <u>子网掩码</u> <u>下一跳</u>
网络号：接收数据包的源地址网络号
下一跳：下一跳路由接口IP

### RIP

network <u>网络号</u>
网络号：路由器接口的网络号

### PPP配置CHAP验证

1. 修改设备名（可选 hostname <u>name</u>）
2. 设置连接的路由的用户名和密码（username <u>对方设备名</u> password <u>密码</u>）
3. 进入Serial串口（interface <u>接口</u>）
4. 开启PPP（encapsulation ppp）
5. 使用CHAP验证（ppp authentication chap）

---
R1与R2的Serial之间
R1:
r1(config)#hostname r1
r1(config)#username r2 password route
r1(config)#interface Serial 0
r1(config-if)#encapsulation ppp
r1(config-if)#ppp authentication chap

R2:
r2(config)#hostname r2
r2(config-if)#username r1 password route
r2(config)#interface Serial 0
r2(config-if)#encapsulation ppp
r2(config-if)#ppp authentication chap

**两端密码要保持一致**


### 配置静态NAT

1. 声明路由器的**所有**端口是内部还是外部（进入接口，ip nat inside/outside）
2. 配置静态NAT（ip nat inside source static <u>内部IP</u> <u>外部IP</u>）

### 控制访问列表

1. 控制访问语句（access-list <u>id</u>  deny/permit <u>协议</u> host <u>源IP</u> <u>目的IP</u> <u>端口</u>）
2. 进入接口启用控制访问（ip access-group <u>id</u> in/out）

r2(config)#access-list 100 deny icmp host 192.168.1.2 host 192.168.1.3 echo
r2(config)#interface Serial 0
r2(config-if)#ip access-group 100 in

### OSPF

