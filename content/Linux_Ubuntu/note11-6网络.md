---
title: note11-6网络
created: 2026-11-06 17:02:52
tag: 
    - ip a
    - route
    - ip link
    - nslookup
    - ping
---

- 查看网络信息  
输入`ip a`，返回信息包括但不限于：网卡，IP地址，子网掩码，本地回环127.0.0.1  

>补充信息：ubuntu中的有线网卡名称一般为：ens33

- 临时修改ip  
仅临时有效，重启后或重启网络后失效  
此ip并不唯一，允许多个ip同时存在  
格式：`ip a add/del IP地址/子网掩码简写形式 dev 网卡名`  
``` bash
ip a add 192.168.75.129/24 dev ens33   /*增加*/
ip a del 192.168.75.129/24 dev ens33   /*删除*/
```  
- 查看网关  
输入`ip route`，查看网关  

- 关闭与开启网卡  
关闭网卡后右上角网络图标应消失，网络设置也应不可用  
``` bash
sudo ip link set ens33 down /*关*/
sudo ip link set ens33 up   /*开*/
```

- 查看域名的ip
格式：`nslookup 域名或网址`
>以下随便看看即可~
``` bash
nslookup www.baidu.com              /*查域名的IP地址*/
nslookup 8.8.8.8                    /*查看IP绑定的域名*/
nslookup www.baidu.con 8.8.8.8      /*用DNS服务器查网站的IP地址*/
```

- 测试网络连通性ping 
>基本无需介绍  
`ping IP地址`
可选项：
``` bash
ping -s 8.8.8.8 
-c 发包个数 
-s 发包的字节数 
-t 设置ttl 
-i 发包间隔
```