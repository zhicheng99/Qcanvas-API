##### 创建img对象

```
var img;
qcanvas.load({
    "a":"
http://sandbox.runjs.cn/uploads/rs/475/t0qpfflr/mb.png
",
    "b":"
http://sandbox.runjs.cn/uploads/rs/475/t0qpfflr/hand.png
"
},function(){
    var b = qcanvas.getSourceByName("b");
    console.log(b.height);
    img = qcanvas.qimg.img({
        img:b,
        sStart:[0,0],
        sWidth:b.width,
        sHeight:b.height,
        size:"cover",
        tStart:[350,0],
        tWidth:80,
        tHeight:70,
});
});
```

或

```
qcanvas.qimg.img({
img:'img/img.png',
sStart:[0,0],
tStart:[200,0],
tWidth:50,
tHeight:120,
degree:30,
mousemove:function(position){
console.log(position);
}
});
```

{% codeeditor   src='./example/img.html', height="800",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}

