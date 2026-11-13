---
title: note11-12_3D变形
created: 2026-11-12T10:45:23
tag:
	- perspective
	- translate
	- rotate
---

进入前，先明确一个点：  
在html5中，立体透视图中的各个轴的位置，方位：  
```
        y（上，垂直轴）
        │
        │
        └────── x（右，水平轴）
       ╱
     z（朝你/朝屏幕外）

```

### 镜头距离perspective
作用：设置镜头的距离，是设置3d效果的前置  
给子元素提供 3D 透视，控制"近大远小"的强度  
考点：值越小，透视越强，值越大，透视越弱  
此属性需要设置在**父元素**中，对其子元素生效！  
格式：`perspective: 400px;`
>有关此属性与transform: perspective()的区别见疑难解答  

### 3D平移translate
格式：
``` html
transform:translateX(50px)	/*X轴*/
transform:translateY(50px)	/*Y轴*/
transform:translateZ(50px)	/*Z轴*/
```
要实现类似3d缩放的效果请使用：`translateZ`更改Z轴距离来实现类似的效果  

### 简写格式：3D平移translate3D()
作用：3D平移的简写格式  
格式：`transform:translate3d(30px,30px,30px)`  
**注意：**  
使用简写格式时，须一次写完3个轴的属性，无需求的轴可用0px代替   

>有关Z轴(缩放)的问题见疑难解答  


### 3D缩放scale
格式：
``` html
transform: scaleX(1.5);		/*X轴*/
transform: scaleY(1.5);		/*Y轴*/
transform: scaleZ(1.5);		/*Z轴*/
```
**注意：**  
在单独使用3dscale缩放时，x与y轴看起来与普通2d缩放效果一样，z轴没有变化，是正常现象  
z轴需与配合其他属性使用才有效果  

### 简写格式：3D缩放scale3D()
格式：`scale3d(1,1,1)`  
使用简写格式时，须一次写完3个轴的属性，无需求的轴用`1`代替  


### 3D旋转rotateX-Y-Z
格式：
``` html
transform:rotateX(45deg);	/*X轴*/
transform:rotateY(45deg);	/*Y轴*/
transform:rotateZ(45deg);	/*Z轴*/
```

### 3D旋转rotate3D简写格式：
格式：`transform:rotate3d(1,1,1,45deg)`  
作用：前三个值定“绕哪根轴转”（比例定方向），最后的 deg 定“转多少度”  
或者：前三个值按比例确定一根“虚拟轴”的方向，最后一个 deg 决定绕这根轴转多少度。例如 (1,2) 是在 x、y 轴之间偏向 y 轴的位置虚拟出一根轴，再绕它旋转 deg 角度。
>注意：rotate的属性值是缩放倍数，不是像素px！

### 变形基准点：tranform-origin  
作用：设置平移，缩放，旋转的基准点
即围绕那个点转，以那个点为中心旋转  
有待补充  
格式：
``` html
transform-origin: left bottom;
transfrom-origin: 20%;
```

### 附加：
>这部分考试会考？
- 当元素背面朝向观察者时，隐藏该元素的背面（不可见）:
	`backface-visibility: hidden;`

### 疑难解答
- 当使用`transform:translateZ()`语句进行Z轴平移时，可能会出现元素相对于父元素中心朝自身方向偏移的情况，  
	这是与3D透视原理相关：元素越靠近观察者，放大越明显，相对消失点的偏移也被等比放大  
	这与：假如说一个物品在我的偏左前方，我离这个物品越来越近时，它在我的视觉中会越来越向偏左侧方的原理相同
	又或者：一辆车从远处朝你开来，但它不在你的正前方，而是偏左（或偏右），最终从你身边驶过，没撞到你。

- perspective 与 transform: perspective()
	perspective是对子元素生效，而transform: perspective是对自己生效  

### 案例

``` html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>translateZ()与视距</title>
		<style type="text/css">
			section {
				width: 220px;
				height: 220px;
				margin: 20px auto;
				border: 2px solid red;
				perspective: 200px;
			}

			.one {
				width: 200px;
				height: 200px;
				margin: 10px auto;
				background: #ccc;
				transition: all 1s;
			}

			section:hover .one {
				transform: translateZ(10px)
			}

			/* 3D变形效果设置流程：
			1.确定样式 -> 2.常态属性 -> 3.hover属性 -> 4.transition -> 5.父元素perspective。 
			写好一行代码不难，难的是一个综合效果需要每一行代码都逻辑严密、考虑周全（比如不仅考虑自己，还要考虑父元素）。
			大家未来走向工作岗位，无论做何种工作，都要有这种精益求精、一丝不苟的态度。			
			*/
		</style>
	</head>
	<body>
		<section>
			<div class="one">我是一个盒子</div>
		</section>
	</body>
</html>
```

``` html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>3D旋转</title>
		<style type="text/css">
			section{
				width:100px;
				height:100px;
				float:left;
				margin: 50px;
				perspective: 200px;
			}
			div{
				width:100px;
				height:100px;
				background:#ccc;				
				transition: all 1s;
			}
			.two{
				background:rgba(255,0,0,0.5);
				
				}			
			#box1:hover .two{transform:rotateX(60deg)}
			#box2:hover .two{transform:rotateY(60deg)}
			#box3:hover .two{transform:rotateZ(60deg)}				
		</style>
	</head>
	<body>
		<section id="box1">
			<div class="one">我是盒子1</div>
		    <div class="two">我是盒子2X轴</div>
		</section>
		<section id="box2">
			<div class="one">我是盒子1</div>
		    <div class="two">我是盒子2Y轴</div>
		</section>
		<section id="box3">
			<div class="one">我是盒子1</div>
		    <div class="two">我是盒子2Z轴</div>
		</section>		
	</body>
</html>
```