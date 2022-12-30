---
title: 三分钟建站指南（Wordpress）
date: 2018-11-23 22:04:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
现在，只要你有一台服务器，你就可以轻松的搭建起一个自己的网站，即使你和我一样，没有一点编程基础。

这得益于如今众多的开源软件和较为人性化的管理面板，让小白都可以无压力的来搭建个人博客。

所以，如果你有这方面的兴趣，就跟着下面的教程，来搭建自己的网站吧。
<h2>搭建过程</h2>
<h3>第一步：选择服务器和域名</h3>
如果只是用作搭建个人博客的话，<strong>1核1G</strong>的配置就足够，后期如果网站做的好了也可以升级配置。

1核1G这种配置在国外主机服务商处的价格大概是<strong>$5/月</strong>，在国内主机服务商处为<strong>￥30-40/月左右</strong>。

区别在于选择国外主机不需要备案，但选择大陆的主机就得去工信部备案，但两者也都大概在人人都付得起的价位。

关于系统选择，<strong>建议选择CentOS7</strong>，或者也可以根据个人的喜好来。

购买完服务器后最好先去管理界面<strong>放行常用的端口</strong>，<strong>如21,22,80,443,888,3306,8888等</strong>。

关于域名的话，既然都搭建网站了，怎么说也得有一个域名吧。

域名的话可以去<strong>万网</strong><strong>或者腾讯云</strong>注册一个，或者去<strong>Freenom</strong>免费申请一个（.ml等）也可以。

弄好的域名记得将www和@的A记录解析到你的服务器IP上。
<h3>第二步：连接服务器</h3>
购买完服务器后，通常你就会有一个<strong>密钥</strong>或者<strong>root密码</strong>，有了这两项的其中一个，你就可以去使用SSH连接工具连接上你的服务器了。

这里推荐一些比较好用的SSH连接工具：XShell6，PUTTY。

Xshell6表面上为收费软件，但是官网里面有个人/教育选项，是<strong>免费使用</strong>的，在官网填写邮件地址后，下载地址就会发送给你。

<a href="https://www.netsarang.com/zh/all-downloads/?code=622&amp;downloadType=0&amp;licenseType=1" target="_blank" rel="noopener noreferrer">XShell6官网传送门</a>

下面以XShell6为例子做演示。

打开软件后会跳出会话框，点击会话框的左上角<strong>新建</strong>，填入你在主机提供商处得到的IP。

<img class="alignnone size-full wp-image-524" src="https://p.ratodo.com/wp-content/uploads/2018/11/23212412.jpg@!full" alt="" width="671" height="677">

填好之后选择左侧的<strong>用户身份验证</strong>，输入你的<strong>用户名和密码</strong>。

如果是密钥就下拉选择<strong>Public Key</strong>，然后选择你的<strong>密钥文件</strong>和输入<strong>用户名和密码</strong>（如果有）。

<img class="alignnone size-full wp-image-525" src="https://p.ratodo.com/wp-content/uploads/2018/11/23212430.jpg@!full" alt="" width="671" height="677">

首次连接会弹出提示框，选择<strong>接受并保存</strong>即可。
<h3>第三步：安装管理面板</h3>
这里选择的是宝塔Linux面板，目前更新到了6.6版本，基本上该有的功能这个面板都有了。

下面是安装命令，复制粘贴即可。

（CentOS7，不建议6）
<pre class="language-html"><code class="language-html">yum install -y wget &amp;&amp; wget -O install.sh http://download.bt.cn/install/install_6.0.sh &amp;&amp; bash install.sh</code></pre>
（Ubuntu/Deepin）
<pre class="language-html"><code class="language-html">wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh &amp;&amp; sudo bash install.sh</code></pre>
（Debian）
<pre class="language-html"><code class="language-html">wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh &amp;&amp; bash install.sh</code></pre>
过程中会让你手动输入一次y

面板安装完成后会给你后台管理地址和初始用户名密码，复制进浏览器即可登陆后台。

登陆到后台后记得自己在<strong>面板设置</strong>中<strong>修改用户名和密码</strong>。

<img class="alignnone size-full wp-image-460" src="https://p.ratodo.com/wp-content/uploads/2018/11/21134201.jpg@!full" alt="" width="542" height="266">

进入到后台管理后会先让你安装运行环境，这里推荐选择<strong>Nginx1.15+PHP7.1+MySQL5.6</strong>。

PhpMyAdmin和FTP可有可无，看你自己会不会用到了。
<h3>第四步：建立网站</h3>
<strong>点击左侧网站-&gt;添加网站</strong>，填写域名（www或者主域名）并创建数据库。

<img class="alignnone size-full wp-image-526" src="https://p.ratodo.com/wp-content/uploads/2018/11/23214450.jpg@!full" alt="" width="642" height="649">

创建完成后，进入<strong>文件管理</strong>，找到你刚刚创建的网站的根目录，将其中自动生成的四个文件删除。

前往<strong><a href="https://wordpress.org/download/" target="_blank" rel="noopener noreferrer">Wordpress官网</a>下载Wordpress的安装文件</strong>，或者上方<strong>资源下载</strong>也可以下载到。

下载完成后将压缩包上传至网站根目录并解压（将文件夹中的文件全部剪切到网站根目录），如下图所示。

<img class="alignnone size-full wp-image-527" src="https://p.ratodo.com/wp-content/uploads/2018/11/23215408.jpg@!full" alt="" width="1694" height="923">

接下来就可以访问你的域名开始Wordpress配置了。
<h3>第五步：Wordpress配置</h3>
访问你的域名，就会启动Wordpress的安装流程。

<img class="alignnone size-full wp-image-529" src="https://p.ratodo.com/wp-content/uploads/2018/11/23215619.jpg@!full" alt="" width="946" height="729">

<img class="alignnone size-full wp-image-528" src="https://p.ratodo.com/wp-content/uploads/2018/11/23215718.jpg@!full" alt="" width="930" height="609">

正确填写完成后就是填写关于你的<strong>站点名称和后台登陆</strong>信息了。

全部填写完成后，Wordpress安装就结束了。

另外，Wordpress的后台管理网址为<strong>你的域名/wp-admin</strong>

至于Wordpress别的东西就自己摸索吧！还是比较有趣的。
<h2>总结</h2>
总体过程很简单，得益于宝塔面板的一键安装搭建环境，省了许多事情。

Wordpress还有很多高级玩法，等待你自己去发现（虽然我自己都没发现几个

还有就是，你还可以在宝塔面板的<strong>网站设置</strong>里为你的站点开启HTTPS和伪静态（选择wordpress即可，可以自定义网站的文章链接）。

关于SSL证书申请可以看我之前的文章，TLS1.3的开启也是。

祝你建站愉快：D
