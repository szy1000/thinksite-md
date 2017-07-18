##jquery高级篇二

###1.1节点操作parent() parents() closet()

	<style>
		#div1{
			width: 300px;
			height: 300px;
			background-color: blue;
		}

		#div2{
			width: 200px;
			height: 200px;
			background-color: red;
		}
	</style>
	
使用parent仅能作用到父级

	<div id="div1">
		<div id="div2">
			
		</div>
	</div>

	<script>
		$(document).click(function(){
			$('#div2').parent().css('background','yellow');
		})
	</script>
	
parents能作用到全部的父级及上级元素

	('#div2').parents().css('background','yellow');
		})
		
parents还可以传参数，作为选择器

	$(document).click(function(){
			$('#div2').parents('.aaa').css('background','yellow');
		})
		
选择父级及以上节点的带有aaa类名的元素

	$('#div2').closest('.aaa').css('background','yellow')
	
closet函数 必须要传参

###1.2siblings()

获取的是兄弟节点，但是不包括自身。

	<ul>
		<li>1</li>
		<li class="two">2</li>
		<li>3</li>
		<li>4</li>
	</ul>

	<script>
		$(document).click(function(){
			$('.two').siblings().css('background','yellow')
		})
	</script>

###1.3 next() nextAll() nextUntil()
next()获取的是同级后面的第一个元素

	$('.two').next().css('background','yellow');

nextAll()获取的是同级后面的所有元素

	$('.two').nextAll().css('background','yellow');	
nextUntil()获取的是同级后面的所有元素知道某个元素 但是不包括该元素的自身

	<ul>
		<li>1</li>
		<li class="two">2</li>
		<li class="aaa">3</li>
		<li class="bbb">4</li>
		<li class="ccc">5</li>
	</ul>

	<script>
		$(document).click(function(){
			$('.two').nextUntil('.ccc').css('background','yellow');
		})
	</script>
	
###1.4过滤 first() last() eq() filter() not()
	
	first()就是获取第一个，这个不用多说了 如同eq(0);
	
请问： last() 怎么用eq()去表示呢？

	是 $('li').size()-1
	还是 -1

filter表示过滤的意思 在函数里面可以输入过滤条件

	$('li').filter('li:nth-child(2n)').css('background','yellow');
	
是2的倍数都变成了黄颜色！

试问： not()会是什么效果呢？

###1.5wrap() wrapAll()
	
	<span>1</span>
	<span>2</span>
	<span>3</span>
	
	$('span').wrap('<div>');

	

wrapAll()需要注意的是
	
	<span>1</span>
	<span>2</span>
	<p>para</p>
	<span>3</span>
	
	$('span').wrapAll('<div>');
	
会将span包裹。

###1.6
作业：
 
1. 子节点怎么去获取，使用什么方法？
2. 兄弟节点的前面元素怎么获取？
3. 包装子元素怎么办？拆包怎么办？参考1.5
4. 拆包的什么会有一个小坑！！！