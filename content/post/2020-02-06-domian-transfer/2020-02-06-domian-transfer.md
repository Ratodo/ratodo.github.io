---
title: 域名转移日记
date: 2020-02-06 22:16:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
这次进行域名转移，一来是觉得阿里云的域名隐私有很大的问题，二来就是一直想尝试下国外域名商的服务，三来也是为日后迁移在阿里云的服务器做准备。

首先说一下阿里云域名隐私问题，在阿里云whois查询的页面上，清清楚楚写着以下几段话：

<img class="aligncenter size-full wp-image-9204" src="https://p.ratodo.com/wp-content/uploads/2020/02/06916.png@!full" alt="" width="809" height="408" />

并且我们用户在阿里云的WHOIS上查询的时候，也确实看不到什么东西，就像这样：

<img class="aligncenter size-full wp-image-9205" src="https://p.ratodo.com/wp-content/uploads/2020/02/09246.png@!full" alt="" width="648" height="515" />

<del>看似贯彻落实了规范，但是只要去国外的任何一个whois查询页面，都可以清清楚楚的查到阿里云所“保护”的个人信息，不知道阿里云的隐私保护保护在哪里了，怕是只局限于自家的whois查询系统吧。</del>

阿里云对不起！.cn域名没有隐私保护服务，并且强制实名，所以显示全部信息也是必然。

再来是国外域名注册商的选择，之前我有试过Gandi和Godaddy的域名服务，Gandi的价格偏贵，Godaddy的口碑一向不好。由于域名是.cn，导致了可选择的域名服务商很少很少，且大多数都是国内的注册商。最后是参考了一下哪煮米的推荐，选择了<a href="http://www.dynadot.com/?s7V8IDA7080m6O" target="_blank" rel="noopener noreferrer">dynadot</a>这家域名注册商，支持.cn转移，支持中文，支持微信支付宝，很好的满足了我的要求。

最后就是为未来迁移服务器做准备了，目前还在使用的是阿里云的学生机，￥10/月，还在接受范围之内，后续无法续费了之后可能会考虑使用国际站的轻量服务器或者是其他VPS商家的国外VPS，备案就只用来做国内CDN加速了。
<h2>过程</h2>
由于域名在阿里云备案的关系，担心迁出域名是否会导致备案出问题，这个我在网上没找到相应的案例，只能等迁移完成之后再看了。

第一步：将域名的DNS服务器暂时托管到Cloudflare，防止在迁移过程中解析出现问题（迁移完成后可能也会继续使用Cloudflare的解析服务）。

第二步：在dynadot注册账号，暂时填写了美国地址以及美国手机号码。

第三步：在阿里云请求转出，在验证完身份之后，带有转移码的邮件就会发到你的邮箱，不知道为什么我的被扔进了垃圾邮件里面。

<img class="aligncenter size-full wp-image-9207" src="https://p.ratodo.com/wp-content/uploads/2020/02/09586.png@!full" alt="" width="651" height="593" />

第四步：在dynadot<a href="https://www.dynadot.com/zh/domain/transfer.html" target="_blank" rel="noopener noreferrer">申请转入</a>，如下图所示，填写完域名和转移码，域名就会被添加进购物车中。

<img class="aligncenter size-full wp-image-9206" src="https://p.ratodo.com/wp-content/uploads/2020/02/02196.png@!full" alt="" width="1099" height="422" />

第五步：付款，支持支付宝和微信，付款转移成功后会增加一年域名有效期，支付宝的付款链接不会自动弹出，需要手动点击。

第六步：此时会收到来自阿里云的通知邮件，提醒你域名会在接下来的五到七天内被转出，并且此时在dynadot也已经有了记录，来等待域名转入。

第七步：等待域名转入。

第八步：在新的域名注册商处使用其DNS服务器或者使用正在使用的第三方DNS解析服务。

（2020.2.12 20:06更新）完成转入，从申请转出到转入完成用时6天。

<img class="aligncenter size-full wp-image-9234" src="https://p.ratodo.com/wp-content/uploads/2020/02/16502.png@!full" alt="" width="679" height="311" />
<h2>题外话</h2>
.cn域名实名认证是CNNIC的要求，与注册商无关，不过在国外注册商注册.com等后缀域名不需要实名认证这一步。Dynadot上表示注册不需要实名认证，但是设置解析之后需要提交实名认证，目前我没有提交，后续如果解析出问题会再更新情况。

<img class="aligncenter size-full wp-image-9233" src="https://p.ratodo.com/wp-content/uploads/2020/02/17622.png@!full" alt="" width="1167" height="501" />

目前的WHOIS查询结果：

<img class="aligncenter size-full wp-image-9262" src="https://p.ratodo.com/wp-content/uploads/2020/02/19902.png@!full" alt="" width="1001" height="444" />
