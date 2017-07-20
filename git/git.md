# 版本控制 -- git

	git: git是目前世界上最先进的分布式版本控制系统（没有之一）。

###**那什么是版本控制系统?**
	简单点说：就是对自己修改的文件，进行修改次数的统计及内容修改部分的统计。方便以后，我们可以在以后任何时候找到之前修改的时间级内容。每次修改就好比更新了一个版本。

*tips: 除了git 还有SVN CVS 这些都是集中式管理系统。*

1. 集中式：简单说就是必须在联网，从服务器获取版本信息。
1. 分布式：简单说不必联网，每个人的电脑就是一台服务器。

##git的安装

**mac下面：**

1.你在终端里面直接输入git，然后回车。
2.根据提示的信息直接安装

**windows下面：**

[戳我](https://git-for-windows.github.io/)下载。

然后就是 next  next ... <font color="red">安装路径不要修改</font>

在命令行里面输入：  git --version  可以验证自己是否安装成功。

安装成功后，要自报家门：

	git config --global user.name "Your Name"

	git config --global user.email "email@example.com"

## git创建版本库 ##

声明：接下来的演示，我以window系统为例子。mac系统的同学可以一同操作，遇到问题及时反馈。

什么是版本库呢？版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

接下来我们在桌面新建一个文件夹作为自己的仓库。

我们需要打开git bash. 在命令行里面输入：

	desktop     //这个表示切换到桌面
	
	mkdir learngit  //新建一个learngit文件夹

	cd learngit    //进入learngit文件夹

	git init      //初始化一个仓库

![](http://i.imgur.com/PjEYisD.gif)

### 小试牛刀 ###

我们在learngit文件下面 新建一个文本文件，输入一段话。当然，你新建js html css都是可以的。
	
	git add readme.txt  

	git commit -m "created file"
	
命令一：加不加冒号都可以，但是要指明后缀名。

如果是多个文件的话可以这样写： git add readme1.txt readme2.txt 加个空格 如此而已！ 

如果内容过多 用git add *

命令二: 必须要加冒号了。

这段话的意思是给提交的内容添加描述。

![successful](http://i.imgur.com/mix89aG.png)

至此，表示提交成功！

![demo](http://i.imgur.com/8YBMlTB.gif)


工作这么久了，算是完成了今天的工作了！好下班，走你！（好假！唉~ 格式需要，没办法！）