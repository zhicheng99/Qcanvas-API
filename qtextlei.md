##### 创建text实例

```
var textfps = qcanvas.qtext.text({
    start:[20,20],
        text:function(){ return qcanvas.currFps},
    color:'blue',
    fontSize:'20px'
})
```

{% codeeditor   src='./example/text.html', height="500px",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}

