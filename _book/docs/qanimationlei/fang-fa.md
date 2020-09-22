| 序号 | 名称 | 说明 |
| --- | --- | --- |
| 1 | animate | 为对象生成animation属性 |
| 2 | createAnimation | 改变对象某些属性 生成动画 |

---

> ##### 1、animate
>
> 为对象生成animation属性  
> 接收参数（aim,startStyle,endStyle,during,isLoop,tween,finishCallback）  
> aim：对象  
> startStyle：起始状态对象或数值 例如：{start:\[0,0\]}  
> endStyle：结束状态对象或数值 例如：{start:\[100,100\]}  
> during：动画时长 单位（秒）  
> isLoop：是否循环播放动画 （false\|true|次数）
> tween：动画方式 （为空时 默认为Linear方式）
> finishCallback：回调函数（动画完成后）

tween动画方式
```
Linear
Quad.easeIn
Quad.easeOut
Quad.easeInOut
Cubic.easeIn
Cubic.easeOut
Cubic.easeInOut
Quart.easeIn
Quart.easeOut
Quart.easeInOut
Quint.easeIn
Quint.easeOut
Quint.easeInOut
Sine.easeIn
Sine.easeOut
Sine.easeInOut
Expo.easeIn
Expo.easeOut
Expo.easeInOut
Circ.easeIn
Circ.easeOut
Circ.easeInOut
Elastic.easeIn
Elastic.easeOut
Elastic.easeInOut
Back.easeIn
Back.easeOut
Back.easeInOut
Bounce.easeIn
Bounce.easeOut
Bounce.easeInOut

```


生成animation属性示例

```
animation:{
    'framesIndex':0, //当前帧
    'framesCount':10,//总帧数
    'during':2,//运行时间
    'frames':{start:[[0,0],[1,0],[2,0]....]},//序列帧对象
    'isLoop':true,    //是否循环播放
}
```

代码示例

```
qcanvas.qanimation.animate(line1,{
        start:[0,80],
    },{
        start:[100,80],
    },2,true);

要求属性的值能够线性变化
```

---

> ##### 2、createAnimation
>
> 改变对象某些属性  
> 该方法用于被以下方法调用  
> Qline类 paintLine方法  
> Qtext类 paintText方法  
> Qarc类 paintArc方法  
> Qpolygon类 paintPolygon方法  
> Qrect类 paintRect方法

paint类型的方法都是在每个动画周期调用的，所以把改变对象某些属性的功能放在此处 就可以在渲染时生成动画。

