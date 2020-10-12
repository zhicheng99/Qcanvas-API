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
    mouseenter:function(){},
    delayRender:true
}
);
```

> 注意：
> delayRender属性的配置
> 如果大多数元素只是静态的  建议开启 可以增加渲染效率
> 如果大多数元素是动画 不建议开启 因为开启后可能有卡顿

{% codeeditor   src='./example/init.html', height="500px",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}

