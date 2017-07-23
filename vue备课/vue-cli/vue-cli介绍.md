#vue-cli介绍

什么是vue-cli就是使用vue的脚手架！方便我们快速开发 怎么去安装他呢？

###1.0 打开你的终端

	npm install vue

	# 全局安装 vue-cli
	npm install --global vue-cli
	# 创建一个基于 webpack 模板的新项目
	vue init webpack my-project
	# 安装依赖，走你
	cd my-project
	npm install
	npm run dev

###1.1 以下是我新建的项目

![]('./2.jpg')

以上信息：

- 项目名称
- 项目描述
- 作者
- 标准化
- 是否安装vue-router  我们这个项目会用到 需要要安装
- ESLint 是用来管理代码格式的插件 最好安装上 规范代码
- 后面的2个是用来模块测试 我们不需要  



###1.2进入项目 安装依赖管理

![]('./3.jpg')

###1.3启动项目

![]('./4.jpg')
你会看到一个基础的项目：

![]('./5.jpg')

###1.4编辑器的配置

.babelIrc es6的语法转换
.editorconfig 编辑器配置
.eslintignore  忽略检查的文件夹
.eslintrc 语法检查的规则
.postcssrc css预处理文件
package 是需要安装的依赖和库文件
