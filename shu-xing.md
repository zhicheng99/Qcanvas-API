Qlayer元素类 
>实质上是一个**抽象**的元素容器类 为了容纳其它元素。（宽高和主画布一样）
1、当我们不使用Qlayer时 元素直接画在主画布上； 
2、当使用Qlayer时 先创建一个临时的canvas画布 把指定要放到该容器内的元素先画这个临时canvas上，最后在requestNextAnimationFrame的下一个循环时再把这个画布画到主画布上  当然临时canvas也在requestNextAnimationFrame控制下不停的重绘 所以现在框架实现的这些元素都可以指定到一个Qlayer对象上 
3、使用Qlayer元素的好处：可以一次性控制一批元素的显示、隐藏、删除、层级关系等
4、删除Qlayer元素 会同时删除它所容纳的所有元素

