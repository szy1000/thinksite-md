##jquery高级篇

###1.1 jquery和JavaScript可以共存，但是不能够混用！

案例一：

原生写法：
	<div id="box"></div>
	<script>
		var oBox = document.getElementById('box');
		oBox.onclick = function(){
			this.style.background = 'blue'
		}
	</script>

jquery写法：
	
	<div id="box"></div>
	$('#box').click(function(){
		$(this).css('background','blue');
	})

错误写法：

	<div id="box"></div>
	<script>
		$(document).ready(function () {
			$('#box').onclick = function(){
				this.style.background = blue;
			}
		})
	</script>

以上代码会报红，试问混用该如之奈何？

	<div id="box"></div>
	<script>
		$(document).ready(function () {
			$('#box').get(0).onclick = function(){
				this.style.background = blue;
			}
		})
	</script>

一个get()就可以解决问题。

*其实下标也是可以解决的 辅助了解 不推荐使用*

*$('#box')[0].style.background = 'blue'*

注意：li标签的lenth？

	alert($('li').length）; //获取li的长度

length虽然是原生js的一个属性，但是length也是jquery里面封装过的方法，可以直接使用！但是个人建议你，如果需要获取长度的时候还是去使用size()方法。

	alert($('li').size()); //获取li的长度

辅助篇：

	for(var i=0;i<$('li').length;i++){
		//修改字体大小
		$("li").css('fontSize','30px');
		//如何说我只是想修改第二个怎么办？
		$("li").eq(2).css('fontSize','30px');
	}


###1.2 outWidth() 与 offsetWidth
	
	#box{
		width: 200px;
		height: 200px;
		background-color: red;
		display: none;
	}

	<div id="box"></div>
	<script>
		var oBox = document.getElementById('box');
		alert(oBox.offsetWidth);  //如果div为none的话就获取不到div的值
	</script>
	
为了解决这样的问题，所以我们就需要使用outerWidth()。

	<script>
		alert($('#box').outerWidth());
		// alert($('#box').width());//仅仅获取宽度
	</script>

<font color="red">此时，我们给div加上padding！再来弹出来看看效果</font>

outerWidth()获取到是 content + padding

试问： 如果我们连div的margin也要获取到怎么办呢？

	alert($('#box').outerWidth(true));

给outerWidth(true)传一个true值即可！


### 1.3text() 和 html()
text仅仅返回 标签内部的内容 不会返回标签，负值也是这样

	<p id="para">I am para <span>I am span</span> !</p>
	<script>
		alert($('#para').tetx()); 
	</script>
	
html可以返回标签，但是唯一遗憾的 只能返回第一个！

	<p>I am para <span>I am span</span> !</p>
	<p>I am para aaa <span>I am span</span> !</p>
	<script>
		alert($('p').html());
	</script>
	
设置值的话，可以一起设置

	<p>I am para <span>I am span</span> !</p>
	<p>I am para aaa <span>I am span</span> !</p>
	<script>
		$('p').html('<h1>das</h1>');
	</script>
	
	
###1.4remove() 和 detach()

我们先写一个div 并为其添加一个click事件。

	$('#box').click(function(){
			alert(1);
		})
如果在开发的时候 需要删除它！但是在后面的操作当中可能又要遇到div的添加它

	var box = $('#box').remove();
	$('body').append(box)	
	
但是我们再次点击。发现事件没有了！

为了解决这样的bug！我们就必须使用detach()了;

	$('#box').click(function(){
		alert(1);
	})

	var box = $('#box').detach();
	$('body').append(box)
	
完美！！！

###1.5 $() 和 window.onload = function(){}

	$() //是等DOM加载完毕
	
	window.onload = function(){}. //全部加载完毕
	
试问：
 


1. outWidth是获取padding + content 的值
获取分别获取div的content width margin-top的值？
2.	innerWidth 和outWidth的区别？
3.	如果html('&lt; h1 &gt; 哈哈 &lt; /h1 &gt;') 和 text('&lt; h1 &gt; 哈哈 &lt; /h1 &gt;') 参考1.3
4.	试一试*$('#box')[0].style.background = 'blue'*
5.	写进博客


