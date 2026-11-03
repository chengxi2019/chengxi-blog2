---
title: note11-3按键
time: 2026-11-03 22:19:48
tar: 
---

### 如何判断按键是否是按下的状态：  
按下时：IO口为高电平  
未按下：IO口为低电平  

### 如何用程序判断按键是否按下：  
因为按下按键后金属触点移动速度比程序慢，可能会出现判断不一致的问题，  
所以在利用程序处理按键按下时，需要稍微**延时**几微秒以消除抖动，随后再次判断  

### 单个按键示例： 

``` c
#include <reg51.h>

sbit key1 = P3^1;

void delay(unsigned int t);

void main()
{
	while(1)
	{
	   if(key1==0)
	   {delay(10);	/*延时10ms，以判断是否真正按下*/
		if(key1==0)
		{
			P2 = 0xff;
		}			
	   }else 
	   P2 = 0x00;   	   
	}
}

void delay(unsigned int t)
{
	unsigned int i,j;
	for(i=t;i>0;i--)
		for(j=100;j>0;j--);
}
```

### 多按键示例

``` c
/********1.MCU上电，8个LED全亮;
  2.S1按下， 8个LED全灭
  3.S2按下， 8个间隔点亮
  4.S3按下， 高4位点亮
  5.S4按下， 低4位点亮
*******************************************/
#include <reg51.h>
sbit key1 = P3^1;
sbit key0 = P3^0;
sbit key2 = P3^2;
sbit key3 = P3^3;

void delay(unsigned int t)
{
    unsigned int i,j;
    for(i=t;i>0;i--)
    for(j=100;j>0;j--);
}

void main()
{
    unsigned char i,w;
    P2 = 0x00;      //上电8个LED全亮（低电平点亮）
    while(1)
    {
        //第1个按键key1(S1)：8个LED全灭
        if(key1==0)
        {
            delay(10);
            if(key1==0)
            {
                P2 = 0xFF;   //全部输出高电平，LED全灭
            } while(!key1);
        }
        //第2个按键key0(S2)：8个LED间隔点亮 01010101
        if(key0==0)
        {
            delay(10);
            if(key0==0)
            {
                P2 = 0x55;  //01010101，间隔低电平，隔一个亮一个
            } while(!key0);
        }
        //第3个按键key2(S3)：高4位点亮
        if(key2==0)
        {
            delay(10);
            if(key2==0)
            {
                P2 = 0x0F;  //00001111，高4位输出低电平点亮，低4位高电平熄灭
            } while(!key2);
        }
        //第4个按键key3(S4)：低4位点亮
        if(key3==0)
        {
            delay(10);
            if(key3==0)
            {
                P2 = 0xF0;  //11110000，低4位输出低电平点亮，高4位高电平熄灭
            } while(!key3);
        }
        else P2=0x00;
    }
}

```

### 底层函数扫描版  
以为不应该在main主函数中过多的书写此类底层代码，所以将其**封装**为一个函数  

``` c
/******1.MCU上电，8个LED全亮；
	   2.S1按下， 8个LED全灭
	   3.S2按下， 8个间隔点亮
	   4.S3按下， 高4位点亮
	   5.S4按下， 低4位点亮
************************************/
#include <reg51.h>
//按键位定义
sbit key1 = P3^1;   //1号按键，编码	   上电P3.1=1
sbit key0 = P3^0;	//2号按键
sbit key2 = P3^2;	//3号按键
sbit key3 = P3^3;	//4号按键

unsigned char key_scan();

void delay(unsigned int t)
{
	unsigned int i,j;
	for(i=t;i>0;i--)
	for(j=100;j>0;j--);
}
void main()
{
	while(1)
	{
	 	//	应用层函数
		switch(key_scan())
		{
			case 0:	P2=0x00;break;
			case 1: P2=0xff;break;
			case 2:	P2=0xaa;break;
			case 3:	P2=0x0f;break;
			case 4:	P2=0xf0;break;
			default:break;
		}
				  	 
	}
}


/*******按键扫描底层逻辑函数*******/
unsigned char key_scan()
{
  unsigned char key_num=0;	// ！kye 1= ！1 取反 ==0	  !0=1
  if(!key1)	    //if(key1==0)
  {
  	delay(10);
	if(!key1)
	{
		key_num	= 1;
	}
  }while(!key1);
  if(!key0)	    //if(key1==0)
  {
  	delay(10);
	if(!key0)
	{
		key_num	= 2;
	}
  }while(!key0);
  if(!key2)	    //if(key1==0)
  {
  	delay(10);
	if(!key2)
	{
		key_num	= 3;
	}
  }while(!key2);
  if(!key3)	    //if(key1==0)
  {
  	delay(10);
	if(!key3)
	{
		key_num	= 4;
	}
  }while(!key3);
 return key_num;
}
```