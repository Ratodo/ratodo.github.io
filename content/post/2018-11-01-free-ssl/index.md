---
title: 关于国内外那些免费SSL证书
date: 2018-11-01 00:29:00 +0800
author: Ratodo
comments: true
categories:
    - 建站笔记
slug: free-ssl
image: https://u.ratodo.com/blog/2018/free-ssl-0.jpg!full
---

## 前言

现在免费证书有很多选择，但主要可以分为四大类，国内云服务厂商免费证书，国外证书品牌免费体验，Cloudflare免费证书以及Let's Encrypt免费证书。

下面大概介绍一下四种证书的类型，申请方式以及证书的部署。

## 国内云厂商免费证书

在云计算的大趋势下，国内三巨头BAT均推出了自家的云服务系统，SSL证书也包含在内，阿里云，百度云，腾讯云均推出了为其一年的免费证书。

### TrustOcean

（2020.2.16更新）经评论区pinwen大佬提醒，申请入口被转移到了TrustOcean首页，[传送门在此](https://console.trustocean.com/certificate/create/85)，登陆账号后直接点击左侧链接即可创建订单。

[Trustocean官网](https://www.trustocean.com)，下图为免费SSL的申请入口。

![Pic1](https://u.ratodo.com/blog/2018/free-ssl-1.png!full)

创建订单界面如下，可选1月或3月有效期，支持同时下单100本，最高**支持100条域名**，比之前250条少，但也绝对够用。

![Pic2](https://u.ratodo.com/blog/2018/free-ssl-2.png!full)

（2020.2.12更新）目前此款证书官网未发现申请入口，可能已经不再支持申请。

（11.5更新）最近发现一个还不错的DV证书，一个证书最高支持保护**250**个域名**（划重点：包含泛域名！！！）**，简直就是拥有多个域名朋友的福音啊！

![Pic3](https://u.ratodo.com/blog/2018/free-ssl-3.png!full)

看了一下提供方是TrustOcean，根证书是由COMODO（USERTrust）提供，有效期三个月，目前还不知道可不可以自动续期，这个SSL也是他们最近才开始做的项目，**自动化申请时间可能较长，可发工单申请加速处理**。官方已优化好，申请过程很流畅。

申请地址：[环洋诚信™-雁雀云服务](https://console.trustocean.com/cart.php)

### [阿里云](https://common-buy.aliyun.com/?spm=5176.7968328.1120760.1.3a8e1232TNRm7l&amp;commodityCode=cas#/buy)

进入阿里云管理控制台，点击左侧的域名，即可找到SSL证书管理控制台，选择购买证书。

先点击Symantec，再点击增强型OV SSL，你就会发现多出来一个免费版DV SSL。

如果你使用的是阿里云的云解析，就可以实现一键DNS验证，无需其它繁琐的步骤。

下图即为申请成功的SSL证书。

![Pic4](https://u.ratodo.com/blog/2018/free-ssl-4.png!full)

通过下载下来的证书我们可以看见证书的颁发者为Encryption Everywhere。

![Pic5](https://u.ratodo.com/blog/2018/free-ssl-5.png!full)

### [百度云](https://login.bce.baidu.com/?account=&amp;redirect=http%3A%2F%2Fconsole.bce.baidu.com%2Fcas%2F%3F_%3D1542123500103#/cas/apply/create)

和阿里云一样，百度云提供的一年期SSL证书也是标称来自Symantec。

![Pic6](https://u.ratodo.com/blog/2018/free-ssl-6.png!full)

购买成功后，百度云提供了DNS验证和文件验证两种方式，鉴于DNS验证需要等待一段时间，我选择了较为简单快捷的文件验证。

文件部署好后百度云会自动检测，检测完成后即下发证书。

此处提示，点击下载证书的时候，如果你用的是Chrome，就会被截拦弹出窗口，请主动放行。

![Pic7](https://u.ratodo.com/blog/2018/free-ssl-7.png!full)

下载完成后查看颁发者信息，可看出颁发者为TrustAsia。

![Pic8](https://u.ratodo.com/blog/2018/free-ssl-8.png!full)

### [腾讯云](https://buy.cloud.tencent.com/ssl?fromSource=ssl&amp;from=qcloudHpHeaderSsl)

腾讯云直接标注了证书由TrustAsia颁发，使用Symantec根证书。

![Pic9](https://u.ratodo.com/blog/2018/free-ssl-9.png!full)

过程都是大同小异，就不多说了。

不用多说，颁发者为TrustAsia。

![Pic10](https://u.ratodo.com/blog/2018/free-ssl-10.png!full)

### [七牛云](https://portal.qiniu.com/signin?redirect=~2Fcertificate~2Fapply)

七牛云的免费SSL证书申请也是一种渠道，颁发者同样为TrustAsia，在此就不多说。

![Pic11](https://u.ratodo.com/blog/2018/free-ssl-11.png!full)

## 国外证书品牌免费体验

国外的许多证书品牌会提供免费体验的DV证书，时长在一个月到三个月不等，这类证书在我看来没有什么申请的必要，因为时间太短，**并且！多数无法申请第二次！**但可能有人会想要查看各个品牌的差异，所以我在下面列举了几个证书品牌的免费体验证书申请地址。

### COMODO （三个月体验）

如果是特别喜欢COMODO这个品牌的话，这个证书也还是有申请的必要的，毕竟COMODO也是个知名老品牌。

可以通过[COMODO官网](https://www.comodo.com/landing/ssl-certificate/free-ssl/)申请。

![Pic12](https://u.ratodo.com/blog/2018/free-ssl-12.png!full)

### SSL.com （三个月体验）

这个品牌我没有去尝试，但是也提供了三个月的免费体验，感兴趣的话可以去SSL.com官网尝试一下。

强烈不建议这个证书，兼容性极差，Win10无法查看证书信息。

![Pic13](https://u.ratodo.com/blog/2018/free-ssl-13.png!full)

### GeoTrust （一个月体验）

这个我感觉实在是没有什么必要，虽然GeoTrust的品牌很响，[GeoTrust官网](https://www.geotrust.com/ssl/free-ssl-certificate/)申请。

![Pic14](https://u.ratodo.com/blog/2018/free-ssl-14.png!full)

### RapidSSL （一个月体验）

这个品牌的根证书是DigiCert，颁发者是RapidSSL RSA CA 2018，[RapidSSL官网申请](https://www.rapidssl.com/)。

![Pic15](https://u.ratodo.com/blog/2018/free-ssl-15.png!full)

## Cloudflare免费证书

Cloudflare免费证书是通过使用Cloudflare的免费全球加速来实现的。

![Pic16](https://u.ratodo.com/blog/2018/free-ssl-16.png!full)

## Let's Encrypt免费证书

接下来介绍的这个是目前最受欢迎的免费证书Let's Encrypt，尤其是它在V2版本还提供了通配符域名的支持。

Let's Encrypt旨在于推动HTTPS的发展，由互联网安全研究小组缩写ISRG）提供服务。主要赞助商包括Linux基金会、电子前哨基金会、Mozilla基金会、Akamai以及思科。

目前Let's Encrypt有多种申请方式，比如服务端创建，网站一键化创建。

服务器创建并自动续期参考链接：[老左博客](https://www.laozuo.org/11668.html)

网站一键化创建：推荐使用[FreeSSL](https://freessl.cn/)来创建。

![Pic17](https://u.ratodo.com/blog/2018/free-ssl-17.png!full)

创建过程中的CSR文件可以使用选择自动生成或者使用已有CSR。

Let's Encrypt有效期三个月，到期需手动续期或者在服务端设置程序实现自动续期。

证书申请成功后可以发现颁发者为Let's Encrypt Authority X3。

![Pic18](https://u.ratodo.com/blog/2018/free-ssl-18.png!full)

## 证书部署

目前市面上有很多免费的Linux管理面板，其中推荐使用[宝塔管理面板](https://www.bt.cn/?btwaf=96081394)。

在宝塔管理面板中进入网站设置，选择SSL即可快速部署证书。

![Pic19](https://u.ratodo.com/blog/2018/free-ssl-19.png!full)

不想安装面板的话也可以，不过会稍微麻烦一点，上传证书文件，修改配置文件，相关步骤也可以在网站上搜索到，就请自行搜索查看吧。

## 总结

当今互联网环境下使用HTTPS来加密连接已经是大趋势，各种免费SSL也五花八门，不过它们的本质也都是一样。

这些免费SSL对于流量不多的小网站来讲是非常实用的，但是对于一些流量不小的网站来讲还是建议买一个收费的SSL来保护你的网站以及你的访问者。
