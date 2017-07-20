# 版本控制 -- git

**notes**: *这篇文章的内容非常乏味！却又是git的核心！请仔细 耐心 体会！* 

> 这个世界没有一顿烧烤解决不了的问题，有的话就两顿！                 --尼古拉斯·赵四
> 
> 这个世界没有一篇文章是看不懂的，有的话就两遍 三遍！


## 工作区(Working Directory)和版本库(Repository)

learngit文件夹就是工作区。

.git 影藏文件夹就是版本库

![](http://i.imgur.com/U5XbHQE.png)

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。我们以后再说分支和HEAD。

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
![](http://i.imgur.com/1Izapr0.png)

第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支

![](http://i.imgur.com/7U19NtF.png)

这是我们还是需要用到 *git status* 命令去帮助我们查看，自己的文件在哪个状态里面。

![](http://i.imgur.com/uV76cxl.gif)


##分支

在版本回退里，你已经知道，每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

一开始的时候，master分支是一条线，Git用master指向最新的提交，再用HEAD指向master，就能确定当前分支，以及当前分支的提交点：

![](http://i.imgur.com/qsV15mo.png)

当我们创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上：

![](http://i.imgur.com/Xd2BtQq.png)

你看，Git创建一个分支很快，因为除了增加一个dev指针，改改HEAD的指向，工作区的文件都没有任何变化！

不过，从现在开始，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针不变：

![](http://i.imgur.com/Juht8UX.png)

假如我们在dev上的工作完成了，就可以把dev合并到master上。Git怎么合并呢？最简单的方法，就是直接把master指向dev的当前提交，就完成了合并：

![](http://i.imgur.com/JDMagQW.png)

所以Git合并分支也很快！就改改指针，工作区内容也不变！

合并完分支后，甚至可以删除dev分支。删除dev分支就是把dev指针给删掉，删掉后，我们就剩下了一条master分支：

![](http://i.imgur.com/noLUWQW.png)

命令：
	
	git checkout -b dev   //新建分支dev并跳转到dev分支上面

	//上面的命令分开写 如下：

	git branch dev      //新建分支
	git checkout dev    //跳转分支

上面的属于连写

	git branch    //查看分支
	
	git checkout dev  跳转分支

新建分支之后，进行开发修改！ 开发结束后 跳回主分支。合并刚才的开发分支

	git merge dev    //将merge合并到master

	git branch -d dev  //删除dev分支


总结：

	查看分支：git branch
	
	创建分支：git branch <name>
	
	切换分支：git checkout <name>
	
	创建+切换分支：git checkout -b <name>
	
	合并某分支到当前分支：git merge <name>
	
	删除分支：git branch -d <name>

