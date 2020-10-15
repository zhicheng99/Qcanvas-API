序号|名称|类型|是否必需（创建对象）| 说明
---|---|---|---|---
1|qarcVersion|String|否（自动生成）| Qarc类版本号
2|qcanvas|Object|否（自动生成）| Qcanvas类实例
3|TYPE|String|否（自动生成）| 圆类型标记 'arc' （注：不允许修改）
4|lineWidth|Number|否| 边线粗细
5|start|Array Or Fun|否| 圆心坐标
6|r|Number| 否|半径
7|sAngle|Number|是| 开始角度
8|eAngle|Number|是| 结束角度
9|borderColor|String|否| 边线颜色
10|counterclockwise|Boolean|否| False = 顺时针，true = 逆时针。
11|fillColor|String|是|填充色
12|opacity|Number|否|填充色透明度(最大为1) 
13|drag|String/Boolean|否|是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':可能横向拖动）
14|pointerEvent|String|否|是否响应事件（默认'auto':响应，'none':不响应）
15|mousedown|Fun|否|事件
16|mousemove|Fun|否|事件
17|mouseup|Fun|否|事件
18|mouseout|Fun|否|事件
19|touchstart|Fun|否|事件
20|touchmove|Fun|否|事件
21|touchend|Fun|否|事件
22|like|String|否|边线的样式（'-':实线 '--':虚线）
23|dragRange|Array|否|限制拖动的区域(限制start的值) 必须为两个坐标点[[左上角x,左上角y]，[右下角x,右下角y]]
24| mouseenter | Fun | 否 | 事件 



***
> ##### 1、qarcVersion (String)
Qarc类版本号
function Qarc(qcanvas){
	**this.qarcVersion = '1.0';**
	this.qcanvas = qcanvas;
}

***
> ##### 2、qcanvas (String)
Qcanvas类实例
function Qarc(qcanvas){
	this.qarcVersion = '1.0';
	**this.qcanvas = qcanvas;**
}

***
> ##### 3、TYPE(String)
圆类型标记 'arc' （注：不允许修改）

***
> ##### 4、lineWidth(Number)
边线粗细

***
> ##### 5、start(Array Or Function)
圆心坐标

***
> ##### 6、r(Number)
半径

***
> ##### 7、sAngle(Number)
开始角度 

***
> ##### 8、eAngle(Number)
结束角度 

***
> ##### 9、borderColor(String)
边线颜色

***
> ##### 10、counterclockwise(Boole)
方向 False = 顺时针，true = 逆时针。

***
> ##### 11、fillColor(String)
填充色
***
> ##### 12、opacity(Number)
填充色透明度
***
> ##### 13、drag(Boole)
是否可以拖动（默认true）

