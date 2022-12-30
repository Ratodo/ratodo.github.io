---
title: 目前使用的一些服务
date: 2020-02-12 22:44:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
搭建网站，最简单的也就是需要一个服务器加一个域名，但肯定不仅仅局限于此，使用CDN全站加速，添加SSL证书，一点一点小小改进。

现在稍微说一下目前我在使用的一些服务，其中有公益性的，也有商业性的，但他们或多或少都会我这个小破网站变得更好一点。
<h2><a href="https://promotion.aliyun.com/ntms/campus2017.html" target="_blank" rel="noopener noreferrer">阿里云云翼计划</a></h2>
最先说的一定是服务器。这是阿里云针对22岁以下的“年轻人”所提供的一项服务，大概10元/月你可以选择1核2G的轻量应用服务器或者ECS服务器。

相对于国内服务器几十上百一个月的费用来说，阿里云的这个服务器确确实实是给我打开了网站的大门。

<img class="aligncenter wp-image-9247 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/13682.png@!full" alt="" width="1261" height="413" />
<h2><a href="https://cloud.tencent.com/product/cns" target="_blank" rel="noopener noreferrer">腾讯云&amp;DNSPOD</a></h2>
在使用了百度云加速，Cloudflare之后，决定使用腾讯云解析，不仅仅是因为可以支持CNAME和MX同时解析，可以支持小程序更改解析记录也是一大优点，目前现在个人专业版9元/年，也是很划算，推荐，<a href="https://www.dnspod.cn/promo/domainscarnival?promo_code=JLLWKU11729&amp;source=sharelink&amp;from=link" target="_blank" rel="noopener noreferrer">活动地址</a>。此外，目前的.com域名也是注册在腾讯云。

<img class="aligncenter wp-image-9249 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/13352.png@!full" alt="" width="1283" height="390" />
<h2><a href="https://www.upyun.com/league" target="_blank" rel="noopener noreferrer">又拍云加速</a></h2>
之前也介绍过又拍云联盟的相关信息，在网站上添加又拍云的logo标志，即可得到约80元的又拍云代金券，用作个人博客网站的全站CDN加速和其他一些内容来说很足够了，目前应该好多个人站长都在用，就好像我这种小小小小站的站长。

<img class="aligncenter wp-image-9250 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/17812.png@!full" alt="" width="913" height="425" />
<h2><a href="https://su.baidu.com" target="_blank" rel="noopener noreferrer">百度云加速</a>&amp;<a href="https://www.cloudflare.com" target="_blank" rel="noopener noreferrer">Cloudflare</a></h2>
百度云加速在海外节点方面与Cloudflare合作，所以也算是间接的使用了Cloudflare的服务，使用百度云加速主要就是使用其海外节点。因为百度云加速的接入方式与一般的CDN服务商不同，所以也用来做一些CNAME跳转的CDN加速，顺带使用HTTPS访问。

<img class="aligncenter size-full wp-image-9759" src="https://p.ratodo.com/wp-content/uploads/2020/02/23837.png@!full" alt="" width="1300" height="560" />

<img class="aligncenter wp-image-9255 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/11442.png@!full" alt="" width="1310" height="433" />
<h2><a href="https://zeit.co" target="_blank" rel="noopener noreferrer">ZEIT</a></h2>
使用这个服务来做一些静态内容的发布，不用占用服务器空间，完全免费，并且可以通过Github很方便的更改源码。

<img class="aligncenter size-full wp-image-9760" src="https://p.ratodo.com/wp-content/uploads/2020/02/25607.png@!full" alt="" width="1331" height="723" />
<h2><a href="https://letsencrypt.org" target="_blank" rel="noopener noreferrer">Let's Encrypt</a></h2>
非常非常知名的公益性SSL证书项目，毫不夸张的说，很大程度上推动了整个互联网HTTPS化的进程。

因为使用了CDN的缘故，没办法使用acme或者certbot来自动更新证书，所以是托管在又拍云上，由又拍云自动续期。

<img class="aligncenter wp-image-9251 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/19922.png@!full" alt="" width="1114" height="469" />
<h2><a href="https://mail.yandex.com/" target="_blank" rel="noopener noreferrer">Yandex Connect</a></h2>
之所以没有使用国内的一些邮件系统，主要还是因为国内的限制有点大，前后使用过阿里云企业邮箱，腾讯企业邮，网易企业邮箱，都不是很满意。

在网上搜了一圈之后决定使用俄罗斯知名搜索引擎Yandex提供的域名邮箱服务，目前使用感觉良好，没有什么问题。

<img class="aligncenter wp-image-9254 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/19792.png@!full" alt="" width="1815" height="720" />
<h2><a href="https://www.nakedssl.com" target="_blank" rel="noopener noreferrer">NakedSSL</a></h2>
这个网站是用来做根域名至www域名的301跳转，使用很方便并且带有SSL证书，虽然在宝塔上面设置也很方便就是了。

<img class="aligncenter size-full wp-image-9761" src="https://p.ratodo.com/wp-content/uploads/2020/02/23557.png@!full" alt="" width="1672" height="870" />
<h2><a href="https://www.bt.cn" target="_blank" rel="noopener noreferrer">宝塔面板</a></h2>
可视化Linux后台管理面板，可以一键安装LNMP(LAMP)，搭建网站也很简单，对我这种人来说，省去了很多搜代码的功夫 (´・ω・`)，强烈推荐还在门外没进来的人使用面板来搭建第一个网站。

<img class="aligncenter wp-image-9252 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/16332.png@!full" alt="" width="1120" height="435" />
<h2><a href="https://www.wordpress.org" target="_blank" rel="noopener noreferrer">WordPress</a></h2>
知名的博客系统，简单易上手，但是很明显的耗用资源比较多。其中我最喜欢的就是这套<a href="https://www.skyarea.cn" target="_blank" rel="noopener noreferrer">Keith</a><a href="https://www.skyarea.cn" target="_blank" rel="noopener noreferrer">大佬</a>二次开发的ASky主题了，简洁好看，等阿里云服务器无法续费了之后，考虑转到Typecho博客系统。

<img class="aligncenter wp-image-9253 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/02/19062.png@!full" alt="" width="1082" height="498" />
<h2>最后</h2>
使用的服务大概就是这么多，以后想起还会慢慢补充，感谢提供这么多优秀的服务与内容。
