---
title: Wordpress全局字体修改详细教程
date: 2018-12-13 23:52:00 +0800
author: Ratodo
comments: true
categories:
    - 建站笔记
slug: wordpress-fonts-change
image: https://u.ratodo.com/blog/2018/wordpress-fonts-change-0.jpg!full
---

## 前言

有很多时候，Wordpress的字体不能让我们满意，这个时候我们就可以通过一些方法来修改主题的默认字体，来达到我们想要的效果。

下面介绍的更换字体主要分为两种，第一种是直接调用系统的字体，来替换原来主题的默认字体；第二种则是使用自己的字体文件，来实现字体的替换。

## 第一种：直接调用

这种方法通过修改CSS文件就可以实现，有些主题自带了自定义CSS样式的设置，Wordpress也提供了这一入口（后台管理-&gt;外观-&gt;自定义CSS），这时候我们就可以直接在里面填上：

```css
*:not([class*="icon"]):not(i) {
font-family: Segoe UI, "Microsoft Yahei" !important;
}
```

![Pic1](https://u.ratodo.com/blog/2018/wordpress-fonts-change-1.jpg!full)

上面的例子就是将字体全局优先替换成**Segio UI**，其次替换成**微软雅黑**，下面列举几个比较适合阅读的字体，供大家替换，替换代码中的**Segio UI**和**Microsoft YaHei**即可。

**宋体（SimSun）**，微软雅黑（"Microsoft Yahei"），**华文黑体（STHeiti）**
**冬青黑体（ Hiragino Sans GB ）**，苹方（PingFang SC）
Arial，Times New Roman，Droid Sans

## 第二种：私有字体调用

既然是私有字体，那就一定无法从公共库中直接选择，必定要上传到某个服务端来进行加载。

这里可以选择：**1.上传至网站服务器 2.上传至Github（推荐）3.上传至私有云存储进行调用**

在这之前需要先做一项准备工作，我们手上的字体文件通常只有一种格式，而为了满足不同浏览器的需要，我们需要将其扩展为五种格式，分别为**.ttf .eot .woff .woff2 .svg**

百度搜索就可以找到在线转换的工具，例如这个：[在线字体转换](https://www.fontke.com/tool/convfont/)

### 1.上传至网站服务器

这种方法面临这一种风险，中文字体库体积通常很大，比如我现在正在使用的思源黑体，一个ttf文件就有8M多，再加上国内服务器的小带宽，肯定导致网站加载时间大大加长。

将你前面准备好的五种字体格式全部上传到网站的一个文件夹内，比如我放在/fonts文件夹内，且统一命名，比如siyuan.ttf,siyuan.svg等等。
在自定义CSS样式中输入下列代码：

```css
@font-face {
font-family: '随便一个名称，需要和下面的保持对应';
src: url('../fonts/yourfont.eot');
src:
url('../fonts/yourfont.eot') format('embedded-opentype'),
url('../fonts/yourfont.woff2') format('woff2'),
url('../fonts/yourfont.woff') format('woff'),
url('../fonts/yourfont.ttf') format('truetype'),
url('../fonts/yourfont.svg') format('svg');
font-weight: normal;
font-style: normal;
}
*:not([class*="icon"]):not(i) {
font-family: "与上面起的名字的对应" !important;
}
```

![Pic2](https://u.ratodo.com/blog/2018/wordpress-fonts-change-2.jpg!full)

个人不是很推荐这种方法，建议还是使用下面的云存储托管。

### 2.上传至Github使用免费的jsDelivr CDN加速

[jsDelivr](https://www.jsdelivr.com)如何如何好用这边就不多说了，[Github](https://github.com)怎么使用这边也不多说了，大体方法就是将你的字体文件上传至Github自己的仓库中，然后使用jsDelivr提供的加速服务来调用，方便好用还不要钱。

jsDelivr调用格式 https://cdn.jsdelivr.net/gh/Github用户名/仓库名/具体路径

svg文件大多会超过20M，评论区小伙伴提醒jsDelivr调用文件超过20M会报错，可以使用其他方式加载svg，不过留在上面也没什么问题，因为正常是不会使用到的。

附上几个字体的调用链接（托管于Github，使用jsDelivr加速服务）

#### AdobeCleanHanSC

```css
@font-face {
font-family: 'AdobeCleanHanSC';
src: url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.eot');
src:
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.eot') format('embedded-opentype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.woff2') format('woff2'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.woff') format('woff'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.ttf') format('truetype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AdobeCleanHanSC/AdobeCleanHanSC.svg') format('svg');
font-weight: 400;
font-style: normal;
font-display: swap;
}
*:not([class*="icon"]):not(i) {
font-family: "AdobeCleanHanSC" !important;
}
```

#### 思源黑体

```css
@font-face {
font-family: 'siyuan';
src: url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.eot');
src:
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.eot') format('embedded-opentype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.woff2') format('woff2'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.woff') format('woff'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.ttf') format('truetype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/siyuan/siyuan.svg') format('svg');
font-weight: 400;
font-style: normal;
font-display: swap;
}
*:not([class*="icon"]):not(i) {
font-family: "siyuan" !important;
}
```

#### 筑紫A丸
```css
@font-face {
font-family: 'AWan';
src: url ('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/Awan.eot');
src:
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/AWan.eot') format('embedded-opentype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/AWan.woff2') format('woff2'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/AWan.woff') format('woff'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/AWan.ttf') format('truetype'),
url('https://cdn.jsdelivr.net/gh/Ratodo/Lib/fonts/AWan/AWan.svg') format('svg');
font-weight: normal;
font-style: normal;
font-display: swap;
}
*:not ([class*="icon"]):not (i) {
font-family: "AWan" !important;
}
```

### 3.上传至云存储进行调用

在个人服务器上存储字体文件的话，服务器需要在加载网页，图片等的同时等待加载字体，但如果使用云存储调用的话就可以在很大程度上解决网站加载慢的问题。

云服务的话有很多选择，如果你的网站还没有开启HTTPS的话，可以去使用**免费的七牛云存储**，如果开启了HTTPS的话可以申请使用**免费的又拍云存储或者使用收费的阿里云OSS**。下面以阿里云OSS和又拍云云存储为例进行演示。

首先，将你先前准备好的四种格式的字体文件上传至你的云存储中，云储存需设置为**公有读**权限。

![Pic3](https://u.ratodo.com/blog/2018/wordpress-fonts-change-3.jpg!full)

然后进入**基础设置-&gt;防盗链**，将你的域名添加进去，允许空Refer，记得加http(s)://，如下图所示。

![Pic4](https://u.ratodo.com/blog/2018/wordpress-fonts-change-4.jpg!full)

接着设置**跨域规则**，将你的域名添加进去，同样需要加http(s)://，**允许Headers处填写***

![Pic5](https://u.ratodo.com/blog/2018/wordpress-fonts-change-5.jpg!full)

接下来就可以去自定义CSS了，填写以下代码：

```css
@font-face {
font-family: '随便一个名称，需要和下面的保持对应';
src: url('../fonts/yourfont.eot');
src:
url('../fonts/yourfont.eot') format('embedded-opentype'),
url('../fonts/yourfont.woff2') format('woff2'),
url('../fonts/yourfont.woff') format('woff'),
url('../fonts/yourfont.ttf') format('truetype'),
url('../fonts/yourfont.svg') format('svg');
font-weight: normal;
font-style: normal;
}
*:not([class*="icon"]):not(i) {
font-family: "与上面起的名字的对应" !important;
}
```

至于又拍云，在云存储配置完成后使用FTP工具登陆云存储空间并进行上传后，即可使用文件的URL地址来进行使用。

![Pic6](https://u.ratodo.com/blog/2018/wordpress-fonts-change-6.jpg!full)

又拍云的云存储连接方式可参考官方文档：[文件管理指南 - 又拍云存储](https://console.upyun.com/services/file/filemanageguide/)

这样就大功告成啦，登上你的网站看看吧！

## 总结

由于目前还没有很全的字体库，所以第二种方法应该使用的比较多的。

如果你的服务器带宽足够大，或者开了什么加速的话，将字体文件放在网站服务器上绝对是没什么问题的，但没有的话还是建议使用一个云存储来帮助你的网站加载那庞大的字体库。

P.S.有个程序叫字蛛，可以缩小网站字体体积，不过我试了一下没有成功，大家也可以照这个方向去研究研究。
字蛛只支持静态html压缩字体体积，所以Wordpress无法直接使用。
