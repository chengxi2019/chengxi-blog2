---
title: note11-4htmlflex属性
time: 2026-11-04 23:06:33
tag: 
    - flex
    - flex-direction
---

## Flex属性值

flex属性，专业名称为弹性盒子  
此属性值是**display属性**的一部分，无法单独使用！！！  

设置了此属性的子元素将撑满父元素内部  
依据子元素的flex属性值的大小，决定该子元素在父元素内所占用的空间大小  
比如示例中的div中的p标签，flex的值分别设置为1,2,3，便能够实现从小到大的效果

设置了此属性后，子元素的float、clear和vertical-align属性无法起作用  
当然水平方向时width不起作用，竖直方向时height不起作用  

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        section{
            border: 2px solid black;
            height: 800px;
            width: 500px;
            display: flex;  /*需先将display设置为flex*/
            flex-direction:row;     /*默认值为row*/
            /* flex-direction:row-reverse; 左右排列但是是反向*/
            /*当设置为水平方向时，子元素的width属性就不生效了，竖直方向同理*/                        
        }
        div:first-child{
            border: 1px solid red;
            height: 800px;
            width: 100px;
            flex: 3;    /*需配合flex具体数值才能生效*/
            /*示例2部分*/
            display: flex;
            flex-direction: column;  /* flex-direction: column; 上下排列*/
            /*当设置为竖直方向时，子元素的height属性就不生效了，水平方向同理*/
            margin: 0px; 
        }
        div:nth-child(2){
            border: 1px solid blue;
            height: 50px;
            width: 100px;
            flex: 2;    /*flex值越大元素占用的位置也越大*/
        }
        div:last-child{
            border: 1px solid green;
            height: 50px;
            width: 100px;
            flex: 1;
        }
        

        div p{
            margin: 0px;
        }                          
        div p:first-child{
            background-color: gray;
            flex: 1;
        }
        div p:nth-child(2){
            background-color: pink;
            flex: 2;
        }
        div p:last-child{
            background-color: red;
            flex: 3;
        }
        
        </style>
</head>
<body>
    <section>
        <div>1
            <p>A</p>
            <p>B</p>
            <p>C</p>
        </div>
        <div>2</div>
        <div>3</div>        
    </section>
</body>
</html>
```