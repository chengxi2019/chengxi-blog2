---
title: note8-html属性选择器
date: 20261025210631
tags:
---

# 属性选择器

通过在style中的类标签中加入挑选条件,已实现统一类名实现不同效果,
属性选择器：通过元素的 HTML 属性或属性值来选中元素，语法为 [属性]、[属性=值] 等。

快速总结:

| 类型 | 备注 | 符号 |
| :--- | :---: | ---: |
| 完全等于 | 可用空格与其他隔开 | = |
| 包含 | （单独存在不与其他接触） | ~= |
| 分隔 | 使用-分隔后开头符合的,或直接是完全等于的 | '|=' |
| 开头 | - | ^= |
| 结尾 | - | $= |
| 含有 | 只要有就可以 | *= |

特殊:
完全对应,一字不差: 
`div[class][class=A]{...}` 

``` html
<style>        
        
         div[class]{color: blue;}              /*仅需拥有class属性即符合*/
         div[class="cod"]{color: green;}       /*class属性为cod的符合*/
         div[class~="cod"]{color: red;}        /*class属性中包含cod的（单独存在不与其他接触）符合*/
      
         div[class|=cod]{color: yellow;}       /*class属性为使用-分隔后开头为cod的或直接是cod的 */
         div[class^=cod]{color: orange;}       /*class属性为cod开头的*/
         div[class$=cod]{color: purple;}       /*class属性为cod结尾的*/

         div[class*=cod]{color: gray}          /*class属性只要含有cod即可*/
         div[class][class=cod]{color: pink}    /*拥有class属性且class属性必须完全符合cod才可  */
        
    </style>
```
