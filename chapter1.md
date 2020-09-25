##### 构造函数初始化 new Qcanvas\(\[画布Id,宽,高\]\)

```
方法一、
var qcanvas = new Qcanvas(["qcanvas",500,300]);
方法二、增加了事件的配置
var qcanvas = new Qcanvas(
{
     id:"qcanvas",
     width:500,
     height:300,
    mousedown:function(){},
    mousemove:function(){},
    mouseup:function(){},
    mouseout:function(){}
    mouseenter:function(){}
}
);
```

{% codeeditor   src='./example/init.html', height="800",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}

