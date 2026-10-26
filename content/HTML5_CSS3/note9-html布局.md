---
title: note9-html布局
date: 2026-10-25 21:28:43
tags:
---

margin,float,padding,overflow
# 布局综合

## 布局属性:

### margin外边距
控制元素外侧距离其他元素的距离  
透明,允许与其他元素重叠  

2个参数时分别控制:上下,左右  
4个参数时分别控制:上,下,左,右(顺时针)  
可设置为auto

``` html
margin: 10px 20px 0px 0px;
margin: 10px 10px;
margin: auto
```


### padding内边距
控制元素内容与边框的距离  
会被背景色影响  
会使得盒子撑大  
>与margin相同
2个参数时分别控制:上下,左右  
4个参数时分别控制:上,下,左,右(顺时针)  

``` html
padding: 10px;                  
padding: 10px 20px;             
padding: 10px 20px 30px 40px;
padding: auto;  
```

### float元素浮动
使元素向左或右浮动,直到碰到其他元素  

文字会环绕在四周  

``` html
float: left;    /* 左浮动 */
float: right;   /* 右浮动 */
float: none;    /* 不浮动（默认） */
```

### overflow内容溢出处理
当内容超出盒子时的处理办法  

``` html
overflow: visible;   /* 默认，溢出可见 */
overflow: hidden;    /* 溢出部分隐藏 */
overflow: scroll;    /* 总是显示滚动条 */
overflow: auto;      /* 需要时才显示滚动条 */
overflow: clip;      /* 直接裁剪，不产生滚动容器 */
```

附注:有关于考试询问元素,盒子大小的解决办法:  
注意!!!不要忘记算入上下左右*两边*的距离!
当问"盒子大小时": width+左padding+右padding+左border+右border
当问"元素大小时": 盒子大小+左margin+右margin