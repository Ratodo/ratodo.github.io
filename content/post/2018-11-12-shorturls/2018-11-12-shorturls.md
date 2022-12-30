---
title: 关于启用短域名
date: 2018-11-12 14:29:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>缘由</h2>
最近在折腾完SSL证书这一块后，突发奇想想要搞一个短域名玩玩。

<del>当然，什么太好的域名我也买不起，就在Namecheap上新购了一个<strong>ybgx.me</strong>。</del>

<del>单单要去记这个域名的话肯定不好记，但是配上我这羞耻的博客名就好记多了。</del>

<del>在GoDaddy上算是以免费的形式得到了一个新的域名，<strong>adwz.net</strong>（a 短网址），这个应该还可以。</del>

<del>原先的域名就留作备用吧，毕竟有都有了。</del>

<del>尽管我的网站并没有什么流量，但是好玩啊（自我安慰中...）</del>
<h2>使用的开源软件</h2>
短域名服务是用<strong>YOURLS</strong>搭建的（没错，又是不需要动脑子的）。

<span data-slate-fragment="JTdCJTIyb2JqZWN0JTIyJTNBJTIyZG9jdW1lbnQlMjIlMkMlMjJkYXRhJTIyJTNBJTdCJTdEJTJDJTIybm9kZXMlMjIlM0ElNUIlN0IlMjJvYmplY3QlMjIlM0ElMjJibG9jayUyMiUyQyUyMnR5cGUlMjIlM0ElMjJjb2RlJTIyJTJDJTIyaXNWb2lkJTIyJTNBZmFsc2UlMkMlMjJkYXRhJTIyJTNBJTdCJTIyc3ludGF4JTIyJTNBJTIydGV4dCUyMiU3RCUyQyUyMm5vZGVzJTIyJTNBJTVCJTdCJTIyb2JqZWN0JTIyJTNBJTIyYmxvY2slMjIlMkMlMjJ0eXBlJTIyJTNBJTIyY29kZS1saW5lJTIyJTJDJTIyaXNWb2lkJTIyJTNBZmFsc2UlMkMlMjJkYXRhJTIyJTNBJTdCJTdEJTJDJTIybm9kZXMlMjIlM0ElNUIlN0IlMjJvYmplY3QlMjIlM0ElMjJ0ZXh0JTIyJTJDJTIybGVhdmVzJTIyJTNBJTVCJTdCJTIyb2JqZWN0JTIyJTNBJTIybGVhZiUyMiUyQyUyMnRleHQlMjIlM0ElMjIlMjAlNUJnaXRodWIlMjBhdXRob3IlM0QlNUMlMjJzb2xzdGljZTIzJTVDJTIyJTIwcHJvamVjdCUzRCU1QyUyMmFyZ29uLXRoZW1lJTVDJTIyJTVEJTVCJTJGZ2l0aHViJTVEJTIyJTJDJTIybWFya3MlMjIlM0ElNUIlNUQlN0QlNUQlN0QlNUQlN0QlNUQlN0QlNUQlN0Q="> [github author="YOURLS" project="YOURLS"][/github]</span>

<a href="http://yourls.org/" target="_blank" rel="noopener noreferrer">进入官网</a>
<h2>安装过程</h2>
首先，进入YOURLS的<a href="https://github.com/YOURLS/YOURLS/releases" target="_blank" rel="noopener noreferrer">Github-Release</a>下载最新的release。

也可以在主导航处点击<strong>资源分享</strong>下载。

如果你是用的<strong>cPanel管理界面</strong>，则可以直接在<strong>应用程序</strong>中找到YOURLS来进行安装，按照安装步骤来就可以完成。

<img class="alignnone size-full wp-image-264" src="https://p.ratodo.com/wp-content/uploads/2018/11/15092339.jpg@!full" alt="" width="1161" height="560" />

如果你是用的是<strong>宝塔Linux面板</strong>之类的管理面板，则需按下面的步骤操作。

首先先要来创建网站。

登录上面板后选择左侧的网站，点击创建站点（需提前将域名解析至此服务器的ip）。

<img class="alignnone size-full wp-image-265" src="https://p.ratodo.com/wp-content/uploads/2018/11/15092746.jpg@!full" alt="" width="640" height="543" />

如图所示配置，一定得创建数据库。

然后进入左侧的文件，选择到我们刚刚创建好的网站目录，将刚刚下载好的最新release上传至网站目录中并解压（记得将YOURLS-xxx文件夹中的文件剪切到根目录，如图所示）。

<img class="alignnone size-full wp-image-266" src="https://p.ratodo.com/wp-content/uploads/2018/11/15093254.jpg@!full" alt="" width="1702" height="815" />

然后进入到/user，<strong>修改config-sample.php为config.php</strong>。

<img class="alignnone size-full wp-image-267" src="https://p.ratodo.com/wp-content/uploads/2018/11/15093453.jpg@!full" alt="" width="1713" height="429" />

<a href="https://github.com/guox/yourls-zh_CN/raw/master/zh_CN.mo">点此下载</a>语言文件，并将其上传至/user/languages，并修改权限为755。

编辑config.php，按下图中的提示填写完你的相应信息（<strong>右键在新标签中打开图片即可查看大图</strong>）。

<img class="alignnone size-full wp-image-268" src="https://p.ratodo.com/wp-content/uploads/2018/11/15093841.jpg@!full" alt="" width="1727" height="846" />

<img class="alignnone size-full wp-image-269" src="https://p.ratodo.com/wp-content/uploads/2018/11/15094321.jpg@!full" alt="" width="1730" height="848" />

设置完成后，打开<strong>你的域名/admin</strong>即可开始使用你的短网址服务了。

<img class="alignnone size-full wp-image-270" src="https://p.ratodo.com/wp-content/uploads/2018/11/15094646.jpg@!full" alt="" width="1007" height="434" />

至于没有安装Linux管理面板的朋友们，可以参考下面的这篇文章。

<a href="http://www.senra.me/self-hosted-url-shortener-series-yourls-powerful-but-need-secondary-development/" target="_blank" rel="noopener noreferrer">自建短链服务系列——YOURLS(需要二次开发的强大程序) | Senraの小窝</a>
<h2>重要的事</h2>
<del>目前全站的链接都配备上了相应的短域名（因为不多，所以我都是一个一个导入的），但是由于<strong>.me域名无法在大陆备案</strong>，而我使用的又是阿里云的服务器，所以<strong>只能通过HTTPS来访问</strong>。</del>

使用Godaddy的虚拟主机服务，在新加坡，避免了备案的问题，但还是开启了全站HTTPS，SSL证书来自Let's Encrypt。

（2018.11.13 23:55更新）目前本网站的所有超链接均已启用了此短网址，如果出现超链接无法跳转的情况还请告知，不胜感激。

（2019.8.23 15:32更新）已弃用短域名服务，正在逐步修改原超链接。
<h2>其它</h2>
目前短域名还只能我自己使用（估计也没有别人需要用这个鬼东西...），我会再继续看一看这个程序的API，如果可以，我会把它的接口给放出来，万一有人会用呢（疯狂自我安慰）。

另外，由于使用的是Godaddy最最最便宜的虚拟主机，连接速度难免会有些。。。都懂的。

但毕竟是一个次要功能，就稍微迁就一下吧。
