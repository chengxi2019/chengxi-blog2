---
title: note7-html表单2
date: 2026-10-25 20:59:46
tags:
---

# 表单2
``` html
<form action="#">
            
    <p>细分input类型： 
        name属性可不写，仅做示例，实际需要 <br>
    </p>  

    邮箱 <br>
    <input type="email" name="email1"> <br>

    网址 <br>
    <input type="url" name="url1"> <br>

    数字 <br>
    <input type="number" max="100" min="0" step="2" value="0" name="name1"> <br>            
    附注： 
    <br>

    范围滑块 <br>
    <input type="range" min="30" max="60" name="range1"> <br>

    日期 <br>
    <input type="date" name="date1"> <br>            
    附注：
    <br>

    选取颜色 <br>
    <input type="color" name="color1"> <br>

    搜索，用于目前网页搜索 <br>
    <input type="search" name="search1"> <br>

    标签定义选项列表 <br>    
    <input type="text" name="text1" list="A">
    <datalist id="A">
        <option value="真值1">提示词1</option>
        <option value="真值2">提示词2</option>
    </datalist> <br>
    附注：此标签不会于出现网页中，仅作为与其配合的输入框的待选选项 <br>       
                  
</form>

```
## 表单属性

``` html
<form action="#">            
        表单属性： <br>

        required必填项 <br>
        <input type="text" required> <br>

        placeholder：提示信息 <br>
        <input type="text" placeholder="提示信息示例"> <br>

        pattern正则表达式 <br>
        <input type="text" pattern=""> <br>
        用途	            正则 <br>
        手机号（中国）	^1[3-9]\d{9}$ <br>
        邮箱	        ^[\w.-]+@[\w.-]+\.\w+$ <br>
        身份证（18位）	^\d{17}[\dXx]$ <br>
        中文	        ^[\u4e00-\u9fa5]+$ <br>
        数字	         ^-?\d+(\.\d+)?$ <br>
        有待补充 <br>

        autocomplete自动填充 <br>
        <input type="text" autocomplete="additional-name"> <br>
        属性与预期有出入，待补充 <br>
        未知补充 <br>

        novalidate不验证输入，可加在form标签中以对整个表单生效 <br>            
        <input type="text" novalidate >

        autofocus自动获得焦点 <br>
        <input type="text" autofocus> <br>
        
        <br> 示例提交按钮 <br>
        <input type="submit" name="submit1" > <br> 
</form>

```

>week7所学