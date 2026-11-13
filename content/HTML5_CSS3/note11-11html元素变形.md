---
title: note11-11变形
created: 2026-11-11T0:49:08
tag: 
    - translate
    - scale
    - rotate
    - skew
---

## 元素变形transform

### 位移translate  
格式：`transform: translate(10px,10px)`  
第一个属性值为水平方向，第二个为垂直方向  
参考position中的relative，仅视觉偏移，元素本身未真正移动  
``` html
p:nth-child(1){height: 50px;width: 50px; transform: translate(10px); background-color: brown;}
p:nth-child(2){height: 50px;width: 50px; transform: translate(-10px,-10px); background-color: brown;}
```

### 缩放scale
格式：`transform: scale(1.5)`
只有一个参数时同时对xy轴缩放,而存在两个参数时，分别对xy轴缩放  
注意：  
- 1的正数为放大，<1的正数为缩小  
- 负数就是缩放的同时再进行反转  
``` html
p:nth-child(3){height: 50px;width: 50px; transform: scale(0.8) ;background-color: pink;}
p:nth-child(4){height: 50px;width: 50px; transform: scale(1.5,-1.5) ;background-color:  pink;}
```

### 旋转rotate
格式：`transform: rotate(30deg)`
正数时为顺时针旋转，负数时为逆时针旋转  
``` html
p:nth-child(5){height: 50px;width: 50px; transform: rotate(60deg); background-color: skyblue;}
```

### 倾斜skew
格式：`transform: skew(-45deg)`  
transform: skew(0deg,-30deg)  
正数为顺时针倾斜，负数为逆时针倾斜  
- 仅有一个参数时仅对x轴倾斜(第二个值为0deg)  
- 有两个参数时分别对x,y轴倾斜   
``` html
p:nth-child(6){height: 50px;width: 50px; transform: skew(45deg); background-color: green;}
p:nth-child(7){height: 50px;width: 50px; transform: skew(-45deg,60deg); background-color: green;}
```