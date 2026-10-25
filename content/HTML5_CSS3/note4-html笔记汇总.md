# CSS 样式练习笔记


### 样式源码示例

### 文本基本
``` html
<style>
        .h1{
            text-align: center;         /* 文本对齐：center居中 / left左 / right右 */
            color: burlywood;           /* 文字颜色 */
            text-indent: 2em;           /* 首行缩进，单位em，原缺少单位 */
            text-decoration: solid;     /* 文本装饰：solid实线，颜色写color */
            text-shadow: none;          /* 文字阴影：none无阴影 */
            letter-spacing: normal;     /* 字符间距 */
            line-height: normal;        /* 行高 */
            vertical-align: text-top;   /* 垂直对齐：文本顶部 */
            word-spacing: normal;       /* 单词间距：默认 */
        }
</style>
```
### 列表
```html
<style>
        .ul{
            list-style-type: square;    /* 列表标记：square方块 / disc圆点 / circle空心圆 */
            list-style-position: inside;/* 列表符号位置：inside向内 / outside向外 */
        }
</style>
```
### 字体
```html      
<style>  
        .font{
            font-family: sans-serif;    /* 字体族：sans-serif无衬线 */
            font-size: large;           /* 字号 */
            font-style: italic;         /* 字体样式：italic斜体 / normal正常 */
            font-weight: bolder;        /* 字重：bolder更粗 / bold加粗 */
        }
</style>  
```
### 超链接
```html      
<style>        
        a:link{color:blue;}           /* 链接：未访问 */
        a:visited{color: gray;}       /* 链接：已访问 */
        a:hover{text-decoration:line-through;}  /* 链接：鼠标悬停 */
        a:active{color: red;}         /* 链接：点击激活瞬间 */
</style>
```

<p class="h1">
    文本示例
</p>
<ul class="ul">
    <li>文本示例</li>
    <li>文本示例</li>
    <li>文本示例</li>
</ul>
<p class="font">字体样式示例</p>
<a href="#">默认</a><br>
<a href="#">已访问</a><br>
<a href="#">悬停</a><br>
<a href="#">点击</a><br>
由于存在本地历史访问记录，未访问链接有时显示为已访问属于正常情况
```