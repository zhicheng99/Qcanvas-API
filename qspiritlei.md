##### 创建spirit对象

```
qcanvas.load({			
				"person":"img/spirit1.png",
			},function(){
				
					var spiritSource = qcanvas.getSourceByName("person"); 

					qcanvas.qspirit.spirit({
						img:spiritSource,
						row:1,
						column:8,
						framesIndex:[0,0],
						tStart:[0,120],
						tWidth:40,
						tHeight:64,
						isLoop:true,
						during:1,
						degree:30,
						mouseup:function(){
							console.log(this);
							console.log('触发mouseup事件');
						}
					})
						
							
			})
			```
			或
			
			```
			qcanvas.qspirit.spirit({ 
			img:'img/spirit1.png',
			row:1,
			column:8,
			framesIndex:[0,0],
			tStart:[0,120],
			tWidth:40,
			tHeight:64,
			isLoop:true,
			during:1,
			mouseup:function(){
				console.log(this);
				console.log('触发mouseup事件');
			}
		}) 
			```



