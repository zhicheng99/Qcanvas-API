序号|名称|说明
---|---|---
1|~~animationFrame~~|~~requestAnimationFrame方法重写（兼容各类浏览器）~~已废弃 现统一使用window.requestNextAnimationFrame方法（核心库中的方法 外部调用一般用不到）
2|start|启动方法（核心库中的方法 外部调用一般用不到）
3|clear|清除画布（核心库中的方法 外部调用一般用不到）
4|extend|对象属性的重置方法（核心库中的方法 外部调用一般用不到）
5|paint|绘制元素的方法（核心库中的方法 外部调用一般用不到）
6|pushElements|元素生成唯一Id并放到elements数组中 （核心库中的方法 外部调用一般用不到）
7|getEleById|通过Id获取到元素对象
8|load|加载图片资源方法(建议使用新的loadImgSource方法)
9|getSourceByName|通过名称得到图片资源对象
10|getEleById|通过Id得到元素对象
11|removeEle|删除元素对象
12|getIndexById|通过Id得到元素在elements数组中的索引
13|lower|把元素降低一个层级 (参数为元素对象)
14|lowerToBottom|把元素层级置底(参数为元素对象)
15|raise|把元素提高一个层级(参数为元素对象)
16|raiseToTop|把元素层级置顶(参数为元素对象)
17|destroy|清除画布所有元素
18|loadImgSource|加载图片资源方法




> ##### 1、~~requestAnimationFrame~~
~~一是把各浏览器前缀进行统一，二是在浏览器不支持requestAnimationFrame方法时将其指向setTimeout方法。~~
已废弃 现统一使用window.requestNextAnimationFrame方法


***
> ##### 2、start
启动方法，框架的启动入口。
this.start();

***
> ##### 3、clear
清除画布
this.clear();

***
> ##### 4、extend
对象属性的重置方法

> ```
Qcanvas.prototype.extend = function(o,n){
	for(var i in n){
		(i != 'TYPE') && (o[i] = n[i]);		
	}
	this.pushElements(o);
}
o:默认对象，n:要创建的对象
> ```

***
> ##### 5、paint
循环elements元素数组，根据每个对象的TYPE类型 分别使用不同绘制方法将对象绘制到画布上 

***
> ##### 6、pushElements
元素生成唯一Id并放到elements数组中 

***
> ##### 7、getEleById
通过Id获取到元素对象

***
> ##### 8、load
加载图片资源方法 
接收参数（sourceObj,callback）
sourceObj：资源对象 例{"a":"http://www.abc.com/a.jpg"}
callback：资源加载完成回调函数

***
> ##### 9、getSourceByName
通过名称得到图片资源对象
接收参数类型 String

> ##### 18、loadImgSource
> 加载图片资源方法
> 接收参数（url） 
> url:资源地址（可以为字符串或数据）['http://www.abc.com/a.jpg']或'http://www.abc.com/a.jpg'
> 该方法返回的是一个类Promise对象  可以直接用.then 编写下一步逻辑