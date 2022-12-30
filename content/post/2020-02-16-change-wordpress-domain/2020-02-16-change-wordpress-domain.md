---
title: 更改Wordpress站点域名的方案
date: 2020-02-16 16:19:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
由于CNAME和MX记录的冲突问题的存在，并且一直未能解决，所以决定更换网站的主域名，改用www二级域来作为网站域名。

下面简单说一下在解决记录冲突过程中的一些操作和更改wordpress站点域名的方法。
<h2>CNAME和MX记录冲突</h2>
在一开始建站的时候，并没有想到以后会用到域名邮箱的情况，也不了解CNAME解析记录和MX解析记录的冲突，所以就将站点搭建在了裸域上。
<h3>CLOUDXNS解析</h3>
18年的时候写过一篇使用CLOUDXNS里的LINK记录来解决CNAME和MX记录冲突的问题，使用LINK来指向一个二级域名，在将二级域名CNAME到CDN提供的地址上，从而解决了冲突问题。但是在别家的DNS解析服务商没有这个功能，并且CLOUDXNS已经停止了对个人的免费服务，所以这个方法现在已经失效了。

<img class="aligncenter size-full wp-image-9301" src="https://p.ratodo.com/wp-content/uploads/2020/02/15776.png@!full" alt="" width="784" height="277" />
<h3>百度云加速</h3>
这个和使用Cloudflare的DNS+CDN服务一样，使用百度云的DNS解析服务，同时使用其CDN服务，添加A解析记录即可实现CDN加速，所以也就不存在CNAME冲突问题，不失为一种很好的解决方案。但是其他CDN服务商基本都没有提供此类服务，并且百度云的国内加速节点数量和质量都很一般，CDN功能也不太全，好处应该也就是这个和免费了吧。

<img class="aligncenter size-full wp-image-9302" src="https://p.ratodo.com/wp-content/uploads/2020/02/17436.png@!full" alt="" width="1263" height="550" />
<h3>Cloudflare解析</h3>
Cloudflare在检测到你同时解析CNAME和MX的时候，会启用CNAME Flattening，由Cloudflare来解析CNAME的A值，返回给DNS解析请求。在我使用的过程中，出现了很大的问题，Cloudflare对于全网只会返回一个它所检测的最佳节点，不知道是不是我的个例，在我使用又拍云和阿里云CDN服务的时候都是如此，这样没能达到CDN的效果，所以放弃了这种解决方式。

<img class="aligncenter size-full wp-image-9305" src="https://p.ratodo.com/wp-content/uploads/2020/02/19206.png@!full" alt="" width="1024" height="212" />
<h3>DNSPOD解析</h3>
DNSPOD支持CNAME和MX记录一起设置，但是在使用过程中也发现了不少问题，比如邮件延迟很大，小概率丢件，影响了使用体验。在开启CNAME加速的情况下，根域名CNAME到二级域名，再用二级域名CNAME到CDN提供的地址上，还是会偶尔出现MX解析记录不生效的问题。

关于我提到的问题，大家可以自己去尝试一下，我所使用的邮件系统是Yandex Connect，估计换成腾讯自家的会好很多？还有待验证。

<img class="aligncenter size-full wp-image-9303" src="https://p.ratodo.com/wp-content/uploads/2020/02/10316.png@!full" alt="" width="1054" height="417" />
<h2>更改Wordpress站点URL</h2>
既然上述几种方案都没解决记录冲突问题，最后就只能更改网站地址了。在更改之前最好先去掉CDN加速，将@和www都以A记录解析到服务器ip上。

首先先安装插件<strong>Velvet Blues Update URLs</strong>，安装完成之后来修改文件。

<img class="aligncenter size-full wp-image-9310" src="https://p.ratodo.com/wp-content/uploads/2020/02/15946.png@!full" alt="" width="560" height="237" />

编辑wp-config.php文件，这个文件就在根目录下，很容易找到，然后在适当的位置插入下面这段字符：
<pre class="language-css"><code class="language-css">define(‘RELOCATE’,true);</code></pre>
保存之后就可以登录wordpress后台来更改你的WordpressURL和站点URL（设置=&gt;常规），更改完成后会让你重新进入后台。

重新登陆之后打开Update URLs（工具=&gt;Update URLs），填写你的旧URL和新URL，勾选全部选项，Update URLs NOW。

<img class="aligncenter size-full wp-image-9309" src="https://p.ratodo.com/wp-content/uploads/2020/02/18246.png@!full" alt="" width="940" height="470" />

全部修改完毕后，回到wp-config.php，删除掉刚刚添加的代码，<strong>一定要删除</strong>！
<h3>坑</h3>
讲一下在这过程中遇到的坑，一个是最近wordpress服务器好像有问题，插件不太好下载，这时候你就可以前往插件的发布地址来下载，然后上传到服务器来安装插件，再一个是我在宝塔面板中开启了防盗链，所以一开始更改域名之后导致我css,js,jpg,png等许多东西404，如果你也有类似的设置的话，记得关掉，或者添加目标域名。
