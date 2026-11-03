---
title: note9-11PWM显示
time: 2026-11-03 15:33:04
tag: 
---

# PWM

PWM显示，可以理解为，本来只能实现开和关两种状态,但现在通过在一个单位时间内以人的肉眼几乎无法察觉的速度快速的重复开与关，并通过调整开与关所占的时间，使得人眼能够察觉到开与关之间的状态或是过程，以实现类似“半开半关”的效果  


``` c
#include <reg51.h>

void delay(unsigned int t);
void main()
{
	unsigned char light_con;
	unsigned int i;
	while(1)
	{
		 for(light_con=0;light_con<=25;light_con++)
		 {
		 	for(i=0;i<30;i++)
			{
				P2 = 0x00;
				delay(light_con);
				P2 = 0xff;
				delay(100-light_con);
			}
		 }
		 for(light_con=25;light_con>0;light_con--)
		 {
		 	for(i=0;i<30;i++)
			{
				P2 = 0x00;
				delay(light_con);
				P2 = 0xff;
				delay(100-light_con);
			}
		 }				
	}
}

void delay(unsigned int t)
{
	int i = t;
	for(;i>0;i--)
	{
	
	}
}
```