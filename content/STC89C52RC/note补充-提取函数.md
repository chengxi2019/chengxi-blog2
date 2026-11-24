---
title: note补充-提取函数
created: 2026-11-17 23:15:45
---

## 提取函数
将原本写在 main 函数里的一大段逻辑提取出来、封装成独立函数，再由`main`调用  

由此会产生两个文件：原文件`.c`与头文件`.h`  
该类型文件两两对应对出现,需同时被加入进工程中(也可仅加入原文件)  

有待补充  


### 头文件(.h)
仅用于声明：即仅指出函数的存在，而不具体说明内容  
基本格式：  
``` c
#ifndef __DELAY_H__(大写文件名 .h改为_H)
#define __DELAY_H__(大写文件名 .h改为_H)

当有定义寄存器时需定义加上：
#include <reg52.h>

函数声明语句
例如：void delay(unsigned int t);

#endif
```

### 原文件(.c)
仅用于说明函数具体内容
基本格式：  
``` c
#include "头文件名"(要带有.h)

函数定义语句：
例如：void delay(unsigned int t)
{
    unsigned int i,j;
    for(i=t;i>0;i--)
        for(j=100;j>0;j--){}
}
```



