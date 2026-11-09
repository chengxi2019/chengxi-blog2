---
title: note11-5htmltransition动画属性
created: 2026-11-05 23:25:36
tag: 
    - transition
    - duration
    - delay
    
---

## transition属性

动画属性，设置了此属性的元素在发生变化（如hover属性）时会有变换的动画效果  

- transition-property属性

设置是否拥有动画效果，即“开关”  
该属性不能单独设置，必须与duration配合使用  
``` html
transition-property: all;     /*所有属性均拥有*/
transition-property: width;   /*仅特定属性拥有*/
transition-property: none;   /*关闭*/
```

- transition-duration:属性  

设置动画效果长度，单位为时间（秒或毫秒）  
此属性**默认（或者未填写）为0**，即没有动画！！！  
故该属性不能不设置，且必须与property配合使用  
``` html
transition-duration: 1s;
```


- transition-timing-function: 

设置动画速度，单位为时间（秒或毫秒）
>现在已经使用ease值来代替具体时间，相关请查看示例    
``` html
transition-timing-function: ease;         /*慢快慢*/
transition-timing-function: ease-in;      /*慢-快(渐入)*/
transition-timing-function: ease-out;     /*快-慢(渐出)*/
transition-timing-function: ease-in-out;  /*慢快慢（首尾速度对称）*/
```

- transition-delay

设置延长动画开始的时间，单位为时间（秒或毫秒）  
**（考点）**：
 - 当此值为负数时，动画会被提前播放，例如-1就是直接从播放时间为1的时候开始播放
 - 当此值为0时，动画立刻播放
``` html
transition-delay: 1s;
```

## transition简写属性  

transition属性支持一次性写完  

标准位置为：  
`transition: property duration timing-function delay`  
**注意！！！**（考点）：  
在简写时出现时间时，看出现的先后顺序来决定其为什么属性：  
只有一个时为duration，两个时第一个为duration，第二个为delay  
``` html
transition: all 1s ease-in-out 0.5s;
```


## 示例

``` html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>transition-property属性</title>
		<style type="text/css">
			.one{
				width:200px;
				height:100px;
				background:#ffaa00;         		
				transition-property: all;	            /*all全部拥有效果*/				
				transition-duration: 1s;	            /*默认(未设置时)为0，所以必须要设置才有效果*/
				transition-timing-function:ease-out;	/*速度控制*/
				transition-delay: 0.5s;	              /*延时*/    				
				/*简写*/
				transition: all 1s ease-in-out 0.5s;				
			}
      /*常常与类似鼠标悬浮hover属性相关的配合使用：*/
			.one:hover{
        width: 500px;
        height: 800px;
        background-color:  blue;
        color: white;
      }	 
		</style>
	</head>
	<body>
		<div class="one">观察宽度和高度的变化</div>
	</body>
</html>  
```

## 好玩的-遮罩层

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>遮罩层</title>
    <style>
    .box {
      background-image: url(../material/Applelogo.png);
      border: 5px solid black;
      width: 400px;
      height: 200px;

      /* 设置超出部分隐藏 */
      overflow: hidden;
      /* 父级需设置为相对定位，作为遮罩的定位容器 */
      position: relative;
    }
    .box p {
      background-color: rgba(0, 0, 0, 0.5);
      margin: 0;
      width: 100%;
      height: 100%;

      /* 遮罩初始位于盒子下方，需位置到父元素外侧 */
      top: 100%;
      left: 0;

      transition: all 1s;
      position: absolute;
    }
    /*重点：使用复合选择器：在box类中的p类在hover时会：*/
    .box:hover p {
      /* hover 时回到顶部，盖住图片 */
      top: 0;
    }
  </style>
</head>
<body>
    <div class="box">
    <p></p>
    </div>
</body>
</html>
```