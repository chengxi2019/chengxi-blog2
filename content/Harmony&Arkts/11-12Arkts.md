---
title: note11-12各种元素
created: 2026-11-12T14:55:35
tag:
---

包含定位，还有第二部分    

``` ts
@Entry
@Component
struct index1 {
  build() {
    Flex({direction:FlexDirection.Column}){
      Flex({wrap:FlexWrap.Wrap}){
        Text('元素1').txtStyle(0x33aacc)
        Text('元素2').txtStyle(0x3f3efc).fontColor(Color.White)
        Text('元素3').txtStyle(0x33aacc)
        Text('元素4').txtStyle(0x339933)
        Text('元素5').txtStyle(0xf3aacc)
        Text('元素6').txtStyle(0x339933)
        Text('元素7').txtStyle(0x3f3efc).fontColor(Color.White)
      }.width('150%').height(150).backgroundColor(Color.Orange)

      Flex({direction:FlexDirection.Column}){
        Text('元素1').txtStyle(0x33aacc)
        Text('元素2').txtStyle(0x3f3efc).fontColor(Color.White)
        Text('元素3').txtStyle(0x33aacc)
        Text('元素4').txtStyle(0x339933)
        Text('元素5').txtStyle(0xf3aacc)
        Text('元素6').txtStyle(0x339933)
        Text('元素7').txtStyle(0x3f3efc).fontColor(Color.White)
      }.width('150%').height(350).backgroundColor(Color.Yellow).margin({top:10})
    }.height('100%').width('100%')
  }
}
@Extend(Text) function txtStyle(bgcolor:number){
  .fontSize(22).width('20%').height(50).textAlign(TextAlign.Center).backgroundColor(bgcolor)
}
```

第二部分  

``` ts
@Entry
@Component
struct FlexPage {
  @State message: string = 'hello world'
  build() {
    RelativeContainer(){
      Image($r('app.media.startIcon')).width(100).id('imgStart').alignRules({
          center:{ anchor:'__container__',align:VerticalAlign.Center},
          middle:{ anchor:'__container__',align:HorizontalAlign.Center}
        })

      Row(){
        Text('左上').fontSize(22).width('100%').textAlign(TextAlign.Center)
      }.width(100).height(100).backgroundColor(0xff0898).borderRadius(10).id('leftT').alignRules({
        bottom:{anchor:"imgStart",align:VerticalAlign.Top},
        right:{anchor:"imgStart",align:HorizontalAlign.Start}
      })
      Row(){
        Text('左下').fontSize(22).width('100%').textAlign(TextAlign.Center)
      }.width(100).height(100).backgroundColor(0xff013).borderRadius(10).id('leftB').alignRules({
        top:{anchor:"imgStart",align:VerticalAlign.Bottom},
        right:{anchor:"imgStart",align:HorizontalAlign.Start}
      })

      Row(){
        Text('右上').fontSize(22).width('100%').textAlign(TextAlign.Center)
      }.width(100).height(100).backgroundColor(0xff091).borderRadius(10).id('rightT').alignRules({
        bottom:{anchor:"imgStart",align:VerticalAlign.Top},
        left:{anchor:"imgStart",align:HorizontalAlign.End}
      })
      Row(){
        Text('右下').fontSize(22).width('100%').textAlign(TextAlign.Center)
      }.width(100).height(100).backgroundColor(0xff0560).borderRadius(10).id('rightB').alignRules({
        top:{anchor:"imgStart",align:VerticalAlign.Bottom},
        left:{anchor:"imgStart",align:HorizontalAlign.End}
      })
    }.height('100%').width('100%')
  }
}
```