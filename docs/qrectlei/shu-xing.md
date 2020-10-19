| 序号 | 名称 | 类型 | 是否必需（创建对象） | 说明 |
| --- | --- | --- | --- | --- |
| 1 | qrectVersion | String | 否（自动生成） | Qrect类版本号 |
| 2 | qcanvas | Object | 否（自动生成） | Qcanvas类实例 |
| 3 | TYPE | String | 否（自动生成） | 矩形类型标记 'rect' （注：不允许修改） |
| 4 | lineWidth | Number | 否 | 矩形边线粗细 |
| 5 | start | Array Or Fun | 否 | 矩形左上角坐标 |
| 6 | width | Number Or Fun | 否 | 矩形宽 |
| 7 | height | Number Or Fun | 否 | 矩形高 |
| 8 | borderColor | String | 否 | 矩形边线颜色 |
| 9 | fillColor | String | 否 | 矩形填充颜色 |
| 10 | drag | String/Boolean | 否 | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':可能横向拖动） |
| 11 | pointerEvent | String | 否 | 是否响应事件（默认'auto':响应，'none':不响应） |
| 12 | mousedown | Fun | 否 | 事件 |
| 13 | mousemove | Fun | 否 | 事件 |
| 14 | mouseup | Fun | 否 | 事件 |
| 15 | mouseout | Fun | 否 | 事件 |
| 16 | touchstart | Fun | 否 | 事件 |
| 17 | touchmove | Fun | 否 | 事件 |
| 18 | touchend | Fun | 否 | 事件 |
| 19 | opacity | Number | 否 | 填充色透明度\(最大为1\) |
| 20 | degree | Number | 否 | 旋转角度（-360~360） |
| 21 | radius | Number | 否 | 圆角度数 |
| 22 | resize | Boolean | 否 | 是否启用缩放控件 |
| 23 | rotate | Boolean | 否 | 是否启用角度控制控件 |
| 24 | dashed | Boolean | 否 | 边线是否为虚线 |
| 25 | mouseenter | Fun | 否 | 事件 |
| 27 | dblclick | Fun | 否 | 事件 |


---

> ##### 1、qrectVersion\(String\)
>
> Qrect类版本号  
> function Qrect\(qcanvas\){  
>     **this.qrectVersion = '1.0';**  
>     this.qcanvas = qcanvas;  
> }

---

> ##### 2、qcanvas\(Object\)
>
> Qcanvas类实例  
> function Qrect\(qcanvas\){  
>     this.qrectVersion = '1.0';  
>     **this.qcanvas = qcanvas;**  
> }

---

> ##### 3、TYPE\(String\)
>
> 矩形类型标记 'rect' ,不能更改

---

> ##### 4、lineWidth\(Object\)
>
> 矩形边线粗细

---

> ##### 5、start\(Array Or Function\)
>
> 矩形左上角坐标

---

> ##### 6、width\(Number Or Function\)
>
> 矩形宽

---

> ##### 7、height\(Number Or Function\)
>
> 矩形高

---

> ##### 8、borderColor\(String\)
>
> 矩形边线颜色

---

> ##### 9、fillColor\(String\)
>
> 矩形填充颜色



