---
title: note10-TS函数声明
date: 2026-10-26 20:50:59
tags: 
    - Arkts 
    - typescript
---

## typescript中函数声明的三种方式

### 普通函数声明
``` ts
function sum1(x:number,y:number):number{
    console.log(x+y);
    return (x+y);
}
```
### 函数表达式(=function)
``` ts
let sum2=function(x:number,y:number):number{
    console.log(x+y);
    return (x+y);
}
```
### 箭头函数(=>)
``` ts
let sum3=(x:number,y:number):number=>{
    console.log(x+y);
    return (x+y);
}
```