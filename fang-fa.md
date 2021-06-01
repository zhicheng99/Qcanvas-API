注：方法是根据对象的属性自动生成的，给对象赋加自定义的初始属性，也会自动添加相应的方法  
格式为 set+属性名称（首字母会自动转成大写）

| 序号 | 名称 | 参数类型 | 说明 |
| :--- | :--- | :--- | :--- |
| 1 | push | Object | 添加元素到Qlayer实例对象中\(多个元素对象以逗号隔开即可\) |
| 2 | getEleById | String | 通过Id获取到元素对象 |
| 3 | removeEle | String | 删除元素对象 |
| 4 | getIndexById | String | 通过Id得到元素在elements数组中的索引 |
| 5 | lower | Object | 把元素降低一个层级 \(参数为元素对象\) |
| 6 | lowerToBottom | Object | 把元素层级置底\(参数为元素对象\) |
| 7 | raise | Object | 把元素提高一个层级\(参数为元素对象\) |
| 8 | raiseToTop | Object | 把元素层级置顶\(参数为元素对象\) |
| 9 | destroy | 无 | 清空layer.elements |

> ##### 1、push
>
> var layer = qcanvas.qlayer.layer\(\);  
> var text = qcanvas.qtext.text\({  
>         start:\[100,100\],  
>         text:'我是来自layer容器里的文字',  
>         color:'red'  
>     }\)  
> layer.push\(text\);  //添加文本对象到layer中



