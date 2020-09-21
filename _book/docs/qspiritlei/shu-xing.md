| 序号 | 名称 | 类型 | 是否必需（创建对象） | 说明 |
| --- | --- | --- | --- | --- |
| 1 | qspiritVersion | String | 否（自动生成） | Qimg类版本号 |
| 2 | qcanvas | Object | 否（自动生成） | Qcanvas类实例 |
| 3 | img | Object/String | 是 | 图片对象或图片地址 |
| 4 | row | Number | 是 | 序列帧图片分为多少行 |
| 5 | column | Number | 是 | 序列帧图片分为多少列 |
| 6 | framesIndex | Array | 否 | 初始的位置 格式\[行,列\] |
| 7 | frames | Array | 否 | 二维的数组 对应序列帧图片的坐标格子 |
| 8 | tStart | Array | 是 | 画布目标位置坐标 |
| 9 | tWidth | Number | 是 | 以画布目标位置开始的宽度 |
| 10 | tHeight | Number | 是 | 以画布目标位置开始的高度 |
| 11 | isLoop | Boole | 否 | 是否循环播放 |
| 12 | during | Number | 是 | 一个序列播放完成需要的时间 单位\(秒\) |
| 13 | drag | String/Boolean | 否 | 是否可拖动（true:可拖动【默认】，false:不可拖动，'vertical':只可竖向拖动，'Horizontal':可能横向拖动） |
| 14 | pointerEvent | String | 否 | 是否响应事件（默认'auto':响应，'none':不响应） |
| 15 | mousedown | Fun | 否 | 事件 |
| 16 | mousemove | Fun | 否 | 事件 |
| 17 | mouseup | Fun | 否 | 事件 |
| 18 | mouseout | Fun | 否 | 事件 |
| 19 | touchstart | Fun | 否 | 事件 |
| 20 | touchmove | Fun | 否 | 事件 |
| 21 | touchend | Fun | 否 | 事件 |
| 22 | degree | Number | 否 | 旋转角度（-360~360） |
| 23 | mouseenter | Fun | 否 | 事件 |






