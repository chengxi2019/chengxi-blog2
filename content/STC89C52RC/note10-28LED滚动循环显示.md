---
title: note10.16
date: 2026-10-16 23:57:12
tags:
---

LED矩阵滚动显示内容  
最大十个内容  

``` c
#include <reg52.h>
sbit SER   = P3^4;
sbit R_CLK = P3^5;
sbit SRCLK = P3^6;

unsigned char HC595_buf[10][8]={
  {0x3C, 0x7E, 0xFF, 0xC3, 0xDB, 0xE7, 0x7E, 0x3C},          // 校徽
  {0x91, 0x4A, 0x00, 0x5C, 0x54, 0x5C, 0x41, 0xFF,},         // 河
  {0x91, 0x4A, 0x00, 0x7F, 0x40, 0x5D, 0x77, 0x5D,},         // 源
  {0x7E, 0x54, 0x7F, 0x40, 0x3A, 0x2C, 0x2C, 0x3A,},         // 职
  {0x22, 0x12, 0x7E, 0x02, 0x7E, 0x12, 0x22, 0x02,},         // 业
  {0x2A, 0x7F, 0x28, 0x00, 0x2D, 0x7A, 0x2D, 0x00,},         // 技
  {0x24, 0x28, 0x30, 0xFE, 0x30, 0x28, 0xA4, 0x00,},         // 术
  {0x30, 0xA0, 0x6A, 0x2A, 0xEF, 0x2A, 0x60, 0xB0,},         // 学
  {0x7F, 0x5C, 0x66, 0x00, 0x65, 0xD6, 0x56, 0x65,},         // 院
  {0x3C, 0x7E, 0xFF, 0xC3, 0xDB, 0xE7, 0x7E, 0x3C},          // 校徽
};  //每一行动态扫描的数据	 

unsigned char COL_buf[]={0x7F,0xBF,0xDF,0xEF,0xF7,0xFB,0xFD,0xFE};

void HC595_data_sent(unsigned char dat);

void Delaylus(unsigned int t)
{
    while(t--);
}

void main()
{
    unsigned char offset;
	unsigned char pos;
	unsigned char digit;
	unsigned char coldix;  	
	unsigned char i,t;
    while(1)
    {
        for(offset = 0;offset<80;offset++)
        {
            for(t=0;t<50;t++)
            {
                for(i=0;i<8;i++)
                {
                    pos = offset+i;
                    if(pos>=80)
                    {
                        pos = pos-80;
                    }
                    digit  = pos/8;
                    coldix = pos%8;
                    
                    HC595_data_sent(HC595_buf[digit][coldix]);
                    P0=COL_buf[i];
                    Delaylus(100);
                    HC595_data_sent(0x00);
                    P0=0xFF;
                }
            }
        }
    }
}

void HC595_data_sent(unsigned char dat)
{
    unsigned char i;
    for(i=0;i<8;i++)
    {
        SRCLK = 0;
        if((dat&0x80)==0x80)
            SER = 1;
        else
            SER = 0;
        dat<<=1;
        SRCLK = 1;
    }
    R_CLK = 0;
    Delaylus(1);
    R_CLK = 1;
}
```