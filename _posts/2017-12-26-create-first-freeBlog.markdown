---
layout: post
title: "从零开始创建一个无需服务器和域名的博客（让你只专注于你的文章）"
date: 2017-12-16 14:29:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img:  # Add image post (optional)
---
> ## 通过阅读这篇博客，你只需要一次性搭建好博客，后期只需要专注于文章的内容。而且可以在本地进行一边修改一边预览，最后同步到你的博客中。博主最后会把同步你博客的内容简化成简单的几条命令。 ##

### 我会把博客中一些名词的解释放在单独的链接，如果有不懂或者想要了解更加详细的信息，你可以点击这些文字。
###
### 博主会尽量做到简洁明了，清晰到每一步，即使你不懂计算机也毫无关系(*^▽^*) ###
<br/>

### 版权声明：欢迎分享，转载请注明出处[www.lframe.cn](http://www.lframe.cn) ###
![Macbook]({{site.baseurl}}/assets/img/biaoqing1.png)
# **博客目录** #

* [1.______注册github账户](#1)
* [2.安装Git环境)(基于Windows)](#2)
* [3.使用SSH加密](#3)
* [4.在github中添加私钥](#4)
* [5.使用github Page搭建博客](#5)
* [6.挑选模板](#6)
* [7.在本地写博客，并上传到github上](#7)
* [8.安装jekyll本地环境(基于window环境)](#8)
* [9.直接fork博主的项目（推荐）](#9)
* [10.编写博客（以fork博主的项目为例，其他的类似）](#10)
* [11.推送博客到远程仓库上（这样别人就可以通过网址访问你的博客了）](#11)
* [12.使用git push推送可能遇到的问题](#12)
* [13.修改配置信息](#13)
* [14.编写markdown文章推荐使用MarkdownPad 2（基于window环境）](#14)
* [15.总结](#15)




<h2 id="1">注册github账户</h2>

>github是什么？ [github](https://baike.baidu.com/item/github/10145341?fr=aladdin "github")为我们提供了免费的服务器，而我们的博客基于github Page直接从 [github](https://baike.baidu.com/item/github/10145341?fr=aladdin "github")存储库托管。你只需要编辑、推送，并且你的修改是实时的。当然啦，你不必紧张，博主会清晰地教你每一步的。
#### 首先你需要注册一个github账户。 ####
[传送门(github官网)](https://github.com/join?source=header-home)，你只需要按照上面的信息填好即可。
在注册github账户的时候需要注意：

- username你尽量填写你熟知的，如果你自己没有注册域名的话，你博客的地址最后将是www.{username}.github.io



<h2 id="2">安装Git环境（基于windows）</h2>
1. <br/>
你需要下载一个Git，[下载地址](http://gitforwindows.org/)<br/>
Linux和Mac上的安装参考[git官方文档](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)。<br/>
下载完成后，找到Git Bash<br/>
![](https://i.imgur.com/iHCNbMv.png)

2.当我们第一次安装完Git后，第一件要做的事情就是设置用户名称和email地址，这一步非常重要，因为我们每次的git提交（即把信息提交到远程仓库github上时都会使用该信息）。
> Git为我们提供了一个git config 命令，专门用来配置或读取相应的工作环境变量。一般我们直接使用如下的全局设置：(上面添写**username**，下面填写邮箱（最好写你注册github账户的邮箱）)<br>
![](https://i.imgur.com/yBEBuYw.png)







<h2 id="3">使用SSH加密</h2>

1：我们在写好文章以后，需要上传到我们的博客上（也就是github仓库上），而我们的本地使用的是Git仓库，在本地Git仓库和github仓库之间的传输需要SSH加密，所以需要设置秘钥。
2：接下来在我们刚才打开的Bash shell中键入如下命令：</br>
`ssh-keygen  -t rsa –C “youremail@example.com`  //用你自己的邮箱替换即可。<br/>
不用管一直回车直到命令完成，完成后如下图：
![](https://i.imgur.com/QyKzut9.png)
3：上图中第二个红线中（对应我们计算机的C:\Users\Administrator\.ssh目录），该目录里面有一个id_rsa.pub文件,用记事本打开。里面就是我们的公钥，上面的那个id_rsa是私钥。公钥可以公开，而私钥不可以公开。具体可以看[这个](http://blog.csdn.net/left_la/article/details/41678935)。SSH看这个[SSH详细介绍](https://baike.baidu.com/item/ssh/10407?fr=aladdin).



<h2 id="4">在github中添加私钥</h2>
1:首先登录你刚刚注册的github，依照下图：
点击你的头像，进入如下界面，依图点击红线部分![](https://i.imgur.com/Ppk1Axj.png)


点击SSH and GPG keys<br/>

![](https://i.imgur.com/M0hhxDA.png)

然后点击右上角的NEW SSH key,然后把我们刚才用记事本打开的id_rsa.pub的内容复制到key中即可。
![](https://i.imgur.com/Stvkvqb.png)
点击 Add SSH key.
至此SSH的配置全部搞完了。


<h2 id="5">使用github Page搭建博客</h2>



1. 一种是学习jekyll教程和网页的设计，自定义自己的风格。这是[jekyll的学习地址](https://www.jekyll.com.cn/).有兴趣的同学可以搞一下。
2. 另一种方式是使用模板，直接fork别人的项目。
3. 直接通过[jekyll theme](http://jekyllthemes.org/)  下载主体，然后直接下载到本地。再通过本地调试后再上传到github上。

#### 这里博主只介绍后两种，有兴趣的同学可以挑战下第一种方式 ####


<h2 id="6">挑选模板</h2>
[github的jekyll项目](https://github.com/jekyll/jekyll/wiki/sites)给出了大量的模板。选择一个，如下图所示。<br/>![](https://i.imgur.com/SqIbMrH.png)<br/>

然后点击Fork到你的仓库中。
![](https://i.imgur.com/TJvvt4u.png)<br/>

最后修改一下仓库的名字。将仓库的名字改为`{你的github的username（就是你登录时使用的username，不是邮箱）}.github.io`，然后点击Rename，如下所示。
![](https://i.imgur.com/hbWCS1v.png)<br>
接下来你就可以用你`{username}.github.io`访问你的网站了。（username解释同上）。
<h2>绑定域名（不想映射自己域名的可以跳过）</h2>
打开github，在你刚才fork的项目下中找到CNAME文件夹。打开它，
![](https://i.imgur.com/2KfkLN5.png)
编辑它的内容，比如博主申请的域名是lframe.cn，则你只需要把'lframe.cn'添加到该文件中，然后点击下面的Commit changes。
等一会，你就可以使用你的域名访问你的博客了。



<h2 id="7">在本地写博客，并上传到github上</h2>

1. 首先我们打开Git Bash，切换到一个磁盘`cd g:`（博主这里切换到g盘，你可以根据自己的情况把相应的字母替换为你的盘符`mkdir blog`(比如你想添加到e盘，就把g改为e)），然后创建一个目录。然后进入该目录。`cd blog`![](https://i.imgur.com/E0vgry7.png)
2. 然后使用`git init`初始化该目录为一个本地仓库。接着使用'git clone https://github.com/用你的用户名替换不同(即username)/用你的用户名替换即username.github.com.git'。看不懂的使用git clone 后面加上你仓库中点击绿色按钮Clone or download里面的网址。
![](https://i.imgur.com/w1b9Q1Q.png)
![](https://i.imgur.com/yEXSUGu.png)
3.  现在你可以写博客了，打开本地仓库，也就是我们上面对应的G:\blog\shadowdoor.github.com \_posts目录，然后创建一个.md文件，该文件类型就是markdown格式。文件命名严格按照上面的日期格式20xx-mm-nn-name-name.md。（其中月份和日期必须是两位，后面的命名随便）![](https://i.imgur.com/HY1MJvl.png)
图中使用的是MarkdownPad 2编写markdown,你暂时先用记事本打开，编写内容如下：
![](https://i.imgur.com/01v29kQ.png)
<br/>红线部分你可以找该_post目录下的任意同类型文件打开（没有软件的话，就用记事本打开），然后复制"---"和"---"之间的内容，只能改title后面引号的内容，那个是最后文章标题的内容。
红线外边的内容是markdown格式的内容，你可以随便编辑一些内容。然后`ctrl +s`保存了。
然后打开你刚才的Git Bash，使用`cd shadowdoor.github.io`进入你的项目目录，接着使用`git add .`把项目所有改变的内容添加到暂存区内，（听不懂没关系，照着码就行了，博主后面会统一总结的），然后使用`git commit -m "测试博客"`,最后使用 `git push origin master`推送到远程仓库github上。具体的实例如下：
![](https://i.imgur.com/KhRwUj6.png)![](https://i.imgur.com/eqccdU3.png)
出现上面信息，说明提交成功了，现在你访问你博客，会发现多了，一篇博客。
4：下面显示了我们刚才提交的博客：
![](https://i.imgur.com/6Plaavk.png)


> 小伙伴可能会着急这头像和内容都是别人的，那我想弄我自己的怎么办啊？博主最后会为你一一解析。
## 从上面可以发现，如果想看修改后的状态，每次都需要①git add . ②git commit -m "提示信息" ③git push origin master 这三步才能实现，而且还得等一会github Page，然后才能查看我们修改的效果。如果我们只修改一点点，这样是不是太浪费时间了，下面介绍如何搭建本地服务实施预览我们修改后的效果。 ##


<h2 id="8">安装jekyll本地环境(基于window环境)</h2>



 *用Mac和Linux上的小伙伴们参考[这里](http://www.cnblogs.com/daguo/p/4097263.html).** <br/>
1: 下载[Ruby](https://rubyinstaller.org/downloads/)<br/> 
32位计算机下载红线中×86版本，64位计算机下载红线中×64版本，
![Macbook]({{site.baseurl}}/assets/img/ruby.png) <br/>
安装的时候全部选择默认选项，但必须选中下图中的第一个`Add Ruby executables to your PATH`,该选项会自动为你添加Ruby的环境变量。<br/>
![Macbook]({{site.baseurl}}/assets/img/ruby1.png) <br/>

2：安装[RubyGems](https://rubygems.org/pages/download),选择压缩格式zip。
![Macbook]({{site.baseurl}}/assets/img/rubyGem.png)<br/>
下载好以后，解压随便一个文件夹中，博主这里在G盘创建了rubygem中，然后把下载好的RubyGems解压到G盘的rubygem文件夹中，然后在cmd中使用命令行进入该文件夹先输入`g:`回车进入G盘，然后输入`cd rubygem`回车，再输入`cd rubygems-2.7.4`回车，然后键入`ruby setup.rb`回车。
![Macbook]({{site.baseurl}}/assets/img/rubyGem1.png)<br/>
3： 安装jekyll<br/>
在刚才的cmd（命令行窗口([window下常用的cmd命令](https://jingyan.baidu.com/article/c74d6000a78f050f6a595df4.html))）键入`gem install jekyll`，当你键入该命令后，可能会弹出一个窗口，确定即可。<br/>
4:安装jekyll-paginate<br/>
继续在命令行窗口中键入`gem install jekyll-paginate`,等待成功即可。<br/>
5：测试：<br/>
①使用cmd命令进入G盘，然后在键入`jekyll new blog`，其中`blog`可以换成你想用的名字，结果如下所示：<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll.png)<br/>
②然后使用cmd进入该文件夹`cd blog`,接着键入`jekyll serve`，可能会出现端口被占用（jekyll默认使用4000端口），<br/>
 <p id="bug">具体情形如下：</p>
![Macbook]({{site.baseurl}}/assets/img/jekyll1.png)</br>
③接着使用cmd键入` netstat -ano`,下来找到如下图所示的被占用的4000端口的最后面的`3176`（每次启动机器该号可能不一样）<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll2.png)<br/>
④接着键入`tasklist /svc /FI "PID eq 3176"`,该PID服务就会显示出来。<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll3.png)<br/>
⑤然后打开任务管理器(ctrl+alt+delete组合键)打开任务管理器，打开详细信息那一页，选择上面查出的FxService，结束该进程（系统提示会有危险，不用管它，直接结束，不会影响你电脑）。<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll4.png)<br/>
⑥接着使用cmd进入你刚刚通过`jekyll new blogs`创建的博客，再次键入`jekyll serve`，如下所示<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll2.png)<br/>
⑦最后使用浏览器地址栏输入`http://localhost:4000/`，就可以看到jekyll默认提供的博客了。<br/>
![Macbook]({{site.baseurl}}/assets/img/page.png)<br/>
⑧如果想关闭网站，在刚才cmd中键入`Ctrl+C`
![Macbook]({{site.baseurl}}/assets/img/jekyll6.png)<br/>
然后键入`y`回车即可。<br/>
到此，说明你的jekyll环境已安装好了。

<h2 id="9">直接fork博主的项目（推荐）</h2>
> **博主会在自述文件中给出修改你博客的具体方式。以及通过修改源代码修改博客中的一些图标，以及显示方式。以及放图片的位置和在博客中引用图片的方式，当然啦，同学们也可以使用 [图床](https://baike.baidu.com/item/%E5%9B%BE%E5%BA%8A/10721348?fr=aladdin) 。** <br/>
> 同学们也可以在[主题站](http://jekyllthemes.org/)找一些博客主题，但是在本地测试的时候，可能会出现一些版本不兼容等不可控因素，所以，还是建议同学们直接fork博主的项目，避免不必要的麻烦。
[博主的github项目地址](https://github.com/liangFrame/liangFrame.github.io)

进去后，然后点击Fork到你的仓库中。
![](https://i.imgur.com/TJvvt4u.png)<br/>

最后修改一下仓库的名字。将仓库的名字改为`{你的github的username（就是你登录时使用的username，不是邮箱）}.github.io`，然后点击Rename，如下所示。
![](https://i.imgur.com/hbWCS1v.png)<br>
然后使用git clone克隆你的项目到本地，（这里以博主的项目为例和你的类似）具体操作如下：<br/>
博主的项目界面如下，点击右边绿色的按钮`clone or download`，下面有个网址，这个网址是博主的该项目的远程仓库的地址。地址是`https://github.com/liangFrame/liangFrame.github.io.git`。你的地址是这样的`https://github.com/username/username.github.io.git`，**这里的username同上是你的用户名**。
![Macbook]({{site.baseurl}}/assets/img/github.png)<br/>
使用在开始界面打开git Bash,键入`cd g:`切换到g盘，（你只需要更换字母即可切换到你想要的任意盘符）。然后键入`git clone https://github.com/username/username.github.io.git`，**username同上。**Git会从远程仓库把`username.github.io`项目克隆到你的G盘上。如下所示<br/>
![Macbook]({{site.baseurl}}/assets/img/git.png)
<br/>接着使用cmd命令进入该文件夹。先键入`g:`进入g盘，然后键入`cd username.github.io`，**username同上是你的用户名**.
然后使用`jekyll serve`，启动会出现下述问题。
如图片所示。<br/>
![Macbook]({{site.baseurl}}/assets/img/jekyll7.png)
然后使用`bundle install` 。
![Macbook]({{site.baseurl}}/assets/img/jekyll8.png)
再次键入`jekyll serve`。
![Macbook]({{site.baseurl}}/assets/img/jekyll9.png)
关闭的方式以及端口被占用的[解决方式](#bug)。




<h2 id="10">编写博客（以fork博主的项目为例，其他的类似）</h2>
打开你的本地仓库，找到_post文件夹，你需要把你写好的博客放在这个文件夹中，注意文件的类型必须和博主的上面的文件的格式相同，即都是以`.markdown`为后缀的文件，且文件的命名也必须是类似于`2017-12-26-create-first-freeBlog.markdown`，你的文件命名要严格遵循 `年-月-日-名字.markdown` 这样的格式，其中名字可以改为你喜欢的，在博客的内容中必须包含如下内容（你可以仓库的_post文件夹中打开任意一篇博客上面都必须有该信息）**其中，title后面双引号中的内容是你博客的标题（你可以修改），date后面是日期，你可以修改也可以不修改，但格式必须一样。其他最好不要动。**<br/>
**---
layout: post
title: "MarkdownPad 2的常用快捷键"
date: 2017-04-06 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img:  # Add image post (optional)
---**
<br/>在该内容下面你可以任意编辑，推荐写(markdown)，当然你也可以使用HTML的一些标签。<br/>
在为博客添加图的时候，你可以使用图床，但也可以使用博主目前使用的方式（估计以后博主也会转向使用图床）。
你只需要找到assets文件夹，然后打开img文件夹，然后把你要用的图片放到该文件夹中，然后再博客中引用的方式是输入如下`![Macbook]({{site.baseurl}}/assets/img/name.png)`，`name`就是你图片的名字，`.png`是你图片的格式。






<h2 id="11">推送博客到远程仓库上（这样别人就可以通过网址访问你的博客了）</h2>
打开git Bash，通过`cd {你项目的根目录}`，然后键入`git add .`，（代表把该项目所有改变的内容保存到暂存区内），接着键入`git commit -m "提交信息"`，（代表把该项目保存到本地仓库），最后键入`git push origin master`，推送到远程仓库了。（等几分钟，可能时间更长一点，github Page服务器就会刷新），你再次访问你的博客，内容已经更新了。

<h2 id="12">使用git push推送可能遇到的问题</h2>
①你可能会遇到如下图所示的问题：
![Macbook]({{site.baseurl}}/assets/img/blog.png)<br/>
你只需要改一下该文件的格式改为UTF-8，如果出现其他编码错误的话，你把文件格式改为相应格式即可。具体如下图所示：
![Macbook]({{site.baseurl}}/assets/img/blog1.png)<br/>

②每次重启电脑后，使用jekyll本地服务器端口仍然会被占用，你需要关闭该端口的服务，[解决方式](#bug)。<br/>
③你使用git提交的时候可能会遇到`Your branch and 'origin/master' have diverged, and have 1 and 1 different commits each, respectively`，解决方法：在我的[CSDN博客](http://blog.csdn.net/m0_37884977/article/details/78901668)中查看。<br/>
> **如果还有其他问题的话，可以发我的邮箱`605415633@qq.com`，**。
<h2 id="13">修改配置信息</h2>
> 你直接在项目的根目录的_config.yml文件中修改即可，博主已经把注释写好了，你修改了之后重启本地服务器，就可以看到效果了。更多的修改需要修改源码，博主后续会添加这一部分内容。
<h2 id="14">编写markdown文章推荐使用MarkdownPad 2（基于window环境）</h2>
安装了markdownPad 2不能实现实时预览，[解决方法](https://www.zhihu.com/question/34393386)。
常用快捷键见上篇博客。
<h2 id="15">总结</h2>
到此，你已经搭建好你的博客了。<br/>
你只需要在你本地仓库中中`_post`文件夹中添加你新写的博客即可。<br/>
然后使用git Bash进入你项目的根目录<br/>
然后键入`git add .`,把修改的内容提交到暂存区内<br/>
接着键入`git commit '提示信息'`，把项目提交到本地仓库中。其中提示信息可以修改为你博客做出修改的备注信息。<br>
最后键入`git push origin master`，推送到了远程仓库github上。<br/>
这里以博主的项目为例，博主的项目在F盘的github.liangFrame.io文件夹下，如下图所示：<br/>
![Macbook]({{site.baseurl}}/assets/img/git1.png)<br/>
表明你已经推送成功了。



 