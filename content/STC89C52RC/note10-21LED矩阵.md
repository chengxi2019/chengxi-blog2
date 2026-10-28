---
title: note10-21LED矩阵
date: 2026-10-28 22:35:17
tags: 
---

LED矩阵显示静态内容：

``` c

/*LED矩阵*/
#include <reg51.h>
sbit SER =P3^4;
sbit R_CLK = P3^5;
sbit SRCLK = P3^6;

unsigned char HC595_buf[] = {0x01,0x02,0x04,0x08,0x10,0x20,0x40,0x80};
void HC595_data_sent (unsigned char dat);

void Delaylus(unsigned int t)
{
	while(t--);
}

void main()
{
	unsigned char i;
    while(1)
	{
		 for(i=0;i<8;i++)
		 {
		 	HC595_data_sent(0x00);

			HC595_data_sent(HC595_buf[i]);
			P0=0x00;
			Delaylus(20000);
		 }
	}
}
void HC595_data_sent(unsigned char dat)
{
	unsigned char i;
	for(i=0;i<8;i++)
	{
		SER=dat>>7;
		dat<<=1;
		SRCLK=0;
		Delaylus(1);
		SRCLK=1;
	}
	R_CLK=0;
	Delaylus(1);
	R_CLK=1;
}

```











