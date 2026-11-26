---
title: note11-15html网页制作综合
created: 2026-11-25 22:31:36
---

在网页的综合制作中有如下部分还有待完善知识点：  
- 使用ul与li制作的导航栏
- 使用div配合图片img制作的滚动条

### ul与li制作的导航栏
此为较为简洁的格式，并不是最简格式  
示例中使用了空白区域来区分最简格式与较简洁格式  
示例中空白区域上方的是最简格式  
``` html
<style>
    ul,li{list-style: none;padding: 0;}    /*去除所有的列表样式*/
    ul{
        display: flex;
        
        background-color: gray;
        }
    li{
        position: relative;

        background-color: aqua;
        margin: 10px;
        width: 33%;
        text-align: center;
    }
    .in_ul{
        display: none;
        position: absolute;
        top: 100%;
        left: 0px;
        padding: 0;

        width: 100%;
    }
    .in_ul li{
        width: 80%;
        margin:  10px auto;
        
    }
    li:hover .in_ul{
        display: block;
    }
</style>

主体部分：  
``` html
<body>
    <ul>
        <li>
            一
            <ul class="in_ul">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </li>
        <li>
            二
            <ul class="in_ul">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </li>
        <li>
            三
            <ul class="in_ul">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </li>
        <li>
            四
            <ul class="in_ul">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </li>
        <li>
            五
            <ul class="in_ul">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </li>
    </ul>      
</body>
```
### div制作的滚动条