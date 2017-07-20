# 版本控制 -- git

人有失手 马有失蹄！

我们新建一个分支，在新建的分支上面进行开发。
	
	git checkout -b line1

然后对readme进行修改操作！并提交！

	git add readme.txt
	git commit -m "add news"

切回主分支。

	git checkout master

![](http://i.imgur.com/Nh5VgRX.gif)

可以清楚的看到 我们在line1分支修改的内容，回到主分支上面，将不再显示。如果 我们由于某些原因，忘记了 git merge <branch name>(忘记的同学请看上一篇文章)进行合并的话，进而继续在master分支进行开发。

回到主分支之后，继续开发 然后提交。 当我们合并的时候，就会发现。

	git checkout master

	git branch

	git add readme.txt

	git commit -m "add new on master"

	git merge line1    //合并  

	//报错


![](http://i.imgur.com/pEY3wlO.gif)

报错之后，我们发现。在不同分支上面开发的内容 都显示在文件里面了。 

<<<<< HEAD  some changes  =============  some changes  >>>>>> 标注起来了

其实。此时git内部结构是这样的。

![](http://i.imgur.com/5mupSRS.jpg)

至此，我们必须 要手动去修改文件。

假设，我们休要保留 2个分支的修改内容。 如果下图，即可完成修改！

![](http://i.imgur.com/ykePRQH.gif)

此时git内部结构是这样的。

![](http://i.imgur.com/4VBVHLs.jpg)

	git branch -d line1  //删除分支