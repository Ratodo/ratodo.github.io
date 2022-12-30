---
title: 在Wordpress中启用阿里云OSS作为媒体库
date: 2018-11-15 10:39:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
<span style="font-size: 12pt;">很多人可能都有这种困扰，网站加载速度太慢，而导致加载速度慢的其中一个大原因就是图片加载。</span>

很多站长为了不用在国内备案，选择把服务器放到国外的VPS上，但国外主机往往对国内的用户不太友好，导致用户体验较差。

<span style="font-size: 12pt;">为了改善这种情况，我们可以把Wordpress的媒体库迁移至阿里云OSS，来使用阿里云的加速服务。</span>

<strong>注意：阿里云OSS需付费使用，国内区目前9元/40GB/1年，流量费用另付，详见阿里云OSS官网。</strong>
<h2>准备工具</h2>
阿里云账号及阿里云OSS Bucket，搭建好的Wordpress系统，阿里云Accesskey

下载好aliyun-oss插件，下载地址：<a href="https://github.com/IvanChou/aliyun-oss-support/releases" target="_blank" rel="noopener noreferrer">Github</a>&nbsp;（开发者：IvanChou）

<del>也可以在主导航处点击<strong>资源分享</strong>下载。</del>
<h2>阿里云OSS配置</h2>
登陆OSS控制管理台，找到你创建好的Bucket，若还未创建，点击右上角的新建Bucket（<strong>读写权限设为公有读，标准存储</strong>）。

在概览中你可以看到你的访问地址。

<img class="alignnone size-full wp-image-275" src="https://p.ratodo.com/wp-content/uploads/2018/11/15100830.jpg@!full" alt="" width="955" height="241">

点击上方的文件管理，新建目录<strong>/wp-content/uploads</strong>（为了方便后续设置）

<img class="alignnone size-full wp-image-276" src="https://p.ratodo.com/wp-content/uploads/2018/11/15101021.jpg@!full" alt="" width="1123" height="314">

选择上方的基础设置，拉到最下方设置<strong>镜像回源</strong>。

<img class="alignnone size-full wp-image-277" src="https://p.ratodo.com/wp-content/uploads/2018/11/15101211.jpg@!full" alt="" width="762" height="892">

<strong>文件名前缀是wp-content/uploads/，回源地址是http(s)://你的网站。</strong>

接下来就可以进行插件的配置了。
<h2>安装插件并配置</h2>
在Wordpress管理界面选择插件-&gt;安装插件-&gt;上传插件，找到下载好的插件并进行安装启用。

在Setting-&gt;阿里云 OSS中进行配置，如下图所示。

<img class="alignnone size-full wp-image-278" src="https://p.ratodo.com/wp-content/uploads/2018/11/15102041.jpg@!full" alt="" width="908" height="907">

一切设置好后点击保存配置就大功告成啦。
<h2>附加功能的设置</h2>
<h3>图片预设样式</h3>
点击右面的<strong>下载样式配置文件</strong>，会跳出来新的窗口，是一个txt文件，可能不会自动下载，把网址粘贴到下载工具中下载下来。

然后回到<strong>OSS管理控制台</strong>，选择<strong>图片处理-&gt;导入样式</strong>，选择下载的txt文件将其导入即可。

如果想要图片水印的话可以先上传水印文件到OSS存储空间，然后编辑<strong>full规则</strong>，按下图提示配置。

（位置，大小，透明度看个人喜好，水印图路径为OSS的文件路径，可在文件管理中点击预览查询到<span style="text-indent: 0em;">）</span>

<img class="alignnone size-full wp-image-279" src="https://p.ratodo.com/wp-content/uploads/2018/11/15102925.jpg@!full" alt="" width="960" height="887">
<h3>原图保护</h3>
在图片处理中，点击访问设置开启原图保护，按下图配置。

<span style="font-size: 12pt;">（<strong>不建议勾选*<del>且强烈建议将站点图标的格式转换为ico再上传设置，否则无法显示站点图标！</del></strong></span><span style="font-size: 12pt;"><strong>下面有讲到解决办法</strong>）</span>

<img class="alignnone size-full wp-image-280" src="https://p.ratodo.com/wp-content/uploads/2018/11/15103452.jpg@!full" alt="" width="680" height="887">
<h3>高级选项</h3>
在插件设置最下方选择<strong>更多选项</strong>，即可打开高级选项。

上面的站点图标因为开了原图显示而无法加载的解决办法如下：

将你要上传的站点图标更改名称，例如favicon，

再在<strong>需要排除的文件</strong>这一选项中填入你更改后的名称，即可让图片不经过OSS直接加载。

如下图所示。

<img class="alignnone size-full wp-image-429" src="https://p.ratodo.com/wp-content/uploads/2018/11/20133452.jpg@!full" alt="" width="618" height="274">

<strong>注意：这样操作会导致所有带有favicon的图片全部绕过OSS直接加载，建议选择一个不常用到的名称。</strong>
<h2>总结</h2>
配置工作到此就完成了，如果在大陆有备案并且有需要的朋友还可以开启CDN加速，在域名管理中即可设置。

<img class="alignnone size-full wp-image-281" src="https://p.ratodo.com/wp-content/uploads/2018/11/15103646.jpg@!full" alt="" width="1190" height="274">

用上了阿里云全家桶，感觉支付宝空空的。

还是老样子，毕竟我很多操作还不熟练，如果哪儿又出现了问题且恰好被你给发现了，还麻烦告知我，感谢！
