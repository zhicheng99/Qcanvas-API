| 序号 | 名称 | 类型 | 是否必需（创建对象） | 说明 |
| --- | --- | --- | --- | --- |
| 1 | qlineVersion | String | 否（自动生成） | Qline类版本号 |
| 2 | qcanvas | Object | 否（自动生成） | 主类Qcanvas的实例 |
| 3 | TYPE | String | 否（自动生成） | 线段类型标记 'line' （注：不允许修改） |
| 4 | start | Array Or Fun | 否 | 线段的开始坐标 |
| 5 | end | Array Or Fun | 否 | 线段的结束坐标 |
| 6 | color | String | 否 | 线的颜色 |
| 7 | like | String | 否 | 线的样式 |
| 8 | width | Number | 否 | 线的粗细 |
| 9 | withText | String | 否 | 线带着的文本 |
| 10 | withTextAlign | String | 否 | 线带着的文本的横向位置 \[left center\(默认\) right\] |
| 11 | drag | String/Boolean | 否 | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':只可横向拖动） |
| 12 | pointerEvent | String | 否 | 是否响应事件（默认'auto':响应，'none':不响应） |
| 13 | mousedown | Fun | 否 | 事件 |
| 14 | mousemove | Fun | 否 | 事件 |
| 15 | mouseup | Fun | 否 | 事件 |
| 16 | mouseout | Fun | 否 | 事件 |
| 17 | touchstart | Fun | 否 | 事件 |
| 18 | touchmove | Fun | 否 | 事件 |
| 19 | touchend | Fun | 否 | 事件 |
| 20 | mouseenter | Fun | 否 | 事件 |
| 21 | withTextId | Number | 否 | 通过withText生成的文本对象id (如果配置了withText，会自动生成该属性，否则没有不存在该属性) |

> ##### 1、qlineVersion\(String\)
>
> Qline类的版本号  
> function Qline\(qcanvas\){  
>     **this.qlineVersion = '1.0';**  
>     this.qcanvas = qcanvas;  
> }

---

> ##### 2、 qcanvas\(Object\)
>
> 主类Qcanvas的实例  
> function Qline\(qcanvas\){  
>     this.qlineVersion = '1.0';  
>     **this.qcanvas = qcanvas;**  
> }

---

> ##### 3、 TYPE\(String\)
>
> 元素的类型 线为line, 不可更改  
> 为了画元素时作辨别

---

> ##### 4、 start\(Array Or Function\)
>
> 线段的开始坐标

---

> ##### 5、 end\(Array Or Function\)
>
> 线段的结束坐标

---

> ##### 6、 color\(String\)
>
> 线段的颜色

---

> ##### 7、 like\(String\)
>
> 线的样式  
> 目前支持以下四种：  
> like:'-' //实线  
> like:'-&gt;' //实线带箭头  
> like:'--' //虚线  
> like:'--&gt;' //虚线带箭头  
> like:'&lt;-&gt;' //实线双向箭头  
> like:'&lt;--&gt;' //虚线双向箭头

---

> ##### 8、 width\(Number\)
>
> 线段的粗细

---

> ##### 9、 withText\(String\)
>
> 线带着的文本

---

> ##### 10、 withTextAlign\(String\)
>
> 线带着的文本的横向位置 \[left center\(默认\) right\]



