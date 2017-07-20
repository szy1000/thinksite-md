#canvas

HTML5里面的新特性，不知道canvas 你就不是一个前端工程师

##1.1 基本用法

使用canvas标签 并指定其宽高。如果浏览器不支持的话，就会显示标签中文字。用以提示用户！

	<canvas id="drawing" width="300" height="400">Your broswer does't support it</canvas>

要想在这块画布上面，画画的话。必须获取到他。

	var drawing = document.getElementById('drawing');

它的身上有一个方法，要在使用之前进行检验。 

	getContext()

如下：

	var drawing = document.getElementById('drawing');
	if(drawing.getContext){
		var context = drawing.getContext("2d");
	}

##1.2 2D上下文

###1.0 填充和描边	

	context.strokeStyle = '' //线条
	context.fillStyle = ''   //填充背景色

不写的话均为黑色

###1.1 绘制矩形

	context.strokeStyle = '#ff0';
	context.strokeRect( 30, 30, 200, 30)
	
	context.fillStyle = 'rgba(255,0,0,.3)';
	context.fillRect(0, 0, 200, 30);

<font color="red">

1. 不写的话均为黑色 写错也是黑色
2. 必须先写好颜色 后写好形状

</font>

*tips:线条的粗细是有lineWidth属性进行控制的的 末端的样式可以改变圆角 方角的*

	context.strokeStyle = '#000';
	context.beginPath();
	context.lineWidth = 10;
	context.lineCap = "round";
	context.moveTo(20, 20);
	context.lineTo(200, 20);
	context.stroke();

需要注意书写的位置，位置错误 会导致不能显示

	context.clearRect(80,10, 20,20);

可以切割出一个小div。

###1.2绘制路径

	
