# 版本控制 -- git

拥抱github!

首先声明一下： 许多人把git github混为一谈。 其实不然！ 

git 是版本控制器

github 是一个远程的线上仓库

各位先去github注册一个帐号。

在setting SSH里面 可以找到自己的密钥  然后新建一个线上仓库。

	git clone address

克隆线上的地址。

![](http://i.imgur.com/mBkcxaz.png)

在本地修改后，我们需要
	
	git add *

	git commit -m "description"

	git push origin <branch>  //推送到线上的地址

	

获取线上的：

	git pull origin master  //一般都是master

如果合并失败: 需要我们手动去修改,然后

	git merge <branch>


本地连接线上的github 我没有演示！ 因为我已经连接好了。

大家自己根据[教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000)去测试。

配置好了本地，最好不要去修改，以免不必要的麻烦。