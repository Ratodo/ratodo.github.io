---
title: 新版百度云加速使用体验
date: 2019-12-08 14:27:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
上个月的时候偶然发现了百度云加速进行了一波升级，不仅新增了对IPv6的支持，免费版还同时支持了SSL证书部署。之前在写<a href="https://www.ratodo.com/article/free-cdn.html" target="_blank" rel="noopener noreferrer">CDN对比</a>的时候就提到了百度云加速，当时免费版还不支持HTTPS，这个也是成为了我不去用他的理由，现在支持了还有什么理由不去用呢？何况海外还是使用Cloudflare的节点，访问延迟肯定会大幅降低。
<h2>部署过程</h2>
和以前一样，百度云加速提供NS接入和CNAME接入两种方式，前者为更改域名的解析服务器，将DNS解析也一并放到百度云加速，后者则是通过设置CNAME解析的方式来起到单域名加速的方式。由于我将域名邮箱和博客网站全都放在了根域名下，所以这里我选择了NS接入，这样就避免了MX记录与CNAME记录冲突的问题了。

<img class="size-full wp-image-9136 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/02478.png@!full" alt="" width="428" height="82">

成功接入后我们就可以去添加解析记录等等的操作了，在你添加A记录或者是CNAME记录的时候，默认会将云加速打开，此时会显示为绿色的云彩，如需关闭点击编辑将其关闭即可。

<img class="size-full wp-image-9137 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/02628.png@!full" alt="" width="552" height="71">

在左边的<strong>安全功能</strong>的二级菜单中我们可以看到<strong>HTTPS</strong>选项，这里的设置和Cloudflare如出一辙，事后看来这里应该用的和Cloudflare一样的技术。

<img class="size-full wp-image-9138 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/04928.png@!full" alt="" width="1679" height="268">

当然这里不像Cloudflare一样自动提供免费证书，需要自行前往左面的<strong>证书管理</strong>处上传自有证书或是申请百度提供的免费证书（这里的免费证书我试着申请，但一直在审核中状态）。

上传完成后就可以点击部署。

<img class="size-full wp-image-9140 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/04668-1.png@!full" alt="" width="530" height="163">

这样部署过程就完成了，之后里面的其他功能可以自己探索。
<h2>分析统计</h2>
在百度云加速的数据概览里可以很清晰的看到访问情况，免费版每天的流量限制是10GB，这样的流量对小博客来说完全够用。

<img class="size-full wp-image-9141 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/09958.png@!full" alt="" width="1663" height="815">

按照惯例，来测试一下全球Ping情况，如下图所示。

<img class="size-full wp-image-9143 aligncenter" src="https://p.ratodo.com/wp-content/uploads/2019/12/01528.png@!full" alt="" width="1354" height="728">

提升很明显了，不过免费版国内的节点不多，从全国Ping的数据来看，似乎只有五六个节点，不过质量都还可以。
<h2>总结</h2>
如果想要全球化的CDN加速的话，百度云加速是一个很好的选择，不过国内节点比较少，并且需要备案才能使用，NS接入提供的DNS解析服务功能也较少。

相比之下又拍云提供的国内节点很多，但国外自建加速节点较少，这点比不上百度云加速合作的Cloudflare，在这点上大家自行取舍吧。
