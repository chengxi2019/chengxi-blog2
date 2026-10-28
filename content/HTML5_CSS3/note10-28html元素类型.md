---
title: note10-28html元素类型
time: 2026-10-28 22:41:45
tag: 
    - display
    - inline
    - block
---

修改：margin与padding属性新增auto,单个属性值的意义  

## 元素类型：

**块元素block**：
`(略，大多数几乎都是块元素，有待补充)`  
  总是新开一行，高度宽度可控，内外边距可控  

**行内元素inline**：
`a span i u b em sub sup ~等`  
  总是与其他元素处于一行，高度宽度不可改变，内外边距不可改变  

**行内块元素inline-block**：
`img input`  
  本身是行内元素，但具有块元素可变高宽度等的属性

## 元素类型强制转变display属性：
- block             转为块元素
- inline            转为行内元素
- inline-block      转为行内块元素

## 综合示例：

``` html
<style>
        p,div{
            padding: 10px;
            background-color: gray;
            width: 200px;
            height: 100px;
            display: inline;  /*设置display属性为inline后强转为行内元素，失去块元素属性*/
        }
        a{
            padding: 10px;;
            background-color: gray;
            width: 200px;        /*行内元素设置高度宽度边距等属性无效*/
            height: 100px;       /*行内元素设置高度宽度边距等属性无效*/
            display: block;      /*设置display属性为block后强转为块元素，可实现块元素属性*/
        }
    </style>
```