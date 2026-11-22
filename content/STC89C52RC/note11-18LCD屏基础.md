---
title: note11-18LCD屏基础
created: 2026-11-18t0:57:03
---

在使用lcd_showchar()函数时：  
先行后列，行从1开始，列从0开始  

``` c
#include <reg52.h>
#include "lcd1602.h"
void main()
{
    LCD_csh();
    while(1)
    {
        //先行后列
        lcd_showchar(1,0,'A');
        lcd_showchar(2,0,'B');
        lcd_showchar(3,0,'C');

        lcd_showchar(1,1,'1');
        lcd_showchar(2,1,'2');
        lcd_showchar(3,1,'3');
    }
}