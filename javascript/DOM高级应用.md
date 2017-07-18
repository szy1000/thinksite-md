##DOM的高级应用

关于table的那些事！

1. tbody不要省略！
2. display可以为none,但是不能为block
3. cellpadding="0" cellspacing="0"
4. 固定宽度 border-collapse:collapse;table-layout:fixed

```css
padding: 0 10px;  
width: 40px;  
height: 30px;  
overflow: hidden;  
text-overflow: ellipsis;  
white-space: nowrap;  
```
5.tbale的一些便捷操作！
 tBodies rows cells
 
 <font color="red">tBodies是个坑啊！！！</font>
 
 ```javascript
var tab = document.getElementById('tab');
var con = tab.getElementsByTagName('tbody')[0].getElementsByTagName('tr')[1].getElementsByTagName('td')[0].innerHTML;
alert(tab.tBodies[0].rows[1].cells[2].innerHTML)
 ```
6.各行变色，hover变色

办法一:css
	
```css
table tbody tr:nth-child(even){
  background-color: #ddd;
}
tbody tr:hover{
  background-color: #ccc!important;
}
```	
方法二： javascript

```javascript
var tab = document.getElementById('tab');
var temp = null;
for(var i=0;i<tab.tBodies[0].rows.length;i++){
	if(i%2!=0){
      tab.tBodies[0].rows[i].style.background = '#ccc';
    }
    tab.tBodies[0].rows[i].onmouseover = function(){
      temp = this.style.background;
      this.style.background = '#ddd';
    }
    tab.tBodies[0].rows[i].onmouseout = function(){
      this.style.background = temp;
    }
}

```

7.添加tr

```javascript
btn.onclick = function(){
    alert(age.value)
    var otr = document.createElement('tr');

    var td = document.createElement('td');
    td.innerHTML = tab.tBodies[0].rows.length+1;
    otr.appendChild(td);

    var td = document.createElement('td');
    td.innerHTML = name.value;
    otr.appendChild(td);

    var td = document.createElement('td');
    td.innerHTML = age.value;
    otr.appendChild(td);

    tab.tBodies[0].appendChild(otr);
  }
  ```
8.删除tr

```javascript
td.getElementsByTagName('a')[0].onclick = function(){
  	tab.tBodies[0].removeChild(this.parentNode.parentNode)
}
        
```

9.查询
```javascript	
btn.onclick = function(){       
    for(var i=0;i<tab.tBodies[0].rows.length;i++){
      if(tab.tBodies[0].rows[i].cells[1].innerHTML ==name.value.trim()){
        temp = tab.tBodies[0].rows[i].style.background;
        tab.tBodies[0].rows[i].style.background = 'yellow';

      }else{
        tab.tBodies[0].rows[i].style.background = '';
      }
    }
  }
```

搜索：
toLowerCase()
search() != -1