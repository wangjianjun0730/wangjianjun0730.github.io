---
layout: post
title: github pages + jekyll制作个人BLOG详细流程
date: 2017-10-24 19:00:24.000000000 +08:00
---
## 一.	Github Pages介绍

>GitHub Pages 可以为你或者你的项目提供介绍网页，它是由 GitHub 官方托管和发布的。你可以使用 GitHub 提供的页面自动生成器，也可以做个人博客，是个轻量级的博客系统。它不需你自己搭建服务器，但是每一个github账号只能制作一个首页，下面讲讲详细的制作流程。


## 二.	Github二级域名创建
>这一步Github Pages官网首页就有图文说明，但前提是你必须注册申请github账号,但是作为码农，github账号还是用该有的。

- **1.打开创建代码仓库页面**
 
![](../assets/images/Snip20171024_7.png)

>注意：创建的仓库名称必须为 \"github账号名称.github.io\" 的形式，建议仓库初始化的选项需要勾上。有很多博客并没勾选此项，在创建好仓库后本地安装 GitHub Desktop 然后通过命令行的方式处理，本人能力问题并没有成功，走了很多冤枉路感觉很繁琐，更何况github网页改版，很多地方都有不一致的情况。

![](../assets/images/Snip20171024_8.png)

	点击左上角Setting下载页面模板

![](../assets/images/Snip20171024_12.png)

![](../assets/images/Snip20171024_11.png)

	选择Select Theme 然后提交（后面的的图我就不贴了）

- 2.将刚刚创建的代码仓库，克隆一份到电脑本地(本人使用的SourceTree，直接check out到本地)
- 3.创建一个简单的Hello World静态页面用终端在目录下创建index.html文件，输入文件内容

```
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>

```

- 4.将这个html文件直接放入刚才克隆的本地仓库，然后push到远程仓库中。打开浏览器输入"github账号名称.github.io"就能看到我们刚才上传的HTML页面了。

![](../assets/images/Snip20171024_16.png)

> 到这里，我们只完成了一般，这个页面很粗糙，并不是我们想要的。我们不仅想看到华丽的页面展示，还想用markdown书写笔记。请继续往下看...

## 三.Jekyll本地环境搭建（待完善）

	a. Jekyll是一种简单的、适用于博客的、静态网站生成引擎。它使用一个模板目录作为网站布局的基础框架，支持Markdown、Textile等标记语言的解析，提供了模板、变量、插件等功能，最终生成一个完整的静态Web站点。说白了就是，只要安装Jekyll的规范和结构，不用写html，就可以生成网站。
	b. Jekyll的核心其实就是一个文本的转换引擎，用你最喜欢的标记语言写文档，可以是Markdown、Textile或者HTML等等，再通过layout将文档拼装起来，根据你设置的URL规则来展现，这些都是通过严格的配置文件来定义，最终的产出就是web页面。

- 1.Jekyll的结构（这里作为了解，熟悉一下）

	```objc

		|-- _config.yml
		|-- _includes
		|-- _layouts
		|   |-- default.html
		|    -- post.html
		|-- _posts
		|   |-- 2007-10-29-why-every-programmer-should-play-nethack.textile
		|    -- 2009-04-26-barcamp-boston-4-roundup.textile
		|-- _site
 		 -- index.html
 
	```

- 2.Jekyll的安装

	- a.安装ruby（Mac电脑自带安装了ruby环境，这里可以忽略。对于因为更新最新系统的伙伴可以重装一下ruby,不知道的可以自行百度）

	- b.打开终端，执行sudo gem install jekyll（用vpn比较快点）
	>注意:	如果是在淘宝的镜像，可能找不到Jekyll.我用的镜像是https://gems.ruby-china.org。但是我是直接更换了镜像，https://gems.ruby-china.org这个没有用这个试过，小伙伴们可以尝试一下<br>

		```
		如果执行sudo gem install jekyll失败，则有可能是镜像问题
		
		更换镜像：
		gem source -r https://ruby.taobao.org/ (移除淘宝镜像)
		gem source -a https://rubygems.org/ (添加新镜像)
		查看当前镜像：
		在终端输入  gem source，出现下面输出代表更换成功
		*** CURRENT SOURCES ***
		https://rubygems.org/	
		
		然后再重新执行：
		再次执行sudo gem install jekyll，输入电脑密码，等待安装一会
		
		
		终端输入：jekyll -v可以查看当前安装的jekyll版本号

		```
		
	
- 3.下载模板并替换本地仓库模板文件

	![](./assets/images/Snip20171024_17.png)
	
	>我下载的是vno-jekyll,看下图
	
	![](../_site/assets/images/Snip20171024_23.png)
	
	>解压下载好的模板压缩包，将包内除了.gitignore,README.md文件外的所有文件复制，粘贴到本地仓库中
	
	![](../assets/images/Snip20171024_25.png)
	


- 4.开启Jekyll环境，在本地仓库目录下执行:jekyll serve，看见下面输出代表开启成功。

```

MacBook-Pro:~ pingankeji$ cd /Users/pingankeji/wangjianjun0730.github.io
MacBook-Pro:wangjianjun0730.github.io pingankeji$ jekyll serve


```

- 5.在浏览器输入http://127.0.0.1:4000/，即可看见刚刚从网上下载的vno-jekyll主体技术博客了 （127.0.0.1是本机ip）

- 6.用git电脑终端将这些代码都上传到git代码仓库。浏览器输入(你的用户名).github.io，就可以看到你的成效了。

	![](../assets/images/Snip20171024_27.png)


## 四.评论功能设置

- 1.登录Disqus网站注册一个账号（开vpn比较快点）
- 2.点击Setting图标，选择Add disqus to site
- 3.点击Start Using Engage
- 4.设置自己的Disqus的URL

![](../assets/images/Snip20171024_30.png)


- 5.设置根目录下_config.yml文件的disqus的URL

	```
	# Comment
	comment:
    	disqus: joeliu
	
	```

## 五.主题细节修改
	一切顺利的话，你讲看到下面这个界面。接下来就将网站信息都改成自己的吧。
- 1.修改个人信息
  博客名、描述、跳转链接的修改的主要文件路径是在根目录下的文件：_config.yml
  
- 2.修改背景图片
  头像和背景存放路径：代码仓库根目录->assets->images，直接替换文件就好了，不过要保持文件名一样。
  				
（在编写markdown时使用这些图片可以直接输入如： \!\[](../assets/images/Snip20171024_27.png)  "../ 表示上级目录"）
	
![](../assets/images/Snip20171024_28.png)

## 六.写文章
- 1.存放文章位置

 ![](../assets/images/Snip20171024_29.png)

 > 用Jekyll写博客，一篇文章就是一个文件，所有需要发表的文章都要放在_posts文件夹里。文件的命名要按YYYY-MM-DD-文章标题.markdown这种格式来，后缀使用.md也可以。文件名一旦确定下来，就不要轻易更改，因为Jekyll结合的评论功能，会根据文件名去查找这篇文章的评论内容。同一篇文章只是更改了文件名，如下：

![](../assets/images/Snip20171024_31.png)

- 2.写文章工具 : 推荐用Mou吧
- 3.书写格式

  > 在文章的开头，我们需要先设置头信息。头信息需要根据YAML的格式写在两行三虚线之间。
  
  ```
	---
	layout: post
	title: 这个是标题
	date: 2016-04-16 11:11:11.000000000 +09:00
	tags: Jekyll Github
	---
 		
  ```
  > layout：指文章布局的类型，需要使用指定的模版文件，模版文件放在_layouts目录下，暂时用post.html。page.html模板比<br>post.html模板少了更早的文章和评论模块。有能力的也可以自己写一个文章页面的布局模板文件。<br>
title：文章的标题。<br>
date：发布文章的时间。（后面的一串零零零好像不能省）<br>
tags：标签，一篇文章可以设置多个标签，使用空格分割。

	---
	
	> 基本上一篇文章只要用到以上一些信息就可以了，当然还有其它的变量可以设置，具体用法可以在Jekyll网站上查看。<br>
	终于可以开始写文章了，一劳永逸，以后再也不用关心那些破事了，将心思放在写文章上。<br>
	为了写出漂亮排版的文章，需要多注意下Markdown的语法说明，第一次运行Mou软件的时候，会有弹出使用语法说明，如果不小心关了，也可以在软件的菜单栏里找到 Help -> Mou Help :
	
	![](../assets/images/Snip20171024_32.png)
	
  > 在写文章的时候，在本地仓库目录下终端执行 jekyll serve，开启Jekyll本地环境，可以一边写博文，一边刷新http://127.0.0.1:4000/地址查看实时效果。写完提交git，就完事啦。