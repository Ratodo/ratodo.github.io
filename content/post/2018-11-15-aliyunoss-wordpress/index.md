---
title: 在Wordpress中启用阿里云OSS作为媒体库
date: 2018-11-15 10:39:00 +0800
author: Ratodo
comments: true
categories:
    - 建站笔记
slug: aliyunoss-wordpress
image: https://u.ratodo.com/blog/2018/aliyunoss-wordpress-0.jpg!full
---

## 前言

很多人可能都有这种困扰，网站加载速度太慢，而导致加载速度慢的其中一个大原因就是图片加载。

很多站长为了不用在国内备案，选择把服务器放到国外的VPS上，但国外主机往往对国内的用户不太友好，导致用户体验较差。

为了改善这种情况，我们可以把Wordpress的媒体库迁移至阿里云OSS，来使用阿里云的加速服务。

**注意：阿里云OSS需付费使用，国内区目前9元/40GB/1年，流量费用另付，详见阿里云OSS官网。**

## 准备工具

阿里云账号及阿里云OSS Bucket，搭建好的Wordpress系统，阿里云Accesskey

下载好aliyun-oss插件，下载地址：[Github](https://github.com/IvanChou/aliyun-oss-support/releases)（开发者：IvanChou）

也可以在主导航处点击**资源分享**下载。

## 阿里云OSS配置

登陆OSS控制管理台，找到你创建好的Bucket，若还未创建，点击右上角的新建Bucket（**读写权限设为公有读，标准存储**）。

在概览中你可以看到你的访问地址。

![Pic1](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-1.jpg!full)

点击上方的文件管理，新建目录**/wp-content/uploads**（为了方便后续设置）

![Pic2](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-2.jpg!full)

选择上方的基础设置，拉到最下方设置**镜像回源**。

![Pic3](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-3.jpg!full)

**文件名前缀是wp-content/uploads/，回源地址是http(s)://你的网站。**

接下来就可以进行插件的配置了。

## 安装插件并配置

在Wordpress管理界面选择插件-&gt;安装插件-&gt;上传插件，找到下载好的插件并进行安装启用。

在Setting-&gt;阿里云 OSS中进行配置，如下图所示。

![Pic4](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-4.jpg!full)

一切设置好后点击保存配置就大功告成啦。

## 附加功能的设置

### 图片预设样式

点击右面的**下载样式配置文件**，会跳出来新的窗口，是一个txt文件，可能不会自动下载，把网址粘贴到下载工具中下载下来。

然后回到**OSS管理控制台**，选择**图片处理-&gt;导入样式**，选择下载的txt文件将其导入即可。

如果想要图片水印的话可以先上传水印文件到OSS存储空间，然后编辑**full规则**，按下图提示配置。

（位置，大小，透明度看个人喜好，水印图路径为OSS的文件路径，可在文件管理中点击预览查询到<span style="text-indent: 0em;">）

![Pic5](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-5.jpg!full)

### 原图保护

在图片处理中，点击访问设置开启原图保护，按下图配置。

（**不建议勾选*且强烈建议将站点图标的格式转换为ico再上传设置，否则无法显示站点图标！****下面有讲到解决办法**）

![Pic6](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-6.jpg!full)

### 高级选项

在插件设置最下方选择**更多选项**，即可打开高级选项。

上面的站点图标因为开了原图显示而无法加载的解决办法如下：

将你要上传的站点图标更改名称，例如favicon，

再在**需要排除的文件**这一选项中填入你更改后的名称，即可让图片不经过OSS直接加载。

如下图所示。

![Pic7](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-7.jpg!full)

**注意：这样操作会导致所有带有favicon的图片全部绕过OSS直接加载，建议选择一个不常用到的名称。**

## 总结

配置工作到此就完成了，如果在大陆有备案并且有需要的朋友还可以开启CDN加速，在域名管理中即可设置。

![Pic8](https://u.ratodo.com/blog/2018/aliyunoss-wordpress-8.jpg!full)

用上了阿里云全家桶，感觉支付宝空空的。
