---
title: note11-2
time: 2026-11-02 21:36:52
tar:
---

# S5700交换机配置vlan

>关掉烦人的cfgchange信息方法：  用户视图下：  <LSW1>u t m

## 创建Vlan

在系统视图中：  

``` bash
[LSW1]vlan 10   /*进入vlan口*/
[LSW1]description caiw10 命名vlan口
[LSW1]quit  /*退出*/
``` 

批量创建Vlan口:  
`[LSW1]vlan batch 10 20 30`

---------------------------


### 端口分配到vlan

需先进入端口：
`[LSW1]interface GigabitEthernet 0/0/2`  
随后输入：  
``` bash
[LSW1]port link-type access
[LSW1]port default vlan 10
[LSW1]quit  /*退出*/
``` 


### 端口批量分配到vlan

选中并进入端口:
``` bash
[LSW1]port-group group-member g 0/0/2 to g 0/0/8    /*选中多个端口*/
[LSW1]port link-type access
[LSW1]port default vlan 10
[LSW1]quit  /*退出*/

```


### 配置端口为trunk交换机互传端口
>一般将0/0/1口作为此用途  
```
[LSW1]int g0/0/1
[LSW1]port link-type trunk
[LSW1]port trunk allow-pass vlan 10 20 30
[LSW1]quit  /*退出*/
```

-------------------------------


### 验证是否生效：

系统界面下输入：  
`[LSW1]display vlan`  

在显示信息中找到并查看：  
(VID为vlan，port为端口)，要求与输入的代码所应形成的效果一致  
``` bash
VID  Type    Ports

......

10   common  UT:GE0/0/2(U)      GE0/0/3(U)                                      

20   common  UT:GE0/0/9(D)      GE0/0/10(D)                                     

30   common  UT:GE0/0/19(D)     GE0/0/20(D)

......
```
---------------------------------


## 删除vlan

[LSW1] undo vlan 10

>规范：先将删除的vlan的端口加入其他vlan后再删除

## 附加内容

display命令无论在用户界面还是系统界面都生效  
在使用save保存配置时要注意返回信息，有时可能要求填写保存配置文件的压缩包的名称（记得写.cfg或.zip的后缀）  