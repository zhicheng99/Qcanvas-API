序号|名称|类型|是否必需（创建对象）| 说明| 
---|---|---|---|---|---
1|qcanvasVersion|String|否(自动生成)|Qcanvas类版本号| 
2|context|Object|否(自动生成)|画布绘图上下文对象| 
3|stage|Object|否(自动生成)|抽象出来的舞台对象| 
4|elements|Array|否(自动生成)|元素数组| 
5|group|Object|否(自动生成)|分组对象| 
6|qline|Object|否(自动生成)|Qline类的实例| 
7|qtext|Object|否(自动生成)|Qtext类的实例| 
8|qrect|Object|否(自动生成)|Qrect类的实例| 
9|delayRender|Boolean|否(自动生成)|是否开启延时渲染| 
10|qarc|Object|否(自动生成)|Qarc类的实例| 
11|qpolygon|Object|否(自动生成)|Qpolygon类的实例| 
12|qanimation|Object|否(自动生成)|Qanimation类的实例| 
13|qimg|Object|否(自动生成)|Qimg类的实例| 
14|qspirit|Object|否(自动生成)|Qspirit类的实例| 
15|qshape|Object|否(自动生成)|Qshape类的实例| 
16|qlayer|Object|否(自动生成)|Qlayer类的实例| 
17|qgroup|Object|否(自动生成)|Qgroup类的实例| 
18|qevent|Object|否(自动生成)|Qevent类的实例| 
19|id|String|是|canvas元素id| 
20|width|Number|是|要渲染的宽度| 
21|height|Number|是|要渲染的高度| 
22|mouseenter|Fun|否|事件| 
23|mousemove|Fun|否|事件| 
24|mouseup|Fun|否|事件| 
25|mouseout|Fun|否|事件| 
26|mousedown|Fun|否|事件| 


> ##### 1、qcanvasVersion(String)
主类的版本号
this.qcanvasVersion = '1.0';

***
> ##### 2、 context(Object)
画布绘图上下文对象
this.context = c_obj.getContext('2d');

***
> ##### 3、stage(Object)
抽象的舞台对象
this.stage = {
		"id":c_p[0],
		"width":c_p[1],
		"height":c_p[2]
	};

***
> ##### 4、elements(Array)
元素数组
this.elements = [];
按z-index属性由小到大排序

***
> ##### 5、group(Object)
分组对象（元素属于哪个组）
this.group = {};

***
> ##### 6、qline(Object)
Qline类的实例
this.qline = new Qline(this);

***
> ##### 7、qtext(Object)
Qtext类的实例
this.qtext = new Qtext(this);

***
> ##### 8、qrect(Object)
Qrect类的实例
this.qrect = new Qrect(this);

***

> 9、delayRender（默认为false）是否开始延时渲染
> 如果大多数元素只是静态的  建议开启 可以增加渲染效率
> 如果大多数元素是动画 不建议开启 因为开启后可能有卡顿

