| 序号 | 名称 | 类型 | 是否必需（创建对象） | 说明 |
| --- | --- | --- | --- | --- |
| 1 | qtextVersion | String | 否（自动生成） | Qtext类版本号 |
| 2 | qcanvas | Object | 否（自动生成） | Qcanvas类实例 |
| 3 | TYPE | String | 否（自动生成） | 文本类型标记 'text' （注：不允许修改） |
| 4 | text | String | 否 | 文本内容 |
| 5 | color | String | 否 | 文本颜色 |
| 6 | textAlign | String | 否 | 文本对齐方式（left center\[默认\] right） |
| 7 | fontSize | String | 否 | 文本字号 |
| 8 | fontFamily | String | 否 | 文本字体 |
| 9 | start | Array or Function | 否 | 文本坐标位置 |
| 10 | drag | String/Boolean | 否 | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':可能横向拖动） |
| 11 | pointerEvent | String | 否 | 是否响应事件（默认'auto':响应，'none':不响应） |
| 12 | mousedown | Fun | 否 | 事件 |
| 13 | mousemove | Fun | 否 | 事件 |
| 14 | mouseup | Fun | 否 | 事件 |
| 15 | mouseout | Fun | 否 | 事件 |
| 16 | touchstart | Fun | 否 | 事件 |
| 17 | touchmove | Fun | 否 | 事件 |
| 18 | touchend | Fun | 否 | 事件 |
| 19 | textBaseline | String | 否 | 当前文本基线（top,buttom, middle\[默认\]） |
| 20 | degree | Number | 否 | 旋转角度（-360~360） |
| 21 | lineHeight | String | 否 | 行高 |
| 22 | mouseenter | Fun | 否 | 事件 |



> ##### 1、qtextVersion\(String\)
>
> Qtext类的版本号  
> function Qtext\(qcanvas\){  
>     **this.qtextVersion = '1.0';**  
>     this.qcanvas = qcanvas;  
> }

---

> ##### 2、qcanvas\(Object\)
>
> Qcanvas类实例  
> function Qtext\(qcanvas\){  
>     this.qtextVersion = '1.0';  
>     **this.qcanvas = qcanvas;**  
> }

---

> ##### 3、TYPE\(String\)
>
> 文本类型标记 'text' （注：不允许修改）

---

> ##### 4、text\(String\)
>
> 文本内容

---

> ##### 5、color\(String\)
>
> 文本颜色

---

> ##### 6、textAlign\(String\)
>
> 文本对齐方式  
> 文本主体和start坐标位置的对齐方式  
> left center\[默认\] right

---

> ##### 7、fontSize\(String\)
>
> 文本字号

---

> ##### 8、fontFamily\(String\)
>
> 文本字体

---

> ##### 9、start\(Array or Function\)
>
> 文本坐标位置



