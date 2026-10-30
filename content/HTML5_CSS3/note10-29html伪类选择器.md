---
title: note10-29html伪类选择器
time: 2026-10-30 21:41:06
tag: 
    
---

## 伪类选择器

又一种选择器的类型  


| 类型  | 符号 |
| :---  | ---: |
|:first-child	   |   是父元素的第一个子元素      |
|:last-child	   |  是父元素的最后一个子元素     |
|:nth-child(n)	   | 是父元素的第 n 个子元素       |
|:nth-last-child(n)|	从后往前数第 n 个          |
|:only-child	   |  是父元素唯一的子元素（独生子）|

## 示例：

``` html

/*存在两个类名是因为同时使用了包含选择器，无需理会*/

.balloon img:nth-last-child(-n+4){width:100px;} /*()中还可使用特别的参数，如此处使用的是末尾4个元素的形式*/
.balloon img:nth-child(6){width:120px;}

.balloon img:first-child{position: relative;top: 50px;}
/**/
.balloon img:nth-child(2){position: relative;top: -20px;}
.balloon img:nth-child(3){position: relative;top: -35px;}
.balloon img:nth-child(4){position: relative;top: 40px;}
.balloon img:nth-child(5){position: relative;top: 54px;}
.balloon img:nth-child(6){position: relative;left: -560px;top: -220px;}
.balloon img:nth-child(7){position: relative;left: 45px;top: -260px;}
.balloon img:nth-child(8){position: relative;left: 140px;top: -300px;}
.balloon img:nth-child(9){position: relative;left: 450px;top: -300px;}
.balloon img:nth-child(10){position: relative;left: 550px;top: -260px;}

```