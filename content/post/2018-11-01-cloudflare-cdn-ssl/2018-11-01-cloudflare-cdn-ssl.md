---
title: 使用Cloudflare免费开启全球加速和HTTPS
date: 2018-11-01 11:41:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
Cloudflare是一家知名的全球科技公司，使用他们的服务主要可以让你的网站加载速度更快（针对国外而言），网站安全性更高等等。

虽然Cloudflare提供了免费全球加速，但是在中国大陆的连接速度远远没有那么好，所以还是<strong>不太推荐</strong>主要使用人群为大陆的网站使用他们的CDN加速。

如果你有<strong>中国大陆的ICP备案又不需要HTTPS</strong>的话，可以选择<a href="https://su.baidu.com/" target="_blank" rel="noopener noreferrer">百度云加速</a>，百度云加速国内用的百度节点，国外用的Cloudflare节点。

<strong>百度云加速</strong>的连接速度如下：

<img class="alignnone size-full wp-image-179" src="https://p.ratodo.com/wp-content/uploads/2018/11/DR6CKQ0IJCS2PU6_JM.png" alt="" width="1205" height="780">
<h2>准备环境</h2>
域名，服务器，Cloudflare账号
<h3>Step1</h3>
首先登陆到<a href="https://www.cloudflare.com/" target="_blank" rel="noopener noreferrer">Cloudflare网站</a>，选择左上角的<strong>Log In</strong>进行登陆，如果没有账号的可以在这儿选择<strong>Sign Up</strong>进行账号注册。

<img class="alignnone size-full wp-image-112" src="https://p.ratodo.com/wp-content/uploads/2018/11/01110134.png" alt="" width="1245" height="498">

Cloudflare官网并不提供简体中文服务，所以只能使用英文进行操作。

登录过程中如果你的网络环境不是很安全，Cloudflare可能会要求你进行验证码验证，提供方是Google，所以你需要科学上网才能加载出验证码。
<h3>Step2</h3>
登陆之后你的界面如下所示，点击<strong>+Add Site</strong>进行你的网站添加。

<img class="alignnone size-full wp-image-114" src="https://p.ratodo.com/wp-content/uploads/2018/11/01110559.png" alt="" width="1076" height="521">

输入你的网站后点击<strong>Add Site</strong>进行下一步。

<img class="alignnone size-full wp-image-115" src="https://p.ratodo.com/wp-content/uploads/2018/11/01110756.png" alt="" width="902" height="426">

接着点击<strong>Next</strong>进行到下一步。

<strong>Select A</strong> Plan这一步选择最左边的<strong>Free</strong>即可。

<img class="alignnone size-full wp-image-116" src="https://p.ratodo.com/wp-content/uploads/2018/11/01110911.png" alt="" width="1201" height="554">

在弹出的窗口中选择<strong>Confirm</strong>继续。（大意是一个账号只能使用一个免费的套餐）
<h3>Step3</h3>
<img class="alignnone size-full wp-image-118" src="https://p.ratodo.com/wp-content/uploads/2018/11/01111408.png" alt="" width="1072" height="1018">

如上图所示，云朵亮了即表示流量经过Cloudflare加速，灰了即表示不经过加速。

另外，如果你本身就在域名服务商初解析了IP，这儿会直接显示出来你的解析IP，点击<strong>Coutinue</strong>进入下一步。
<h3>Step4</h3>
这一步就需要你到域名服务商处进行操作了，到域名服务商处改变你的域名服务器，将其更改为Cloudflare提供的服务器即可。

<img class="alignnone size-full wp-image-119" src="https://p.ratodo.com/wp-content/uploads/2018/11/01111730.png" alt="" width="1051" height="752">

Freenom示例如下，在<strong>Management Tools</strong>里选择<strong>Nameservers</strong>，进行修改。

<img class="alignnone size-full wp-image-120" src="https://p.ratodo.com/wp-content/uploads/2018/11/01112007.png" alt="" width="1145" height="702">

修改完成后等待一会，因为修改域名服务器有延迟时间，等待生效即可。
<h3>Step5</h3>
更改生效后即可在Cloudflare管理你的网站加速了。

推荐开启以下功能：

<strong>Speed栏</strong>

<img class="alignnone size-full wp-image-125" src="https://p.ratodo.com/wp-content/uploads/2018/11/01113323.png" alt="" width="1074" height="489">

<img class="alignnone size-full wp-image-122" src="https://p.ratodo.com/wp-content/uploads/2018/11/01112504.png" alt="" width="1025" height="334">
<h3>Step6</h3>
关于开启网站HTTPS，首先先点击上方的<strong>Crypto</strong>，你会发现默认它就帮你开启了HTTPS，SSL证书默认是Cloudflare提供的<strong>Flexible类型</strong>，这里你可以手动选择更改为<strong>Full类型</strong>。

推荐的设置如下所示：

<img class="alignnone size-full wp-image-123" src="https://p.ratodo.com/wp-content/uploads/2018/11/01112941.png" alt="" width="1024" height="825">

<strong>HSTS</strong>设置

点击<strong>Enable</strong>后划到最下方选择<strong>I Understand</strong>，选择<strong>Next</strong>。

推荐设置如下：

<img class="alignnone size-full wp-image-124" src="https://p.ratodo.com/wp-content/uploads/2018/11/01113209.png" alt="" width="638" height="982">

然后点击<strong>Save</strong>保存即可。
<h2>连接速度测试</h2>
一切都设置好之后我使用了<a href="https://www.ipip.net/" target="_blank" rel="noopener noreferrer">IPIP.NET</a>提供的Ping查询进行网站连接速度测试。

测试结果如下图

<img class="alignnone size-full wp-image-126" src="https://p.ratodo.com/wp-content/uploads/2018/11/01113744.png" alt="" width="1199" height="779">

可以看出来Cloudflare与国内的连接普遍很差，所以如果不是很需要海外连接加速，使用cloudflare也不是很必要。
