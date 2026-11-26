---
title: note11-25A跳转
created: 2026-11-25T11:05:56
---


### 跳转
最基础：
``` ts
@Entry
@Component
struct NavPage {
  build() {
    Column(){
      Navigator({target:"pages/Index"}){  //{}中是路径
        Column(){
          Button("Clickme").fontSize(24)
        }
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

简单的计数器（未知用途）  
``` ts
@Component struct CompD{
  @Consume reviewVotes:number;
  build() {
    Column(){
      Text(`票数：(${this.reviewVotes})`).fontSize(20)
      Button(`票数：(${this.reviewVotes},give+1)`).fontSize(20)
        .onClick(()=>{this.reviewVotes += 1;})
    }.width('50%')
  }
}
@Component struct CompC{
  build() {
    Row(){ CompD();CompD();}
  }
}
@Component struct CompB{
  build() {
     CompC();
  }
}
@Entry @Component struct CompA{
  @Provide reviewVotes:number=0;
  build() {
    Column(){
      Button(`reviewVotes(${this.reviewVotes},give+1)`).fontSize(20)
        .onClick(()=>{this.reviewVotes += 1;})
      CompB();
    }
  }
}

```

### 带数据的跳转
跳转前，数据收集页  
``` ts
import { router } from "@kit.ArkUI";

@Entry
@Component
struct RegisterPage {
  @State username: string = '';
  @State userpass: string = '';
  @State userage: number = 18;


  build() {
    Column({space:10}){
      TextInput({placeholder:'输入账号'}).placeholderFont({size:22})
        .fontSize(22).onChange((value:string)=>{this.username=value;})
      TextInput({placeholder:'输入密码'}).placeholderFont({size:22})
        .type(InputType.Password).fontSize(22)
        .onChange((value:string)=>{this.userpass=value;})
      TextInput({placeholder:'输入年龄'}).placeholderFont({size:22})
        .fontSize(22).onChange((value:string)=>{this.userage=parseInt(value);})
      Button('注册').fontSize(22).width('60%').onClick(()=>{
        router.pushUrl({
          url:"pages/navPage",params:{uName:this.username,uPass:this.userpass,uAge:this.userage}
        })
      })
    }
    .height('100%')
    .width('100%')
  }
}
```
### 数据展示部分
跳转后，数据展示页  
``` ts
import { router } from "@kit.ArkUI"

@Entry
@Component
struct NavPage {
params=router.getParams() as Record<string,string>;
  build() {
    Column(){
      Text("注册信息：").fontSize(28).fontWeight(600)
      Text(`
      账号${this.params.uName}\n
      密码:${this.params.uPass}\n
      年龄:${this.params.uAge}`)
      Navigator({target:"pages/Index"}){
        Column(){
          Button("Clickme").fontSize(24)
        }
      }
    }
    .height('100%')
    .width('100%')
  }
}
```