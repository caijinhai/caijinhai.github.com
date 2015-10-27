---
layout: post
title: "基于github和jekyll建blog"
description: "在github上建blog"
keywords: "github ruby jekyll blog"
category: 随笔
tags: [github]
---
{% include JB/setup %}

###安装jekyll
	####1.先下载安装ruby环境
	在 https://pages.github.com/versions/ 查看所需要的Ruby版本，下载安装。
	最好保持默认的路径 C:\Ruby200-x64， 因为安装包明确提出 “请不要使用带有空格的文件夹 (如： Program Files)”。
	勾选 “Add Ruby executables to your PATH”（配置PATH环境），其他两个选项也可以勾选。
	
	PATH环境配置：我的电脑》》属性》》高级选项》》环境变量》》编辑》》PATH中加入ruby路径例如：“C:\Ruby22-x64\bin”
	
	####2.安装devkit
	DevKit - RubyInstaller	DevKit 是一个在 Windows 上帮助简化安装及使用 Ruby C/C++ 扩展如 RDiscount 和 RedCloth 的工具箱。
	1)再次前往 http://rubyinstaller.org/downloads/
	2)下载同系统及 Ruby 版本相对应的 DevKit 安装包。
	For use with Ruby 1.8.7 and 1.9.3:

	DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe
	For use with Ruby 2.0 and above (32bits version only):

	DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe
	For use with Ruby 2.0 and above (x64 - 64bits only)

	DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe
	
	1)运行安装包并解压缩至某文件夹，如 C:\DevKit
	2)通过初始化来创建 config.yml 文件。在命令行窗口内，输入下列命令：
	cd “C:\DevKit”
	ruby dk.rb init  //初始化
	notepad config.yml   //记事本打开config.yml文件
	3)在打开的记事本窗口中，于末尾添加新的一行 - C:\Ruby200-x64,（或者在# - C:/ruby192dev一行中去掉#修改为ruby文件路径）保存文件并退出。
	4)回到命令行窗口内，执行安装。
	ruby dk.rb install
	
	####3.安装jekyll
	执行命令 gem  install jekeyll
	
	在此处我出现了一个错误：
	提示:ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
	Errno::ECONNRESET: An existing connection was forcibly closed by the remote host. - SSL_connects.org/quick/Marshal.4.8/jekyll-2.5.3.gemspec.rz)
	搜素很久后才明白原因：如下
	由于 RubyGems 的服务器是放在国外的，因此国内用户使用起来会比较的费劲，甚至是无法使用，好在阿里巴巴帮我们解决了这个问题，在国内的用户建议添加使用阿里巴巴提供的镜像：
	命令 gem sources -a http://ruby.taobao.org/  //增加gem sources 地址
	命令 gem sources -l  //查看本地sources
	*** CURRENT SOURCES ***

	https://rubygems.org/
	http://ruby.taobao.org/
	命令　gem sources --remove https://rubygems.org/     //删除原有的gem sources
	记住：只能有个gem sources 并且可以访问的。否则可能有问题
	解决问题后重新安装： gem install jekyll
###至此安装jekyll完成
	
<!-- more -->

###用jekyll建blog
	####在此有两种方法
	####自己建文件及模板，比较麻烦。
	1、建一个文件夹 ：mikdir new blog  
	2、到文件夹下建git 初始化： cd jekyll_demo    git init
	3、创建一个_layouts目录，用于存放模板文件。进入该目录，创建一个default.html文件，作为Blog的默认模板。
	4、创建一个_posts目录，用于存放blog文章。
	·······
	通过git命令提交到github上。
	建页面以及相关目录，模仿http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html欢迎去参考
	
	####自动创建blog
	1)jekyll new blog  //命令创建。(本人没试过 ，仅供产考)
	这样就会创建一个新文件夹d:/blog，其结构如下：
	1. 文件夹_layouts：用于存放模板的文件夹，里面有两个模板，default.html和post.html
	2. 文件夹_posts：用于存放博客文章的文件夹，里面有一篇markdown格式的文章--2014-01-27-welcome-to-jekyll.markdown
	3. 文件夹css：存放博客所用css的文件夹
	4. .gitignore：可以删掉，后面会将项目添加到git项目，所以这个不需要了
	5. _coinfig.yml：jekyll的配置文件，里面可以定义相当多的配置参数，具体配置参数可以参照其官网
	6. index.html：项目的首页

	根据实际需要，可能还需要创建如下文件或文件夹：
	1. _includes:用于存放一些固定的HTML代码段，文件为.html格式，可以在模板中通过liquid标签引入，常用来在各个模板中复用如 导航条、标签栏、侧边栏 之类的在每个页面上都一样不变的内容，需要注意的是，这个代码段也可以是未被编译的，也就是说也可以使用liquid标签放在这些代码段中
	2. image和js等自定义文件夹：用来存放一些需要的资源文件，如图片或者javascript文件，可以任意命名
	3. CNAME文件：用来在github上做域名绑定的，将在后面介绍
	4. favicon.ico：网站的小图标
	....

	创建完需要的文件夹之后，首先需要修改的就是jekyll的配置文件_config.yml，这个配置文件的内容相当多，详细见官方文档
	开启服务  jekyll serve   
	在localhost:4000 访问，
	可以参考：http://segmentfault.com/a/1190000000406013
	
	2)克隆模板
	先在github上fock别人的到自己github中
	git clone https://github.com/username/username.github.com（名字只能改为username.github.com，用你的github名替换username） //github上随便一搜github pages 很多的。
	克隆到本中，修改一下config.yml配置文件内容，改为自己的信息，轻松搞定。
	每一次修改再push 到远程
	git add .
	git commit -m "config.yml"
	git push origin master
	到处blog轻松搞定，通过username.github.io即可访问
reply:

			from 个人邮件:   cjh123honey@gmail.com
			from 个人博客：　http://caijinhai.github.io
			from 个人微信公众订阅号: superbar