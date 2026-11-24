---
title: note11-24
created: 2026-11-24T17:12:23
---


固定字符  
``` c
#include "lcd1602.h"
#include  <reg52.h>
unsigned char code str1[] = "WLECOME TO CHINA";
unsigned char code str2[] = " SHENZHEN APEC";

void main()
{
    lcd_csh();
    while(1)
    {
        lcd_showString(0,0,str1);
        lcd_showString(1,1,str2);
    }
}
```

可在main函数中自定义的：

有待补充  