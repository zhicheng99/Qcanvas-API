var group = qcanvas.qgroup.group\(\)

分组group实例是抽象出来的元素 只在逻辑上把一些元素集合到一块，  
本质上是排了一下顺序 只是把一组元素放一块了

如group是第2个创建的元素 那么只要是push到group里的元素依次往后排2,3,4.....  别的元素一并往后移动位置

元素还是一直重绘在主canvas上

{% codeeditor   src='./example/group.html', height="800",maxLines="500", readOnly='true', theme='github' %}

{% endcodeeditor %}