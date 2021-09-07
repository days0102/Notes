# Linux网络配置(Ubuntu)
## 查看ip
- ifconfig  //查看网卡设备信息
- nmcli device show //查看网卡设备信息
- nmcli connectin show //查看连接状态

---

## 测试联通性
>- ping ip
>>- 如：ping 192.168.1.1  
>- ping ip -c n  联通n次
>> - 如：ping -c 4 192.168.1.1

---

## 查看域名ip
- nslookup 域名
- 如：nslookup www.baidu.com