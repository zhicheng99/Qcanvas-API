var layer = qcanvas.qlayer.layer\(\)

Qlayer元素类

> 实质上是一个**抽象**的元素容器类 为了容纳其它元素。（宽高和主画布一样）  
> 实现的原理：Qlayer实例完全继承于Qcanvas类, 所以Qlayer相当于重新实现一次Qcanvas的逻辑  只是在每次requestNextAnimationFrame时，把临时画布上的内容重新画到了主画布上

1、当我们不使用Qlayer时 元素直接画在主画布上；  
2、当使用Qlayer时 先创建一个临时的canvas画布 把指定要放到该容器内的元素先画这个临时canvas上，最后在requestNextAnimationFrame的下一个循环时再把这个画布画到主画布上  当然临时canvas也在requestNextAnimationFrame控制下不停的重绘 所以现在框架实现的这些元素都可以指定到一个Qlayer对象上
3、使用Qlayer元素的好处：可以一次性控制一批元素的显示、隐藏、删除、层级关系等  
4、删除Qlayer元素 会同时删除它所容纳的所有元素  
5、**注：** 添加到同一个layer实例中的多元素 它们之间的层级关系是以该layer实例为基准的 所以Qcanvas的以下方法 对Qlayer元素容器内的元素无效 如果需要调整层级关系 需要调用Qlayer的下列方法
6、注：当实例化Qline 配置了withText后 如果把它添加到一个layer中，那么通过withText属性生成的Qtext实例也会一并添加到该layer中

| 方法          | 介绍                                 |
| ------------- | ------------------------------------ |
| lower         | 把元素降低一个层级（参数为元素对象） |
| lowerToBottom | 把元素置底（参数为元素对象）         |
| raise         | 把元素提高一个层级（参数是元素对象） |
| raiseToTop    | 把元素置顶（参数为元素对象）         |

{% codeeditor   src='./example/layer.html', height="500px",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}