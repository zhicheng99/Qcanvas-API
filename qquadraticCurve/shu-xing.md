| 序号 | 名称                   | 类型           | 是否必需（创建对象） | 说明                                                         |
| ---- | ---------------------- | -------------- | -------------------- | ------------------------------------------------------------ |
| 1    | qquadraticCurveVersion | String         | 否（自动生成）       | Qline类版本号                                                |
| 2    | qcanvas                | Object         | 否（自动生成）       | 主类Qcanvas的实例                                            |
| 3    | TYPE                   | String         | 否（自动生成）       | 线段类型标记 'quadraticCurve' （注：不允许修改）             |
| 4    | start                  | Array Or Fun   | 否                   | 线段的开始坐标                                               |
| 5    | handler                | Array Or Fun   | 否                   | 控制点坐标                                                   |
| 7    | end                    | Array Or Fun   | 否                   | 线段的结束坐标                                               |
| 7    | color                  | String         | 否                   | 线的颜色                                                     |
| 8    | like                   | String         | 否                   | 线的样式                                                     |
| 9    | width                  | Number         | 否                   | 线的粗细                                                     |
| 10   | withText               | String         | 否                   | 线带着的文本                                                 |
| 11   | withTextAlign          | String         | 否                   | 线带着的文本的横向位置 \[left center\(默认\) right\]         |
| 12   | drag                   | String/Boolean | 否                   | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':只可横向拖动） |
| 13   | pointerEvent           | String         | 否                   | 是否响应事件（默认'auto':响应，'none':不响应）               |
| 14   | mousedown              | Fun            | 否                   | 事件                                                         |
| 15   | mousemove              | Fun            | 否                   | 事件                                                         |
| 16   | mouseup                | Fun            | 否                   | 事件                                                         |
| 17   | mouseout               | Fun            | 否                   | 事件                                                         |
| 18   | touchstart             | Fun            | 否                   | 事件                                                         |
| 19   | touchmove              | Fun            | 否                   | 事件                                                         |
| 20   | touchend               | Fun            | 否                   | 事件                                                         |
| 21   | mouseenter             | Fun            | 否                   | 事件                                                         |
| 22   | withTextId             | Number         | 否                   | 通过withText生成的文本对象id (如果配置了withText，会自动生成该属性) |
| 23   | dblclick               | Fun            | 否                   | 事件                                                         |
| 24   | handlerShow            | Boolean        | 否                   | 是否显示控制点                                               |

> ##### 1、qquadraticCurveVersion\(String\)
>
> QquadraticCurve类的版本号 

---

> ##### 2、 qcanvas\(Object\) 
>

---

> ##### 3、 TYPE\(String\)
>
> 元素的类型 线为quadraticCurve, 不可更改  
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



