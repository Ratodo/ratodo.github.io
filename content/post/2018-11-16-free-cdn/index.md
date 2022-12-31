---
title: 国内免费CDN对比与申请部署教程
date: 2018-11-16 21:43:00 +0800
author: Ratodo
comments: true
categories:
    - 建站笔记
slug: free-cdn
image: https://u.ratodo.com/blog/2018/free-cdn-0.jpg!full
---

## 前言

本篇文章针对的是国内CDN，**需要完成备案才能够使用**。

现在的网络环境下，如果你的网站只是用一个单一的节点的话，可能会导致有些地区的访问速度极慢甚至还会出现打不开的情况。

这对新站点更是一个很大的损失，而刚入门的新站长（比如我），资金方面可能会有问题，并且网站流量不是很大。这时候我们就可以借助于国内免费的CDN服务来加速我们的个人站点了。

（国外CDN加速推荐Cloudflare，之前有介绍过怎么来设置和部署，[点此查看](https://www.ratodo.com/article/cloudflare-cdn-ssl.html)）

**（长文多图预警）**

## 免费CDN

本文章中进行测试的**免费CDN**有：

1. 百度云加速 2. 又拍云联盟 3. 七牛云加速 4. 加速乐（知道创宇） 5. 景安CDN（快云） 6. 华为云CDN（试用） 7. 360CDN

主要从**注册难易性**，**管理****面板功能完整性**和**各地网络延迟**三个方面来进行对比。

（以下小标题均为超链接，可跳转至相应的CDN提供商官网）

**（以下若有注册链接均为我的推广链接，不强迫使用，注册地址点击标题的官方网站进入就可以找到入口，但还是希望能支持一下）**

### [百度云加速](https://su.baidu.com/product/cdn.html)

![Pic1](https://u.ratodo.com/blog/2018/free-cdn-1.jpg!full)

登陆上你的百度账号后，即可进入接入界面，如果没有实名认证的话，还需要先去控制台进行实名认证，提交资料后半天左右可以通过。

再接入界面填写你的主域名（例如我的是resdon.cn，得备案，未备案域名验证不会通过），并且选择接入方式，NS方式需要修改域名服务器，CNAME只需要添加一个CNAME解析就可以了。

![Pic2](https://u.ratodo.com/blog/2018/free-cdn-2.jpg!full)

接下来就是添加子域名，主域名是@，www是www，我这里写的是一个测试页。

![Pic3](https://u.ratodo.com/blog/2018/free-cdn-3.jpg!full)

接下来设置DNS记录，需要你去DNS服务商处添加CNAME记录，如果选择的NS接入，则需修改你的域名服务器（较麻烦，不推荐）。

![Pic4](https://u.ratodo.com/blog/2018/free-cdn-4.jpg!full)

下一步是选择版本，我们选择免费版本就可以。

等待信息同步之后就可以使用百度云加速了。

另外，百度云加速支持全球加速（国内自有节点，国外与Cloudflare合作），但免费版只支持HTTP加速，即你无法布置SSL证书。

控制台界面如下图。

![Pic5](https://u.ratodo.com/blog/2018/free-cdn-5.jpg!full)

下面使用[IPIP.NET](https://www.ipip.net)提供的测试工具来测试一下全球延迟。

![Pic6](https://u.ratodo.com/blog/2018/free-cdn-6.jpg!full)

得益于和Cloudflare的合作，**海外的延迟极好**，这点是其他几家免费CDN提供商都没有的优势。

我用的是阿里云上海的服务器，国内裸连的延迟如下，可做个对比。

![Pic7](https://u.ratodo.com/blog/2018/free-cdn-7.jpg!full)

### [又拍云联盟](https://console.upyun.com/register/?invite=H1QjLM2pX)（本站正在使用）

![Pic8](https://u.ratodo.com/blog/2018/free-cdn-8.jpg!full)

**使用他们的免费CDN服务需要在网页上添加他们的站点Logo，且需要通过审核**（每月10GB存储+15G CDN流量）。

新用户注册有有效期一个月的61元代金券，[点此注册](https://console.upyun.com/register/?invite=H1QjLM2pX)。

下图为控制台照片。

![Pic9](https://u.ratodo.com/blog/2018/free-cdn-9.jpg!full)

点击右上角**创建服务**，进入到创建页面。

![Pic10](https://u.ratodo.com/blog/2018/free-cdn-10.jpg!full)

这儿值得注意的是，**支持全球加速和HTTPS**，在这点上比百度云又好了一点点，到DNS服务商处添加CNAME解析就完成设置了。

![Pic11](https://u.ratodo.com/blog/2018/free-cdn-11.jpg!full)

可以设置图片处理，回源管理，HTTPS等，HTTPS里面还可以一键开启TLS1.3，比较实用。

下面用IPIP.NET来测试一下全球延迟。

![Pic12](https://u.ratodo.com/blog/2018/free-cdn-12.jpg!full)

全球节点**除了亚洲以外加速效果都不太理想，只能说稍微好了一点点**。

看了下，又拍云的国外CDN节点较少，检测出来的仅有德国，香港，新加坡三个海外节点，导致国外延迟不理想。

还请各位仁者见仁智者见智吧。

## [七牛云加速](https://portal.qiniu.com/signup?code=1hmfwbuy04382)

七牛云加速同样需要**实名认证**，[点此注册](https://portal.qiniu.com/signup?code=1hmfwbuy04382)。

七牛云**只支持免费HTTP加速**（每月免费10GB），**不支持HTTPS（需付费）**，支持全球加速。

![Pic13](https://u.ratodo.com/blog/2018/free-cdn-13.jpg!full)

选择**域名管理-&gt;添加域名**，开始设置你的CDN。

![Pic14](https://u.ratodo.com/blog/2018/free-cdn-14.jpg!full)

创建成功后，到DNS服务商处添加CNAME解析即可。

![Pic15](https://u.ratodo.com/blog/2018/free-cdn-15.jpg!full)

等待相关信息同步完成后，就可以开始使用了。

七牛云同样包含了**回源配置**，**缓存配置**，**HTTPS配置**（免费版不可用），**访问控制**，**图片优化**等功能，还是可以的。

![Pic16](https://u.ratodo.com/blog/2018/free-cdn-16.jpg!full)

接下来来测试全球延迟

![Pic17](https://u.ratodo.com/blog/2018/free-cdn-17.jpg!full)

**全球延迟极好！可以和百度云加速相提并论了。**

**国内延迟也不错，有明显的加速效果！**可惜**不支持HTTPS**，这算是唯一的缺点了。

### [加速乐（知道创宇）](https://sso.yunaq.com/cas/login?service=https%3A%2F%2Fwww.yunaq.com%2Faccounts%2Flogin%2F%3Fnext%3D%252Fsite%252Flist%252F)

创建账号后，需要**实名认证**，**验证手机**，**邮箱**，缺一不可。

免费版CDN能提供的有：**3600GB/月**，峰值最高5G/小时，72条线路，防盗链，永久在线等（比较适合大流量的站长）。**不支持HTTPS**。

![Pic18](https://u.ratodo.com/blog/2018/free-cdn-18.jpg!full)

点击**添加域名**，输入**主域名**，同样选择**CNAME接入方式**，进入下一步。

下一步就是**添加子域名**了，点击添加子域名，输入你要加速的内容，这一部分和百度云加速有些相似。

![Pic19](https://u.ratodo.com/blog/2018/free-cdn-19.jpg!full)

然后继续**下一步**。

![Pic20](https://u.ratodo.com/blog/2018/free-cdn-20.jpg!full)

需要**验证域名**，方式有两种，**挂标验证和TXT验证**，选择最适合自己的就好。

我在这里选择的是**TXT验证**，只需要在域名注册商处添加一个TXT解析即可。

下为验证成功后的提示。

![Pic21](https://u.ratodo.com/blog/2018/free-cdn-21.jpg!full)

默认模式是**回源模式**，需要回到子域名管理处重新选择为**云端模式**（自域名管理-&gt;DNS修改-&gt;云端模式）<span style="text-indent: 0em;">。</span>

![Pic22](https://u.ratodo.com/blog/2018/free-cdn-22.jpg!full)

然后根据显示出的CNAME去DNS服务商处添加你的CNAME记录。

添加完后点击**检测**，检测成功即为成功接入。

![Pic23](https://u.ratodo.com/blog/2018/free-cdn-23.jpg!full)

控制面板支持的功能如下，**没有图片优化**。

![Pic24](https://u.ratodo.com/blog/2018/free-cdn-24.jpg!full)

**知道创宇加速乐主打的是安全加速功能，提供了其他服务商没有提供的三个防火墙。**

下面测试全球延迟（官网没标注是否全球加速，我们可以正好来检测一下）

![Pic25](https://u.ratodo.com/blog/2018/free-cdn-25.jpg!full)

很明显，**不支持全球加速**，但是国内延迟有较大改善，但海外延迟**不降反升**。

但加速乐的优点是**安全**和**大流量**。

### [快云CDN（景安网络）](https://ac.zzidc.com/cas/login?service=https%3A%2F%2Fmc.zzidc.com%2Fkycdn%2FkuaiyunCdnAction)

景安同样需要**实名认证**之后才可以使用。

![Pic26](https://u.ratodo.com/blog/2018/free-cdn-26.jpg!full)

点击**添加网站**，即可开始配置CDN。添加完主域名后，会提示你**在七天内完成解析，否则会被删除**。

在**添加子域名**中，进行对加速域名的添加，与上文中的百度云加速和加速乐添加类似。

添加完子域名后，根据显示出来的**别名**去在DNS服务商处添加CNAME解析即可。

![Pic27](https://u.ratodo.com/blog/2018/free-cdn-27.jpg!full)

控制台仅支持**缓存刷新**与**智能压缩**，图片快速加载都需要**专业版**支持，在这点上不如其他服务商，并且**不支持HTTPS**。

![Pic28](https://u.ratodo.com/blog/2018/free-cdn-28.jpg!full)

下面来测试全球延迟，和加速乐一样，**没有写出是否支持全球加速**。

![Pic29](https://u.ratodo.com/blog/2018/free-cdn-29.jpg!full)

检测出来了，支持海外加速，海外用的**Cloudflare服务器**，在这点上和百度云加速一样，不得不说，Cloudflare的海外加速很稳。

至于国内加速的情况，只能说**加速效果一般**。

### [华为云CDN（试用）](https://activity.huaweicloud.com/2018nov-promotion/index.html?fromuser=cmVzZG9u)

华为云的CDN是使用两个月，每个月**500GB加速流量**，需要**实名认证**，[注册链接](https://activity.huaweicloud.com/2018nov-promotion/index.html?fromuser=cmVzZG9u)。

![Pic30](https://u.ratodo.com/blog/2018/free-cdn-30.jpg!full)

实名认证支持三种认证方式，**银行卡认证**和**APP人脸验证**是实时的。

![Pic31](https://u.ratodo.com/blog/2018/free-cdn-31.jpg!full)

是以订单的形式完成这两个月的试用的，**不****支持全球加速**（仅为国内流量包，需另购海外加速包），**支持HTTPS**，可惜是试用两个月（购买大陆流量包目前的价格是50元/500GB/1年）。

![Pic32](https://u.ratodo.com/blog/2018/free-cdn-32.jpg!full)

点击**添加域名**，完成对你域名的CDN加速。

填写完信息后确定，稍等片刻后会出现CNAME信息，到DNS服务商处添加CNAME解析。

![Pic33](https://u.ratodo.com/blog/2018/free-cdn-33.jpg!full)

毕竟还是个付费产品，该有的功能都有，还是挺齐全的。

接下来测试全球延迟。

![Pic34](https://u.ratodo.com/blog/2018/free-cdn-34.jpg!full)

国内延迟处于**比较优秀**的水平，海外延迟就不用说了，自然崩了。

### [360 CDN](https://wangzhan.qianxin.com/)（无法使用）

360的CDN感觉选择是**处于半残废状态**，也同样需要**实名认证**。

![Pic35](https://u.ratodo.com/blog/2018/free-cdn-35.jpg!full)

在文本框中输入**主域名**，选择CNAME接入，添加域名。

![Pic36](https://u.ratodo.com/blog/2018/free-cdn-36.jpg!full)

接着**添加子域名**即可，选择云防护，过程和百度云加速类似。

![Pic37](https://u.ratodo.com/blog/2018/free-cdn-37.jpg!full)

将获得的CNAME添加到DNS服务商处的解析中即可加速生效。

![Pic38](https://u.ratodo.com/blog/2018/free-cdn-38.jpg!full)

CNAME解析已经生效了，但是360这边检测不出来，果然是残废的，无法使用。

下面的是之前解析成功时的延迟，惨不忍睹，除了列出的这几个，其余节点全部100%丢包。

![Pic39](https://u.ratodo.com/blog/2018/free-cdn-39.jpg!full)

## 总结

除了360不能用了以外，将**其他6家服务商**纳入其中进行对比。

**注册难易性：**各家都差不多，都需要**实名认证**+**网站备案**，**又拍云**要更为麻烦，要向官方提出申请，并**在网站上推广又拍云**。

**管理****面板功能完整性：华为云&gt;又拍云&gt;七牛云=百度云&gt;加速乐&gt;快云**

下面比较中，最前面的是最好。

**各地网络延迟（全球）：百度云&gt;快云&gt;七牛云&gt;又拍云（前为支持全球）&gt;华为云&gt;加速乐**

**各地网络延迟（国内）：华为云&gt;又拍云&gt;七牛云&gt;百度云&gt;加速乐&gt;快云**

（按平均值算，且至经过IPIP.NET一次测试，不严谨）

**支持HTTPS的服务商：又拍云，华为云**

**支持全球加速的服务商：百度云，快云（基于Cloudflare）；又拍云，七牛云（自有）**

**综合推荐：又拍云&gt;百度云&gt;七牛云&gt;快云&gt;加速乐&gt;华为云**

**（为个人想法，仅供参考；才疏学浅，如有错误，还请指正）**

Last Update Time: 2018-11-16
