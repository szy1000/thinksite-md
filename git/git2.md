# 版本控制 -- git

## 状态查看 ##

好的！新的一天开始了。今天我们要继续工作，添加内容。

我们对readme.txt文件 添加一点东西。

![](http://i.imgur.com/JReB3lO.png)

在命令行里面输入：

	git status

查看当前的状态：

	$ git status
	On branch master
	Changes not staged for commit:
	  (use "git add <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)
	
	        modified:   readme.txt
	
	no changes added to commit (use "git add" and/or "git commit -a")

大致的信息就是： readme.txt文件被修改，改变的内容没有提交。

虽然git status能够告诉我们哪个文件被修改过。 但是我们并不知道，文件的哪里被修改了。

	$ git diff
	diff --git a/readme.txt b/readme.txt
	index ef91ba6..8afe9de 100644
	--- a/readme.txt
	+++ b/readme.txt
	@@ -1 +1,3 @@
	-created readme file
	\ No newline at end of file
	+created readme file<A3><A1>
	+
	+go on working!!!
	\ No newline at end of file

最底下的 + 表示添加的部分。 如果有删除部分的话！ 就显示 - 。

至此，我们已经知道哪里被修改过！接下来就是"添加文件"了

	git add readme.txt

	git status 

添加文件到暂存区，再来查看状态，显示没有被提交。

	$ git status
	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

    modified:   readme.txt

提交之后，再看状态：

	git commit -m "add some more"

添加后：

	$ git commit -m "add some more"
	[master c97e5f8] add some more
	 1 file changed, 3 insertions(+), 1 deletion(-)

最后查看状态：

	git status
显示工作区 是干净的了

	$ git status
	On branch master
	nothing to commit, working directory clean

至此！你已经会了 修改文件 并将其提交到版本库了。

至于工作区和暂存区的概念，我们后面会讲到！


## 版本回退 ##

>  --人非圣贤孰能无过！

提交了错误的版本，在工作当中是时有发生，碰到这样的情况怎么办？

git的作者早就为我们想好了！

我们需要使用：
	
	git log  

显示出来所有的版本号：

	$ git log
	commit 96c20466832f0d4bdf090500fa15ce92e370c1bb
	Author: szy1000 <1538078053@qq.com>
	Date:   Thu Jun 1 16:07:06 2017 +0800

    delete

	commit 8b50a57da2dd1250c29b3dbf6951c9ee85ceaa7f
	Author: szy1000 <1538078053@qq.com>
	Date:   Thu Jun 1 16:05:42 2017 +0800

    add some more

	commit c97e5f825a30d7ce76d599af3d8536e4d11bf545
	Author: szy1000 <1538078053@qq.com>
	Date:   Thu Jun 1 15:43:27 2017 +0800

    add some more

	commit 6735914237478ffe175e32c3d0ba776f690a5689
	Author: szy1000 <1538078053@qq.com>
	Date:   Thu Jun 1 15:01:48 2017 +0800

    created readme

到这里大家，就可以看到所有的信息都显示了。而且也看到 git commit -m "描述"的作用了吧！

如何去回退到指定的版本呢？

git reset --hard "版本号"

	git reset --hard 6735914

即可回退到你想要的版本。

如图 我回退到最初的版本了！

![](http://i.imgur.com/RvDTtSo.gif)