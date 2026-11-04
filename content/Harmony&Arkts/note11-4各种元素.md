---
title: note11-4各种元素
date: 2026-11-04 23:22:47
tags:     
---

包含评分，滚动条，打开页面(自行摸索)，计数器(未完成),下拉菜单  

``` ts
import { Router } from '@ohos.arkui.UIContext';
import { router } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State starnum: number = 4;
  @State strcontent:string= '永远相信美好的事情即将发生';
  @State isstart:boolean=true;
  @State province:string = ' ';
  @State count:number = 20;

  build() {
    Column(){
      Rating({rating:2,indicator:false}).stars(6).stepSize(1)
      //rating:默认评分，indicator：是否不可更改//star最大值
        .onChange((value:number)=>{this.starnum=value;})
      //onchange实时获取值的变化
      Text(`获取评分星级：${this.starnum}`).fontSize(24)

      Divider().strokeWidth(1)

      Column(){
        //滚动条
        Marquee({start:this.isstart,step:6,loop:-1,fromStart:true,src:this.strcontent})
          .fontSize(36).width('100%').height(200).background(Color.Gray).fontColor(Color.White)
          .onClick(()=>{this.isstart=!this.isstart;}) //点击以停止
      }

      Divider().strokeWidth(1)

      Button('打开目标页面')
        .onClick(() => {
          // 使用 pushUrl 进行跳转
          router.pushUrl({
            url: 'components/AAAPage',
            params: { id: 123 } // 可选：传递参数
          });
        })

      //计数器-未完成
      // Counter(){
      //   Text(this.count.toString()).fontSize(24).width('45%').height(50)
      //     .onInc(()=>{this.count++;})
      //     .onDec(()=>{if(this.count>0){this.count--}})
      // }



//下拉菜单
      Select([
        { value: '北京市', icon: $r('app.media.startIcon') },
        { value: '天津市', icon: $r('app.media.startIcon') },
        { value: '上海市', icon: $r('app.media.startIcon') },
        { value: '重庆市', icon: $r('app.media.startIcon') },
        { value: '河北省', icon: $r('app.media.startIcon') },
        { value: '山西省', icon: $r('app.media.startIcon') },
        { value: '辽宁省', icon: $r('app.media.startIcon') },
        { value: '吉林省', icon: $r('app.media.startIcon') },
        { value: '黑龙江省', icon: $r('app.media.startIcon') },
        { value: '江苏省', icon: $r('app.media.startIcon') },
        { value: '浙江省', icon: $r('app.media.startIcon') },
        { value: '安徽省', icon: $r('app.media.startIcon') },
        { value: '福建省', icon: $r('app.media.startIcon') },
        { value: '江西省', icon: $r('app.media.startIcon') },
        { value: '山东省', icon: $r('app.media.startIcon') },
        { value: '河南省', icon: $r('app.media.startIcon') },
        { value: '湖北省', icon: $r('app.media.startIcon') },
        { value: '湖南省', icon: $r('app.media.startIcon') },
        { value: '广东省', icon: $r('app.media.startIcon') },
        { value: '海南省', icon: $r('app.media.startIcon') },
        { value: '四川省', icon: $r('app.media.startIcon') },
        { value: '贵州省', icon: $r('app.media.startIcon') },
        { value: '云南省', icon: $r('app.media.startIcon') },
        { value: '陕西省', icon: $r('app.media.startIcon') },
        { value: '甘肃省', icon: $r('app.media.startIcon') },
        { value: '青海省', icon: $r('app.media.startIcon') },
        { value: '台湾省', icon: $r('app.media.startIcon') },
        { value: '内蒙古自治区', icon: $r('app.media.startIcon') },
        { value: '广西壮族自治区', icon: $r('app.media.startIcon') },
        { value: '西藏自治区', icon: $r('app.media.startIcon') },
        { value: '宁夏回族自治区', icon: $r('app.media.startIcon') },
        { value: '新疆维吾尔自治区', icon: $r('app.media.startIcon') },
        { value: '香港特别行政区', icon: $r('app.media.startIcon') },
        { value: '澳门特别行政区', icon: $r('app.media.startIcon') }
      ]).value("请选择省份").selected(0).onSelect((index: number, value: string) => {this.province = value;})
      if (this.province != ' ') {Text(`你来自${this.province}`).fontSize(22)}

      Divider().strokeWidth(1)
    }
    .height('100%')
    .width('100%')


  }
}
```