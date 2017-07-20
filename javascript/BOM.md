##BOM基础

###1.window

	<input type="button" value="open" onclick="window.open('https://www.baidu.com');">

document.write();

open('url','_blank');

	var newWin = open('','_blank');
	
	newWin.document.write = 'hello';


close
	
	<input type="button" value="open" onclick="window.close()">

火狐里面不能打开用户打开的页面


	<input type="button" value="open" onclick="window.open(close.html);">

	window.close();


###2.userAgent

	alert(window.navigator.userAgent

###3.location

	window.location //当前地址
	
	window.loaction = '111'

###4.尺寸

	document.documentElement.clientWidth

	document.documentElement.scrollTop;  //ie 

	document.body.scrollTop;  // chrome

###5.window

	onload

	onresize

	onscroll

###6. alert() confirm() prompt()

	confirm   // true or false


	prompt（'dasd','das'）  //返回的值