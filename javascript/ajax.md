##ajax进阶

form的引起

	application/x-www-form-urlencoded

###php

get

	<?echo

	header('content-type:text/html;charset="utf-8"');
	error_reporting(0);
	
	$username = $_GET['username'];
	$age = $_GET['age'];
	
	echo "你的名字:{$username},年龄: {$age} "

post

	<?echo

	header('content-type:text/html;charset="utf-8"');
	error_reporting(0);
	
	$username = $_POST['username'];
	$age = $_POST['age'];
	
	echo "你的名字:{$username},年龄: {$age} "

true And false

	setTimeout(function (argument) {
		alert(1);
	}, 2000)

	alert(2)

后端输出：

	<?echo

	header('content-type:text/html;charset="utf-8"');
	error_reporting(0);
	
	$arr1 = array('leo','shen','jj');

	$arr2 = array('username'=>'leo','age'=>'18');
	
	echo json_encode($arr1);

返回内容的修改

	var arr = [1,2,3];
	alert(JSON.stringify(arr)) //change to string

	var str = '[100,200,300]';

	var arr1 = JSON_parse(str);

news

	$news = array(
	 array('titile' => '' , 'data' => '' ),
	 array('titile' => '' , 'data' => '' ),
	 array('titile' => '' , 'data' => '' ),
	 array('titile' => '' , 'data' => '' ),
	)

方法

	open('get',' news.php?username=123&age=23',true);

	open('get',' news.php?username=中文&age=23',true);//乱码
	
	encodeURI();

post文档类型

	xhr.setRequestHeader('content-type','application/x-www-form-urlencoded');

	xhr.send('uesername =leo&age=30')
	