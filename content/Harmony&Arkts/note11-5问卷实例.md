---
title: note11-5问卷实例
time: 2026-11-05 23:21:39
tag: 
---

### 问卷示例代码

``` ts
import { promptAction } from "@kit.ArkUI";

interface iQuestionType{    //1.定义调查问题类型接口
  singleChoice:string;
  multiChoice:string[];
  fillIn:string;
  starRating:string;
}
interface iQuestiongInterface{  //2.定义多选题接口
  key:string;
  lable:string;
}
@Entry
@Component
struct Index {
  @State singleAnswer: string = '';
  @State multiAnswer:string[]=[];
  @State fillAnswer:string='';
  @State starRating:number=0;
  private singleOptions:string[]=['A.非常满意', 'B.满意', 'C.一般', 'D.不满意', 'E.非常不满意'];
  private multiOptions:iQuestiongInterface[]=[
    {key:"OptionsA",lable:"功能丰富"},{key:"OptionsB",lable:"界面美观"},
    {key:"OptionsC",lable:"性能流畅"},{key:"OptionsD",lable:"交互良好"}  ];
  build() {
    Column({space:10}){
      Text("智能产品满意度调查").fontSize(30).fontWeight(600)
      Scroll(){
        Column(){
          Column(){   //3.单选题
            Text("1. 您对产品的整体满意度如何？(单选)").fontSize(20).fontWeight(600).width('100%')
            ForEach(this.singleOptions,(item:string)=>{
              Row(){
                Radio({value:item,group:"singleGroup"}).onChange((isChecked:boolean)=>{
                  if(isChecked){  this.singleAnswer=item;  }
                })
                Text(item).fontSize(18)
              }.width('100%')
            })
          }.width('100%').backgroundColor(0xF3f3f3).padding(10).borderRadius(20)
        Divider().width('98%').strokeWidth(2).color(Color.Red).margin({top:10,bottom:10})
        Column(){   //4.多选题
          Text("2. 您最喜欢产品哪些方面？（多选）").fontSize(20).fontWeight(600).width('100%')
          ForEach(this.multiOptions,(item:iQuestiongInterface)=>{
            Row(){
              Checkbox({name:item.lable,group:"chkGroup"}).shape(CheckBoxShape.ROUNDED_SQUARE)
                .onChange((isChecked:boolean)=>{
                  if(isChecked){ this.multiAnswer.push(item.lable); }
                })
              Text(item.lable).fontSize(18)
            }.width('100%')
          })
        }.width('100%').backgroundColor(0xD3F3F3).padding(10).borderRadius(20)
        Column(){   //5.填空题
          Text("3.您对我们产品或服务有什么建议？(填空)").fontSize(20).fontWeight(600).width('100%')
          TextArea({placeholder:"填写宝贵意见"}).height(100).width('100%')
            .onChange((value:string)=>{  this.fillAnswer=value;  })
        }
        Column(){ //6.星级评价
          Text("4. 请为我们的产品打分（星级评价）").fontSize(20).fontWeight(600).width('100%')
          Rating().height(40).width(200).onChange((value:number)=>{  this.starRating=value; })
        }
        Button("提交问卷").fontSize(20).width('50%').onClick(()=>{ this.submitSurvey(); })
        }.width('100%')
      }
    }.height('100%').width('100%')
  }
  submitSurvey(){
    const surveyResult:iQuestionType={
      singleChoice:this.singleAnswer || '未选择',
      multiChoice:this.multiAnswer.length>0?this.multiAnswer:['未选择'],
      fillIn:this.fillAnswer || '未填写',
      starRating:this.starRating===0?'未评分':`${this.starRating}星`
    }
    promptAction.showDialog({
      title:"问卷提交成功",
      message:`您填写的数据：
      1.满意度：${surveyResult.singleChoice}
      2.多选结果：${surveyResult.multiChoice.join('、')}
      3.宝贵意见：${surveyResult.fillIn}
      4.星级评价：${surveyResult.starRating}  `,
      buttons:[{text:"确定",color:'#007AFF'}]
    })
  }
}
```