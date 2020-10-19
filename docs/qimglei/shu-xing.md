| 序号 | 名称 | 类型 | 是否必需（创建对象） | 说明 |
| --- | --- | --- | --- | --- |
| 1 | qimgVersion | String | 否（自动生成） | Qimg类版本号 |
| 2 | qcanvas | Object | 否（自动生成） | Qcanvas类实例 |
| 3 | img | Object/String | 是 | 图片对象或图片地址 |
| 4 | size | String | 否 | 图片渲杂方式 （现只有一种 cover 以后再增加） |
| 5 | sStart | Array | 是 | 源图片开始剪切的起始坐标 |
| 6 | sWidth | Number | 是 | 源图片开始剪切的宽度 |
| 7 | sHeight | Number | 是 | 源图片开始剪切的高度 |
| 8 | tStart | Array | 是 | 画布目标位置起始坐标 |
| 9 | tWidth | Number | 是 | 画布目标位置宽度 |
| 10 | tHeight | Number | 是 | 画布目标位置高度 |
| 11 | drag | String/Boolean | 否 | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':可能横向拖动） |
| 12 | pointerEvent | String | 否 | 是否响应事件（默认'auto':响应，'none':不响应） |
| 13 | mousedown | Fun | 否 | 事件 |
| 14 | mousemove | Fun | 否 | 事件 |
| 15 | mouseup | Fun | 否 | 事件 |
| 16 | mouseout | Fun | 否 | 事件 |
| 17 | touchstart | Fun | 否 | 事件 |
| 18 | touchmove | Fun | 否 | 事件 |
| 19 | touchend | Fun | 否 | 事件 |
| 20 | degree | Number | 否 | 旋转角度（-360~360） |
| 21 | mouseenter | Fun | 否 | 事件 |
| 22 | dblclick | Fun | 否 | 事件 |




size属性 一旦不为空 就会重新计算 sStart sWidth sHeight这三个属性

