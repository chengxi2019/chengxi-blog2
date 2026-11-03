---
title: note9-20流水灯
time: 2026-11-03 15:38:39
tag: 
---

有待补充：  

``` c
#include <reg51.h> 
#include <intrins.h>
void delay(unsigned int t);
unsigned char i;

void light4()
{
	for(i = 0;i<4;i++)
	{
		P2 = 0xff;
		delay(500);
		P2 = 0x00;
		delay(500);
	}
}

void san4()
{
		for(i = 0;i<4;i++)
	{
		P2 = 0xaa;
		delay(500);
		P2 = 0x55;
		delay(500);
	}	
}

void moveleft()
{
	P2= 0xfe;
	for(i=0;i<8;i++)
	{
		delay(500);
		P2 = _crol_(P2,1);
	}
}


void rightmove()
{
	P2= 0x7f;
	for(i=0;i<8;i++)
	{
		delay(500);
		P2 = _cror_(P2,1);
	}
}


void zhuliang()
{
	P2 = 0xfe;
	for(i=0;i<8;i++)
	{ 
		delay(500);
		P2= P2<<1;
	}
}
 
void zhumie()
{
	P2 = 0x01;			 //0001 111
	for(i=0;i<8;i++)
	{ 
		delay(500);
		P2= P2<<1 | 0x01;
	}
}
void main()
{
//	unsigned char LED[] ={  0xfe,0xfd,0xfb,0xf7,0xef,0xdf,0xbf,0x7f, //从左到右移动
//							0x7f,0xbf,0xdf,0xef,0xf7,0xfb,0xfd,0xfe, //从右到左移动
//							0xaa,0x55,0xaa,0x55,0xaa,0x55,0xaa,0x55, //间隔闪烁4次	  1
//							0x00,0xff,0x00,0xff,0x00,0xff,0x00,0xff, //全亮全灭4次	   1
//							0xfe,0xfc,0xf8,0xf0,0xe0,0xc0,0x80,0x00, //逐个点亮到全亮
//							0x80,0xc0,0xe0,0xf0,0xf8,0xfc,0xfe,0xff};

	while(1)
	{
		 light4();
		 san4();
		 moveleft();
		 moveright();
		 zhuliang();
		 zhumie();
	}

}




void delay(unsigned int t)
{
	unsigned int i,j;
	for(i = t;i>0;i--)
		for(j = 100;j>0;j--);	//此处有;表for为空

}

```