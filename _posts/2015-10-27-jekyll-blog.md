---
layout: post
title: "����github��jekyll��blog"
description: "��github�Ͻ�blog"
keywords: "github ruby jekyll blog"
category: ���
tags: [github]
---
{% include JB/setup %}

###��װjekyll
	####1.�����ذ�װruby����
	�� https://pages.github.com/versions/ �鿴����Ҫ��Ruby�汾�����ذ�װ��
	��ñ���Ĭ�ϵ�·�� C:\Ruby200-x64�� ��Ϊ��װ����ȷ��� ���벻Ҫʹ�ô��пո���ļ��� (�磺 Program Files)����
	��ѡ ��Add Ruby executables to your PATH��������PATH����������������ѡ��Ҳ���Թ�ѡ��
	
	PATH�������ã��ҵĵ��ԡ������ԡ����߼�ѡ����������������༭����PATH�м���ruby·�����磺��C:\Ruby22-x64\bin��
	
	####2.��װdevkit
	DevKit - RubyInstaller	DevKit ��һ���� Windows �ϰ����򻯰�װ��ʹ�� Ruby C/C++ ��չ�� RDiscount �� RedCloth �Ĺ����䡣
	1)�ٴ�ǰ�� http://rubyinstaller.org/downloads/
	2)����ͬϵͳ�� Ruby �汾���Ӧ�� DevKit ��װ����
	For use with Ruby 1.8.7 and 1.9.3:

	DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe
	For use with Ruby 2.0 and above (32bits version only):

	DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe
	For use with Ruby 2.0 and above (x64 - 64bits only)

	DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe
	
	1)���а�װ������ѹ����ĳ�ļ��У��� C:\DevKit
	2)ͨ����ʼ�������� config.yml �ļ����������д����ڣ������������
	cd ��C:\DevKit��
	ruby dk.rb init  //��ʼ��
	notepad config.yml   //���±���config.yml�ļ�
	3)�ڴ򿪵ļ��±������У���ĩβ����µ�һ�� - C:\Ruby200-x64,��������# - C:/ruby192devһ����ȥ��#�޸�Ϊruby�ļ�·���������ļ����˳���
	4)�ص������д����ڣ�ִ�а�װ��
	ruby dk.rb install
	
	####3.��װjekyll
	ִ������ gem  install jekeyll
	
	�ڴ˴��ҳ�����һ������
	��ʾ:ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
	Errno::ECONNRESET: An existing connection was forcibly closed by the remote host. - SSL_connects.org/quick/Marshal.4.8/jekyll-2.5.3.gemspec.rz)
	���غܾú������ԭ������
	���� RubyGems �ķ������Ƿ��ڹ���ģ���˹����û�ʹ��������ȽϵķѾ����������޷�ʹ�ã����ڰ���ͰͰ����ǽ����������⣬�ڹ��ڵ��û��������ʹ�ð���Ͱ��ṩ�ľ���
	���� gem sources -a http://ruby.taobao.org/  //����gem sources ��ַ
	���� gem sources -l  //�鿴����sources
	*** CURRENT SOURCES ***

	https://rubygems.org/
	http://ruby.taobao.org/
	���gem sources --remove https://rubygems.org/     //ɾ��ԭ�е�gem sources
	��ס��ֻ���и�gem sources ���ҿ��Է��ʵġ��������������
	�����������°�װ�� gem install jekyll
###���˰�װjekyll���
	
<!-- more -->

###��jekyll��blog
	####�ڴ������ַ���
	####�Լ����ļ���ģ�壬�Ƚ��鷳��
	1����һ���ļ��� ��mikdir new blog  
	2�����ļ����½�git ��ʼ���� cd jekyll_demo    git init
	3������һ��_layoutsĿ¼�����ڴ��ģ���ļ��������Ŀ¼������һ��default.html�ļ�����ΪBlog��Ĭ��ģ�塣
	4������һ��_postsĿ¼�����ڴ��blog���¡�
	��������������
	ͨ��git�����ύ��github�ϡ�
	��ҳ���Լ����Ŀ¼��ģ��http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html��ӭȥ�ο�
	
	####�Զ�����blog
	1)jekyll new blog  //�������(����û�Թ� ����������)
	�����ͻᴴ��һ�����ļ���d:/blog����ṹ���£�
	1. �ļ���_layouts�����ڴ��ģ����ļ��У�����������ģ�壬default.html��post.html
	2. �ļ���_posts�����ڴ�Ų������µ��ļ��У�������һƪmarkdown��ʽ������--2014-01-27-welcome-to-jekyll.markdown
	3. �ļ���css����Ų�������css���ļ���
	4. .gitignore������ɾ��������Ὣ��Ŀ��ӵ�git��Ŀ�������������Ҫ��
	5. _coinfig.yml��jekyll�������ļ���������Զ����൱������ò������������ò������Բ��������
	6. index.html����Ŀ����ҳ

	����ʵ����Ҫ�����ܻ���Ҫ���������ļ����ļ��У�
	1. _includes:���ڴ��һЩ�̶���HTML����Σ��ļ�Ϊ.html��ʽ��������ģ����ͨ��liquid��ǩ���룬�������ڸ���ģ���и����� ����������ǩ��������� ֮�����ÿ��ҳ���϶�һ����������ݣ���Ҫע����ǣ���������Ҳ������δ������ģ�Ҳ����˵Ҳ����ʹ��liquid��ǩ������Щ�������
	2. image��js���Զ����ļ��У��������һЩ��Ҫ����Դ�ļ�����ͼƬ����javascript�ļ���������������
	3. CNAME�ļ���������github���������󶨵ģ����ں������
	4. favicon.ico����վ��Сͼ��
	....

	��������Ҫ���ļ���֮��������Ҫ�޸ĵľ���jekyll�������ļ�_config.yml����������ļ��������൱�࣬��ϸ���ٷ��ĵ�
	��������  jekyll serve   
	��localhost:4000 ���ʣ�
	���Բο���http://segmentfault.com/a/1190000000406013
	
	2)��¡ģ��
	����github��fock���˵ĵ��Լ�github��
	git clone https://github.com/username/username.github.com������ֻ�ܸ�Ϊusername.github.com�������github���滻username�� //github�����һ��github pages �ܶ�ġ�
	��¡�����У��޸�һ��config.yml�����ļ����ݣ���Ϊ�Լ�����Ϣ�����ɸ㶨��
	ÿһ���޸���push ��Զ��
	git add .
	git commit -m "config.yml"
	git push origin master
	����blog���ɸ㶨��ͨ��username.github.io���ɷ���
reply:

			from �����ʼ�:   cjh123honey@gmail.com
			from ���˲��ͣ���http://caijinhai.github.io
			from ����΢�Ź��ڶ��ĺ�: superbar