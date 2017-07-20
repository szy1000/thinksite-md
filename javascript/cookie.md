##cookies

小甜饼： 浏览器的cookie。正如标题一般，它真的很小很小。由于浏览器的不同。他的大小在4-10K之间。它遵循 同源策略

格式：
	
	document.cookie='name=szy';
	document.cookie='password=123456'; 	

=是添加的意思

###1.设置cookie过期时间 

正常的cookie的生命周期，是关闭浏览器之后，就会消失。如果想设置过去时间的话。我们就需要要cookie的另外一个属性。”max-age = seconds”。还有其他的属性，请参见大犀牛的586页。

	document.cookie='name2=szy; max-age=10s'

用expires = time

	var oDate=new Date();
	oDate.setDate(oDate.getDate()+1);
	document.cookie='Name=szy; expires='+oDate;


	oDate.toUTCString();


###2.删除cookie

	document.cookie='Name=szy; expires= -1';


	function getCookies(name) {
	    var arr=document.cookie.split('; ');
	    for(var i=0;i<arr.length;i++){
	        var arr2=arr[i].split('=');
	        if(arr2[0]==name){
	            return arr2[1];
	        }
	    }
    return '';

###3.

	为了 方便大家，我将封装好的函数一并放到下面：
	
	//setCookie
	function setCookie(name,value,iDay) {
	    var oDate=new Date();
	    oDate.setDate(oDate.getDate()+iDay);
	    document.cookie=name+'='+value+';expires='+oDate.toUTCString();
	}
	
	//removeCookie
	function removeCookie(name){
	    setCookie(name,1,-1)
	}
	
	//getCookies
	function getCookies(name) {
	    var arr=document.cookie.split('; ');
	    for(var i=0;i<arr.length;i++){
	        var arr2=arr[i].split('=');
	        if(arr2[0]==name){
	            return arr2[1];
	        }
	    }
	    return '';
	}