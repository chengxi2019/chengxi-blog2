---
title: note10-29html定位属性
time: 2026-10-29 22:24:24
tag: 
    - position
    - z-index
---

## 元素定位方式属性position

position定位属性使用方式：

``` html
position: static;       /*默认，默认效果(无)*/
position: absolute;     /*绝对值，坐标原点为画面左上角*/
position: relative;     /*相对位置:相对于原本的位置*/
```
**单独设置position属性没有效果！**  
需要再使用偏移属性配合才有效果：`top bottom left right `  
(分别对应上下左右，具体见下方示例代码)  
偏移属性可以为负数  

 
## z-index属性
设置z轴的值，当画面中有多个元素重叠时，此值越大的元素越靠上
**z-index的值默认为1**

``` html
z-index: 1;
z-index: 2;     /*设置z-index值为2的元素会遮盖在z-index值为1的元素上*/
```

### 示例代码

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>1029</title>
    <style>
        .one{
            background-color: red;
            width: 100px;
            height: 100px;
            position: absolute;
            top: 100px;
        }
        .two{
            background-color: yellow;
            width: 100px;
            height: 100px;
            position: absolute;
            top: 10px;
            
        }
        .three{
            background-color: green;
            width: 50px;
            height: 50px;
            position: relative;
            left: 0px;
            top: 0px;
            
        }
        .four{
            background-color: pink;
            width: 100px;
            height: 100px;
            position: absolute;
            right: 100px;
            top: 100px;
            z-index: 2;
        }

        .five{
            background-color: gray;
            width: 100px;
            height: 100px;
            position: absolute;
            right: 110px;
            top: 110px;
        }
    </style>
</head>
<body>
    <div class="one">1</div>
    <div class="two">2<div class="three">3</div></div>
    <div class="four">4</div>
    <div class="five">5</div>
</body>
</html>
```

### 有关absolute与relative的疑难杂症

position属性的值中`absolute`与`relative`属性考试可能会考，故有此篇：  

**absolute**  
设置为此属性时，脱离文档流(元素本身会偏离原来的位置)，原位置可以被其他元素占用，  
偏移后以其父元素的末尾为坐标原点，
如果没有父元素，则以画面左上角为坐标原点，  
可以与其他元素重叠  

**relative**  
设置为此属性时，不脱离文档流(元素本体不偏移原来的位置)，原来的位置不可以被其他元素占用，仅视觉上发生偏移，但布局上仍在原地，当然原位置不可以被其他元素占用  
本体所处位置不可以与其他元素重叠，但偏移后的显示内容可能盖住别的元素，形成视觉重叠。