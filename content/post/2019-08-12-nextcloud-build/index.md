---
title: 快速搭建NextCloud服务端及利用Aria2离线下载
date: 2019-08-12 20:18:00 +0800
author: Ratodo
comments: true
categories:
    - 建站笔记
slug:  nextcloud-build
image: https://u.ratodo.com/blog/2019/nextcloud-build-0.jpg!full
---

## 前言

网上可能已经有很多搭建NextCloud的教程了，今天这篇教程是我在搭建NextCloud过程中的一些心得，供大家参考一下。

在这个网盘到处飞的时代，拥有自己的一个私人网盘还是有很大作用的，起码数据算是掌握在自己手中（其实也是在服务商处。

NextCloud由于其出色的跨平台协作能力以及简洁易操作的界面博得了好多人的喜爱，今天介绍一下通过snap的安装方法。

P.S.本篇文章所使用的服务器为日本的LightSail，操作系统为Ubuntu18.04。

## 安装过程

首先登陆上自己的服务器，获取root权限（有些不必）

``sudo -i``

然后输入以下命令

```
sudo apt-get update
sudo apt-get install
snap sudo apt-get install snapd
sudo snap install nextcloud
```

直接复制粘贴可能会导致最后一行代码未被执行，建议查看后确定是否需要重新执行。

稍等片刻后出现如下字样即为安装成功。

![Pic1](https://u.ratodo.com/blog/2019/nextcloud-build-1.jpg!full)

这个时候就可以在浏览器里输入你服务器的ip地址进行设置了。

![Pic2](https://u.ratodo.com/blog/2019/nextcloud-build-2.jpg!full)

至此就算是安装好了，是不是很简单哈哈哈哈哈。

## 启用HTTPS站点

刚刚只是安装好了NextCloud服务端，现在要进行域名的设置。

首先要提前将要绑定的域名解析到你服务器的ip地址，最好等到确定解析成功了再进行接下来的步骤。

输入以下代码执行申请Let's Encrypt的证书：

``sudo nextcloud.enable-https lets-encrypt``

![Pic3](https://u.ratodo.com/blog/2019/nextcloud-build-3.jpg!full)

（在这一步的时候我出现了问题，在部署完证书之后我无法访问我的域名和ip地址，这个问题在我卸载重装之后等到了解决。P.S.卸载命令：snap remove nextcloud  重装后需重新执行申请证书命令）

此时通过域名访问会出现来自不受信任的域，如下图所示：

![Pic4](https://u.ratodo.com/blog/2019/nextcloud-build-4.jpg!full)

这时候只需要输入下面的命令即可（将domain.com换成自己的域名，如需再加就将1改为2，以此类推）

``sudo nextcloud.occ config:system:set trusted_domains 1 --value=domain.com``

这样就可以正常访问了，到这个时候，你的nextcloud已经可以正常使用了。

## 使用Aria2进行离线下载

如果能用服务器来离线下载的话就好多了，视频什么的都还可以在线看，但是不要违反服务器所在国家的相关法规，反正可能会被关闭服务器。

首先要带年纪右上角头像选择应用，再点击已禁用的应用，将External storage support启用。

回到服务器上执行安装Aria2：

``wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/aria2.sh &amp;&amp; chmod +x aria2.sh &amp;&amp; bash aria2.sh``

![Pic5](https://u.ratodo.com/blog/2019/nextcloud-build-5.jpg!full)

接下来修改Aria2的下载存储路径，打开：vi /root/.aria2/aria2.conf，找到：dir=XXX，建议修改为 /var/snap/nextcloud/common/nextcloud/data/xxx/files/Downloads（其中xxx是你在安装时候的用户名）

![Pic6](https://u.ratodo.com/blog/2019/nextcloud-build-6.jpg!full)

同时也建议将rpc令牌改为自己好记的字符串。

![Pic7](https://u.ratodo.com/blog/2019/nextcloud-build-7.jpg!full)

修改完毕后运行``service aria2 restart``重启一下aria2服务。

现在我们前往nextcloud的设置界面，点击管理下方的外部存储，添加刚刚的本地的外部存储。

![Pic8](https://u.ratodo.com/blog/2019/nextcloud-build-8.jpg!full)

这样就可以了，接下来下载一个aria2可视化程序。（以下内容引用自[挖站否](https://wzfou.com/nextcloud-aria2/)）

**引用开始**

AriaNg项目：

	项目：https://github.com/mayswind/AriaNg
 	下载：https://github.com/mayswind/AriaNg/releases/latest

AriaNg是一个前端(HTML+JS静态)控制面板，不需要和 Aria2(后端/服务端)放在一个服务器或者设备中，你可以直接下载到你的本地电脑上解压打开index.html，或者放在服务器访问，服务器只要有Nginx或者Apache就可以了。

点击打开AriaNg 设置 填入RPC别名、地址、协议、请求方法和密钥。RPC地址填写IP或者域名，端口默认的是6800，密钥的话就是你刚刚在配置文件中修改过的。（点击放大）

![Pic9](https://wzfou.com/wp-content/uploads/2017/08/Aria2-nextcloud_05.gif)

设置完成后，点击Aria2 状态你可以看到Aria2已经连接成功了。没有连接成功的话，检查一下VPS的防火墙有没有开放两个端口，一个是RPC监听端口`` 6800(默认)``，一个是BT监听端口`` 51413(默认)``。当然修改了配置文件后记得重启VPS。

![Pic9](https://wzfou.com/wp-content/uploads/2017/08/Aria2-nextcloud_05_1.gif)

打开AriaNg面板，你就可以添加httpBT磁力链接开始下载了。

![Pic9](https://wzfou.com/wp-content/uploads/2017/08/Aria2-nextcloud_07.gif)

由于我们用的是VPS主机下载资源，所以速度基本上可以飞起来了。

![Pic9](https://wzfou.com/wp-content/uploads/2017/08/Aria2-nextcloud_08.gif)

**引用结束**

**！！记得确认下载位置是不是之前设置的位置！！**

到这里之后还有一个问题，就是我们下载的文件可能不会在nextcloud中显示，这个时候就要使用nextcloud自带的occ功能来刷新文件夹中的文件了。

首先在root目录下创建一个可执行文件

``vi /root/nextcloud.sh``

在里面输入

```
#!/bin/bash
sudo nextcloud.occ files:scan --all
```

之后保存退出

对其赋予权限，``chmod 777 nextcloud.sh``

运行``crontab -e``回车

在下面添加一段代码：

``*/1 * * * * /root/nextcloud.sh``

按Ctrl+X退出，Y确定回车即可。上述命令代表每分钟执行一次nextcloud.sh，你也可以改成2分钟30分钟都可以，看你需要。

所有的下载任务都可以在Aria2可视化界面之中进行，很方便。

## 总结

建议不要在日本的服务器上BT下载，很容易挂掉~
