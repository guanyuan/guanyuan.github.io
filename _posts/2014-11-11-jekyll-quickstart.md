---
layout: post
title: "Jekyll QuickStart"
description: ""
category: 
tags: []
---
{% include JB/setup %}


## 建立远程仓库
需要注意的是：用户名USERNAME必须与你的github账户名一样。

1. 在你的github上[https://github.com]新建一个仓库，名称为： USERNAME.github.io

2. 切换到你想要存放博客的目录，执行以下命令：
```
git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
cd USERNAME.github.com
git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
git push origin master
```

3. 等待
这个时间可能比较长，通常需要10分钟以上。

4. 本地安装Jekyll
不是必须的，然而如果你想要在push之前预览自己的博客，可以安装一个本地Jekyll。
```
$ gem install jekyll
```
我在安装的过程中，遇到了问题：通过更换gem的仓库地址得以解决，具体见：
```
$ gem sources --remove http://rubygems.org/
$ gem sources -a http://ruby.taobao.org/
$ gem sources -l
*** CURRENT SOURCES ***
http://ruby.taobao.org   
$ gem install jekyll
```
安装结束后，执行
```
$ cd USERNAME.github.com 
$ jekyll serve
```
用浏览器打开： http://localhost:4000/
就可以看到效果。

5. 新建一个post
```
$ rake post title="Jekyll QuickStart"
```
此操作将会在guanyuan.github.io/_posts/目录下，新建文件： 2014-11-11-jekyll-quickstart.md

6. 新建一个Page
```
#Create pages easily via rake task:
$ rake page name="about.md"

#Create a nested page:
$ rake page name="pages/about.md"
```
将分别在当前目录下生成about.md 或 pages/about.md，并且在文件头生成自动include Jekyll Bootstrap "setup"文件。

6. 发布
```
$ git add .
$ git commit -m "Add new content"
$ git push origin master
```
每次提交，如果有错误，可以在仓库首页的setting选项中看到。

6. 定制
主题，可以在[这里](http://themes.jekyllbootstrap.com/preview/the-minimum/)浏览可用的jekyll主题.
比如这里选择主题
安装过程如下：
```
$ rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"
```
安装结束后，会提示是否切换到该主题，输入yes
此外还可以通过手动方式安装主题，将主题下载到：_theme_packages 目录下，安装并切换主题：
```
$ rake theme:install name="the-program"
$ rake theme:switch name="the-program"
```
主题的配置文件在： ./_includes/themes/THEME-NAME， 而\_layout中存放的时当前主题的配置信息。所以如果要对主题进行修改，应该对源文件进行修改，而layout目录下仅仅是源文件的一个拷贝。
修改结束后，必须要重新切换主题，修改才会生效
```
$ rake theme:switch name="the-program"
```



参考：
1. http://jekyllbootstrap.com/usage/jekyll-quick-start.html
2. http://jekyllbootstrap.com/usage/jekyll-theming.html
