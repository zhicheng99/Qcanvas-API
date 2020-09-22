序号|名称|类型| 说明
---|---|---|---
1|qcanvasVersion|String|Qcanvas类版本号
2|context|Object|画布绘图上下文对象
3|stage|Object|抽象出来的舞台对象
4|elements|Array|元素数组
5|group|Object|分组对象
6|qline|Object|Qline类的实例
7|qtext|Object|Qtext类的实例
8|qrect|Object|Qrect类的实例


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

