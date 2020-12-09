##### 创建三次贝塞尔曲线bezierCurve对象

```
qcanvas.qbezierCurve.bezierCurve({
		start:[20,20],
		handler1:[50,80],
		handler2:[100,20],
		end:[200,20],
		width:1,
		like:'<-->',
		color:'red',
		drag:true,
		withText:'我是个三次曲线',
		handlerShow:true
	})
```

{% codeeditor   src='./example/qbezierCurve.html', height="500px",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}

