## Cisco设备

Cisco的交换机设备中，有三层交换机和二层交换机。
有的交换机接口可以直接设置IP地址，有的不能直接设置IP地址（和设备的接口类型有关/百兆口千兆口等）


## VLAN 配置

### 显示VLAN划分情况

show vlan

### 添加VLAN

vlan <u>id</u>    添加vlan号为id 的VLAN
name <u>name</u>  设置vlan名

### VLAN配置IP

int vlan <u>id</u>   进入vlan
ip add/address <u>ip</u> <u>mask</u> 配置IP

### 将端口加入VLAN

interface <u>接口</u>
switchport access vlan <u>id</u>
switchport mode trunk  改变端口模式

## 三层交换机开启路由[[Route]]功能

ip routing

