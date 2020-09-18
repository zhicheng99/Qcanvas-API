/*画线类*/	
function Qline(qcanvas){
	this.qlineVersion = '1.0';
	this.qcanvas = qcanvas;
	console.log(this);
	

	
}	

/*
四种形式的线 
参数对象
{
TYPE:'line',
start:[0,0],  //开始坐标
end:[50,50],  //结束坐标
color:'red',  //颜色
like:'-',     //画出来的样子 [-][->][--][-->]
width:1,			//线条宽度
withText:'text', //带着的文本
withTextAlign:'center'  //文本的横向位置 [left center(默认) right]
}
*/
Qline.prototype.line = function(options){
	
	var OPTIONS = {
		TYPE:'line',
		
		color:'#000',  //颜色
		like:'-',     //画出来的样子 [-][->][--][-->]
		width:1,
		start:[0,0],
		end:[50,50],
		//withText:'text', //带着的文本
		//withTextAlign:'center'  //文本的横向位置 [left center(默认) right]
	}
	
	
			
						
	this.qcanvas.extend(OPTIONS,options);		
	this.qcanvas.appendSetFun(OPTIONS);
	
	//分离文字
	if(typeof OPTIONS.withText !='' && OPTIONS.withText!=''){
		
		this.splitText(OPTIONS);
			
	}
	
	return OPTIONS;
}

Qline.prototype.getMiddleCoordinates = function(obj){
	
	return [
		(obj.start[0] < obj.end[0] ? obj.start[0]:obj.end[0])+Math.abs(obj.start[0]-obj.end[0]) * 0.5,
		(obj.start[1] < obj.end[1] ? obj.start[1]:obj.end[1])+Math.abs(obj.start[1]-obj.end[1]) * 0.5,
	];
	
}
		
//分离携带的文字	
Qline.prototype.splitText = function(obj){
	

	var _this = this;
	this.qcanvas.qtext.text({
			TYPE:'text',
			text:obj.withText,
			color:obj.color,
			withTextAlign:obj.withTextAlign?obj.withTextAlign:'center',
			start:function(){return _this.getMiddleCoordinates(obj)}
	});
		
}	
	
Qline.prototype.paintLine  = function(obj){
	this.qcanvas.qanimation.createAnimation(obj);
	switch(obj.like)
	{
		case '-':
			this.qcanvas.context.strokeStyle = obj.color;
			this.qcanvas.context.beginPath();
			this.qcanvas.context.lineWidth=obj.width;
			//if(obj.like == '--'){
			//	this.qcanvas.context.setLineDash([2, 4]);
			//}
			
			this.qcanvas.context.moveTo(obj.start[0],obj.start[1]);
			this.qcanvas.context.lineTo(obj.end[0],obj.end[1]);
			this.qcanvas.context.stroke();
			
			
			
			break;
		case '->':
			this.qcanvas.context.strokeStyle = obj.color;
			this.qcanvas.context.beginPath();
			this.qcanvas.context.lineWidth=obj.width;
			//if(obj.like == '--'){
			//	this.qcanvas.context.setLineDash([2, 4]);
			//}
			
			this.qcanvas.context.moveTo(obj.start[0],obj.start[1]);
			this.qcanvas.context.lineTo(obj.end[0],obj.end[1]);
			this.qcanvas.context.stroke();
			
			//分解出两条实线 生成箭头效果
			if(this.lineIsChange(obj)){
					this.appendArrow(obj);
			}

			//画箭头			
			if(typeof obj.arrow !='undefined'){ 
					arguments.callee.call(this,obj.arrow[0]);
					arguments.callee.call(this,obj.arrow[1]);
			}
			
			break;

		case '--':
			this.paintDashLine(obj);
			break;
		
		case '-->':
			this.paintDashLine(obj);

			
			//画箭头
			if(typeof obj.arrow !='undefined'){ 
					arguments.callee.call(this,obj.arrow[0]);
					arguments.callee.call(this,obj.arrow[1]);
			}
			
			

			break;
	}	
	
}	

//附加箭头对象
Qline.prototype.appendArrow = function(obj){
				arrowObj = this._calcH({
				
				},{
					'x':obj.start[0],
					'y':obj.start[1],
				},{
					'x':obj.end[0],
					'y':obj.end[1],
				});
	
			obj.arrow = [
							{
									like:'-',
									start:[arrowObj.h1.x,arrowObj.h1.y],
									end:[obj.end[0],obj.end[1]]
							},
							{
									like:'-',
									start:[arrowObj.h2.x,arrowObj.h2.y],
									end:[obj.end[0],obj.end[1]]
							},	
					]
}	
	
	
 //计算头部坐标
Qline.prototype._calcH=function(a,sp,ep){
	 var theta=Math.atan((ep.x-sp.x)/(ep.y-sp.y));
	 var cep=this._scrollXOY(ep,-theta);
	 var csp=this._scrollXOY(sp,-theta);
	 var ch1={x:0,y:0};
	 var ch2={x:0,y:0};
	 var l=cep.y-csp.y;
	 ch1.x=cep.x+l*(a.sharp||0.025);
	 ch1.y=cep.y-l*(a.size||0.05);
	 ch2.x=cep.x-l*(a.sharp||0.025);
	 ch2.y=cep.y-l*(a.size||0.05);
	 var h1=this._scrollXOY(ch1,theta);
	 var h2=this._scrollXOY(ch2,theta);
	 return {
		h1:h1,
		h2:h2
		};
 };
 //旋转坐标
Qline.prototype._scrollXOY=function(p,theta){
	 return {
		x:p.x*Math.cos(theta)+p.y*Math.sin(theta),
		y:p.y*Math.cos(theta)-p.x*Math.sin(theta)
	 };
 };
	
	

Qline.prototype.getBeveling = function(x,y){  
    return Math.sqrt(Math.pow(x,2)+Math.pow(y,2));  
}  	


//起止点是否有变化	
Qline.prototype.lineIsChange = function(obj){
	
	//当前的起止点和原来的做比较
	
	if(typeof obj.oldStart =='undefined'){
			obj.oldStart = JSON.parse(JSON.stringify(obj.start));
			obj.oldEnd = JSON.parse(JSON.stringify(obj.end));
			return true;
	}else{
		
		if(obj.start[0]==obj.oldStart[0] &&
			 obj.start[1]==obj.oldStart[1] &&
			 obj.end[0]==obj.oldEnd[0] &&
			 obj.end[1]==obj.oldEnd[1]
			){
			
			return false;
		}else{
			obj.oldStart = JSON.parse(JSON.stringify(obj.start));
			obj.oldEnd = JSON.parse(JSON.stringify(obj.end));
			return true;
		}
		
		
	}
}	
	
//画虚线	
Qline.prototype.paintDashLine = function(obj){
	
			this.qcanvas.context.strokeStyle = obj.color;
			this.qcanvas.context.beginPath();
			this.qcanvas.context.lineWidth=obj.width;
	
			if(this.lineIsChange(obj)){
				
					var dashLen = 2;  
					//得到斜边的总长度  
					var beveling = this.getBeveling(obj.end[0]-obj.start[0],obj.end[0]-obj.start[1]);  
					//计算有多少个线段  
					var num = Math.floor(beveling/dashLen);  
			
					obj.dashPoint = [];
						
					for(var i = 0 ; i < num; i++)  
					{  
						obj.dashPoint.push([
							obj.start[0]+(obj.end[0]-obj.start[0])/num*i,
							obj.start[1]+(obj.end[1]-obj.start[1])/num*i
						])  
					}  
				
				if(obj.like=='-->'){
						this.appendArrow(obj);
				}
				
					
				
				
			}else{
				
				for(var i = 0 ; i < obj.dashPoint.length; i++){
					  
						this.qcanvas.context[i%2 == 0 ? 'moveTo' : 'lineTo'](obj.dashPoint[i][0],obj.dashPoint[i][1]);  
				} 
			
			}
			
			
	
			this.qcanvas.context.stroke();  
}	
	
	

	
	

	
/*文字类--------------------------------------------------------*/
function Qtext(qcanvas){
	this.qtextVersion = '1.0';
	this.qcanvas = qcanvas;
	
	
}	

Qtext.prototype.text = function(options){
		var OPTIONS = {
			TYPE:'text',
			text:'Qcanvas Text',
			color:'red',
			textAlign:'center',
			textBaseline:'middle',
			fontSize:"12px",
			fontFamily:'Microsoft YaHei',
			start:[],
			
		}
			
	this.qcanvas.extend(OPTIONS,options);
	this.qcanvas.appendSetFun(OPTIONS);
	
	return OPTIONS;
}

Qtext.prototype.paintText = function(obj){
		//设置字体颜色
    this.qcanvas.context.strokeStyle = obj.color;
    //从坐标点(50,50)开始绘制文字
		
		
		var start = this.qcanvas.isFun(obj.start)?obj.start():obj.start;
		this.qcanvas.context.textBaseline = obj.textBaseline;
		this.qcanvas.context.font = obj.fontSize + ' '+obj.fontFamily;
		this.qcanvas.context.textAlign = obj.withTextAlign;
    this.qcanvas.context.strokeText(this.qcanvas.isFun(obj.text)?obj.text():obj.text,  start[0],  start[1]);
		
		this.qcanvas.context.textAlign ='center';
}


/*矩形类-----------------------------------------------------*/
function Qrect(qcanvas){
	this.qrectVersion = '1.0';
	this.qcanvas = qcanvas;

}

Qrect.prototype.rect = function(options){
	var OPTIONS = {
			TYPE:'rect',
			lineWidth:1,
			start:[0,0],
			width:100,
			height:50,
			borderColor:'#000',
			fillColor:'',
		
			
		}
			
	this.qcanvas.extend(OPTIONS,options);
	this.qcanvas.appendSetFun(OPTIONS);
	
	return OPTIONS;
}

Qrect.prototype.paintRect = function(obj){
	
		this.qcanvas.context.beginPath();
		this.qcanvas.context.lineWidth=obj.lineWidth;
		this.qcanvas.context.strokeStyle=obj.borderColor;
	
		
	
		this.qcanvas.context.rect(obj.start[0],obj.start[1],obj.width,obj.height);
	
	
		this.qcanvas.context.stroke();
	
	
		(obj.fillColor!='') && (this.qcanvas.context.fillStyle = obj.fillColor) && this.qcanvas.context.fill();
}
	

/*圆类--------------------*/
function Qarc(qcanvas){
	this.qarcVersion = '1.0';
	this.qcanvas = qcanvas;
  this.unit = Math.PI / 180;
}

Qarc.prototype.arc = function(options){
	var OPTIONS = {
			TYPE:'arc',
			lineWidth:1,
			borderColor:'#000',
			fillColor:'red',
			start:[0,0],
			r:20,
			sAngle:0,
			eAngle:0,
			counterclockwise:false
		}
			
	this.qcanvas.extend(OPTIONS,options);
	this.qcanvas.appendSetFun(OPTIONS);
	
	return OPTIONS;
}	
	
Qarc.prototype.paintArc = function(obj){
	this.qcanvas.qanimation.createAnimation(obj);
	this.qcanvas.context.beginPath();
	this.qcanvas.context.lineWidth=obj.lineWidth;
	this.qcanvas.context.strokeStyle=obj.borderColor;
	this.qcanvas.context.arc(obj.start[0],obj.start[1],obj.r,obj.sAngle*this.unit,obj.eAngle*this.unit);
	this.qcanvas.context.stroke();
	
	(obj.fillColor!='') && (this.qcanvas.context.fillStyle = obj.fillColor) && this.qcanvas.context.fill();
	
}	
	
	
/*多边形类----------------*/
function Qpolygon(qcanvas){
	this.qpolygonVersion = '1.0';
	this.qcanvas = qcanvas;
}
Qpolygon.prototype.polygon = function(options){
	var OPTIONS = {
			TYPE:'polygon',
			lineWidth:1,
			borderColor:'#000',
			fillColor:'red',
			start:[0,0],
			r:20,
			num:4
		}
			
	this.qcanvas.extend(OPTIONS,options);
	this.qcanvas.appendSetFun(OPTIONS);
	
	return OPTIONS;
}	
	
	
Qpolygon.prototype.paintPolygon = function(obj){
	var ctx = this.qcanvas.context;
	
		var x = obj && obj.start[0] || 0;  //中心点x坐标
    var y = obj && obj.start[1] || 0;  //中心点y坐标
    var num = obj && obj.num || 3;   //图形边的个数
    var r = obj && obj.r || 100;   //图形的半径
    var width = obj && obj.lineWidth || 1;
    var strokeStyle = obj && obj.borderColor;
    var fillStyle = obj && obj.fillColor;
    //开始路径
    ctx.beginPath();
    var startX = x + r * Math.cos(2*Math.PI*0/num);
    var startY = y + r * Math.sin(2*Math.PI*0/num);
    ctx.moveTo(startX, startY);
    for(var i = 1; i <= num; i++) {
        var newX = x + r * Math.cos(2*Math.PI*i/num);
        var newY = y + r * Math.sin(2*Math.PI*i/num);
        ctx.lineTo(newX, newY);
    }
    ctx.closePath();
    //路径闭合
    if(strokeStyle) {
        ctx.strokeStyle = strokeStyle;
        ctx.lineWidth = width;
        ctx.lineJoin = 'round';
        ctx.stroke();
    }
    if(fillStyle) {
        ctx.fillStyle = fillStyle;
        ctx.fill();
    }
	
}		

/*动画类----------------*/
function Qanimation(qcanvas){
	this.qanimationVersion = '1.0';
	this.qcanvas = qcanvas;
}	

Qanimation.prototype.animate = function(aim,startStyle,endStyle,during,isLoop){
	
	//要求 startStyle对象和endStyle对象属性必须是一样的
	//序列帧对象(属性=>值)  
	var frames = {};
	var framesCount = this.qcanvas.fps * during;
	
	
	
	for(var i in startStyle){
			
			//如果是属性的值是数组的 生成成对的数组序列 用于渲染动画
			if(this.qcanvas.isArr(startStyle[i])){
				frames[i] = [];
				
				var perArr = [];
				for(var j=0;j<startStyle[i].length;j++){
						perArr.push((endStyle[i][j] - startStyle[i][j])/framesCount);
				}
				
				
				
				for(var t=0;t<framesCount;t++){
					var temp = [];
					for(var p=0;p<perArr.length;p++){
							temp.push(startStyle[i][p]+ t*perArr[p]);  //暂时都是线性变化 
					}
					
					frames[i].push(temp);
				}
				
			}
			
			//属性的值是数字的
			if(this.qcanvas.isNum(startStyle[i])){
				frames[i] = [];
				var per = (endStyle[i] - startStyle[i])/framesCount;
				
				for(var t=0;t<framesCount;t++){
					frames[i].push(startStyle[i]+ t*per);
				}
				
			}
		
		
		
		
	}
	
	aim.animation = {
		'framesIndex':0,
		'framesCount':framesCount,
		'during':during,
		'frames':frames,
		'isLoop':isLoop?isLoop:false,
	}
	
}
//通过对象的animation属性中序列对象frames 改变相应的属性值
//使渲染过程中生成动画		
Qanimation.prototype.createAnimation = function(obj){
		
		if(typeof obj.animation !='undefined' && obj.animation && obj.animation.frames){
				
				var framesIndex = obj.animation.framesIndex;
				var framesCount = obj.animation.framesCount;
				var frames = obj.animation.frames;
				var isLoop = obj.animation.isLoop;
		
				obj.animation.step = typeof obj.animation.step !='undefined'?obj.animation.step:1;//控制方向  
				
				var step = obj.animation.step;
				
				obj.animation.framesIndex=obj.animation.framesIndex+step;
		
				obj.animation.framesIndex = obj.animation.framesIndex<=0?0:obj.animation.framesIndex;
		
				obj.animation.framesIndex = obj.animation.framesIndex>=framesCount?(framesCount-1):obj.animation.framesIndex;
				
				if(isLoop){
					if(obj.animation.framesIndex==(framesCount-1)){
						obj.animation.step = -1; //反方向运动回去		
					}
		
					
					if(obj.animation.framesIndex==0){
						obj.animation.step = 1; 		
					}
		
				}
		
				//console.log(framesIndex);
				
			
				for(var i in obj.animation.frames){
						obj[i] =  obj.animation.frames[i][framesIndex];
				}
				
		
		}
		
}	

	
/*画图片类*/
function Qimg(qcanvas){
	this.qimgVersion = '1.0';
	this.qcanvas = qcanvas;
}	

Qimg.prototype.sourcePosition = function(pic,w,h){
			
			//原图及目标区域的宽高比
			var sourceRate = pic.width/pic.height;
			var targetRate = w/h;
			var x,y,w,h;
			
			if(sourceRate>=targetRate){
					h = pic.height;
					w = targetRate*pic.height;
					y = 0;
					x = (pic.width - w)*0.5;
			}else{
					w = pic.width;
					h = pic.width/targetRate;
					x = 0;
					y = (pic.height - h)*0.5;
			
			}
			
	return {
		sStart:[x,y],
		sWidth:w,
		sHeight:h,
		sourceRate:sourceRate,
		targetRate:targetRate
	}
	
	
}

Qimg.prototype.img = function(options){
	var OPTIONS = {
			TYPE:'img',
			img:{},
			size:"",
			/*sStart:[0,0],
			sWidth:options.width,
			sHeight:options.height,
			tStart:[0,0],
			tWidth:options.width,
			tHeight:options.height,*/
		}
			
	this.qcanvas.extend(OPTIONS,options);
	this.qcanvas.appendSetFun(OPTIONS);
	
	
	if(OPTIONS.size!=''){
		
		//重新计算sStart sWidth sHeight
		//全覆盖目标区域 图像的某些部分也许无法显示在目标区域中
		if(OPTIONS.size =='cover'){ 
				delete OPTIONS.sStart;
			  delete OPTIONS.sWidth;
				delete OPTIONS.sHeight;
			  
				
				var sourceObj = this.sourcePosition(OPTIONS.img,OPTIONS.tWidth,OPTIONS.tHeight);
				console.log(sourceObj);
				
				OPTIONS.sStart = sourceObj.sStart;
				OPTIONS.sWidth = sourceObj.sWidth;
				OPTIONS.sHeight = sourceObj.sHeight;
			
			
			
		}
	
	
	}
	
	return OPTIONS;
}	
Qimg.prototype.paintImg = function(obj){
		
	this.qcanvas.context.drawImage(obj.img,obj.sStart[0],obj.sStart[1],obj.sWidth,obj.sHeight,obj.tStart[0],obj.tStart[1],obj.tWidth,obj.tHeight);
	
}	
	

/*
画布框架Qcanvas结构---------------------------------------------------------
*/
/*主类*/
/*
c_p:初始化canvas参数数组
*/	
function Qcanvas(c_p){
	
	var doc = document;
	if(c_p.length<3 ){
		console.log('Qcanvas 初始化参数不正确');
		return false;
	}
	
	var c_obj = doc.getElementById(c_p[0]);
	c_obj.width = c_p[1];
	c_obj.height = c_p[2];
	
	
	
	this.qcanvasVersion = '1.0';
	this.context = c_obj.getContext('2d');
	this.fps = 60;
	
	
	//舞台对象
	this.stage = {
		"id":c_p[0],
		"width":c_p[1],
		"height":c_p[2]
	};
	
	
	
	//元素数组 （按z-index由小到大排序）
	this.elements = [];
	
	//分组对象（元素属于哪个组）
	this.group = {};
	
	
	
	console.log('主类构造函数执行');
	
	
	this.qline = new Qline(this);
	this.qtext = new Qtext(this);
	this.qrect = new Qrect(this);
	this.qarc = new Qarc(this);
	this.qpolygon = new Qpolygon(this);
	this.qanimation = new Qanimation(this);
	this.qimg = new Qimg(this);
	
	
	this.animationFrame = this.requestNextAnimationFrame();
	
	
	//计算fps
	this.lastLoop = (new Date()).getMilliseconds();
	this.count = 1;
  this.currFps = 0;
	
	//启动
	this.start();
}

//根据elements数组 画所有元素
Qcanvas.prototype.paint = function(){
	
	for(var i = 0; i<this.elements.length; i++){
		var o = this.elements[i];
		
		switch (o.TYPE){
			case 'line':
				this.qline.paintLine(o);
				break;
			case 'text':
				this.qtext.paintText(o);
				break;
			case 'rect':
				this.qrect.paintRect(o);
				break;
			case 'arc':
				this.qarc.paintArc(o);
				break;	
			case 'polygon':
				this.qpolygon.paintPolygon(o);
				break;	
			case 'img':
				this.qimg.paintImg(o);
				break;		
		}
				
	}
}




//启动
Qcanvas.prototype.start = function(){
	//console.log('start');
	this.clear();
	this.paint();			
	//requestNextAnimationFrame.call(this,[arguments.callee]);
	
	var currentLoop = (new Date()).getMilliseconds();
    if (this.lastLoop > currentLoop) {
			this.currFps = this.count;
      this.count = 1;
    } else {
			this.count  += 1;	
    }
				
		this.lastLoop = currentLoop;		
				
	
	this.animationFrame(this.callback = this.start);			
}
	
Qcanvas.prototype.clear = function(){
		this.context.clearRect(0,0,this.stage.width,this.stage.height);
}	

		

//根据对象属性名称自动生成[set+属性名称]方法
Qcanvas.prototype.appendSetFun = function(o){
	
		var firstToUpperCase = function(s){
				var p = s.split('');
				p[0] = p[0].toUpperCase();
				
				return p.join('');
		}		
				
		for(var i in o){
			
				(i != 'TYPE') && 
				(i != 'id') && 
				(i != 'withText') && 
				(i != 'withTextAlign') && 
				(o['set'+firstToUpperCase(i)] = (function(index,obj){
					var p = index;
					return function(t){
						obj[p] = t;
					}
			})(i,o));
				
		}		
}

Qcanvas.prototype.extend = function(o,n){
	

				
	for(var i in n){
		
			(i != 'TYPE') && (o[i] = n[i]);
				
	}
				
		
	
	this.pushElements(o);
}
	
Qcanvas.prototype.pushElements = function(element){
	
	if(typeof element.id == 'undefined'){
		//自动生成一个唯一id
		element.id = parseInt(Math.random()*10000);
		this.elements.push(element);
	}
	
}

Qcanvas.prototype.getEleById = function(id){
	
	for(var i=0;i<this.elements.length;i++){
		if(this.elements[i].id == id){
				return this.elements[i];
				break;
		}	
	}
	
}	

//加载图片资源				
Qcanvas.prototype.load = function(sourceObj,callback){
	
	if(typeof this.source=='undefined'){
			this.source = {};
	}
	
	var _this = this;
	
	//先实现加载图片资源
	var imgArr = [];
	var num = 0;
	for(var i in sourceObj){
		
		
		img = new Image();
		imgArr.push(img);
		img.onload = function(){
			_this.source[this.alias] = this;
			
			num++;
			
			if(num==imgArr.length){
					callback();
			}
			
			
		};
		img.alias = i;
		img.src=sourceObj[i];
	}
	
}

Qcanvas.prototype.getSourceByName = function(name){
		
		return this.source[name];		
}				
				
				
				
				
				
				
				

	
Qcanvas.prototype.isFun = function(o){
	if(Object.prototype.toString.call(o)=='[object Function]'){
		return true;
	}else{
		return false;
	}
}
				
Qcanvas.prototype.isArr = function(o){
	if(Object.prototype.toString.call(o)=='[object Array]'){
		return true;
	}else{
		return false;
	}
}	
				
Qcanvas.prototype.isNum = function(o){
	if(Object.prototype.toString.call(o)=='[object Number]'){
		return true;
	}else{
		return false;
	}
}					
				
	
				
Qcanvas.prototype.requestNextAnimationFrame = function(){
        var originalWebkitMethod,
            wrapper = undefined,
            callback = undefined,
            geckoVersion = 0,
            userAgent = navigator.userAgent,
            index = 0,
            self = this;
        if(window.webkitRequestAnimationFrame){
            wrapper = function(time){
                if(time === undefined){
                    time += new Date();
                }
                self.callback(time);
            };
            originalWebkitMethod = window.webkitRequestAnimationFrame;
            window.webkitRequestAnimationFrame = function(callback,element){
                self.callback = callback;
                originalWebkitMethod(wrapper , element);
            }
        }
        if(window.mozRequestAnimationFrame){
            index = userAgent.indexOf('rv:');
            if(userAgent.indexOf('Gecko') != -1){
                geckoVersion = userAgent.substr(index+3 , 3);
                if(geckoVersion === '2.0'){
                    window.mozRequestAnimationFrame = undefined;
                }
            }
        }


        return window.requestNextAnimationFrame ||
               window.webkitRequestAnimationFrame ||
               window.mozRequestAnimationFrame ||
               window.oRequestAnimationFrame ||
               window.msRequestAnimationFrame ||


               function (callback , element){
                    var start,
                        finish;
                    window.setTimeout(function(){
                        start = +new Date();
                        callback(start);
                        finish = +new Date();
                        self.timeout = 1000/self.fps - (finish - start);
                    } , self.timeout);
               };
}
				
				
	
	


//-----------------调用----------------------------------------------------------

var qcanvas = new Qcanvas(["qcanvas",500,300]);
console.log(qcanvas);
				
var line1 = qcanvas.qline.line({
	start:[0,80],
	end:[50,50],
	color:'red',
	like:'-',
	withText:'动画'
});
var line2 = qcanvas.qline.line({
	start:[0,20],
	end:[150,50],
	color:'blue',
	like:'--',
	withText:'line2'
});
var line3 = qcanvas.qline.line({
	start:[30,50],
	end:[150,60],
	width:1,
	like:'->',
	color:'gray',
	withText:'line3'
});		

var line4 = qcanvas.qline.line({
	start:[100,123],
	end:[150,180],
	width:1,
	like:'-->',
	color:'gray',
	withText:'line4',
	withTextAlign:'left'
});
		
var text = qcanvas.qtext.text({
	start:[200,200],
	color:'blue',
	fontSize:'20px'
})		
	var textfps = qcanvas.qtext.text({
	start:[20,20],
		text:function(){ return qcanvas.currFps},
	color:'blue',
	fontSize:'20px'
})	
		
		
		
var rect = qcanvas.qrect.rect({
	start:[160,100],
	borderColor:'red',
	fillColor:'blue'
})		
		
var arc = qcanvas.qarc.arc({
	start:[100,100],
	sAngle:0,
	eAngle:360,
	fillColor:'',
	r:20
});		


var polygon = qcanvas.qpolygon.polygon({
	r:30,
	num:6,
	start:[350,200]
})

/*动画*/
qcanvas.qanimation.animate(line1,{
	start:[0,80],
},{
	start:[100,200],
},2,true);
		
qcanvas.qanimation.animate(arc,{
	eAngle:360,
},{
	eAngle:0,
},10,true);
		
		
qcanvas.load({
	"a":"http://sandbox.runjs.cn/uploads/rs/475/t0qpfflr/mb.png",
	"b":"http://sandbox.runjs.cn/uploads/rs/475/t0qpfflr/hand.png"
},function(){ 
	var b = qcanvas.getSourceByName("b");
	console.log(b.height);
	
	qcanvas.qimg.img({
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
		
		
		
		
		
console.log(rect);
console.log(line1);	
console.log(arc);
		
		
		
		
		
		
		

		



