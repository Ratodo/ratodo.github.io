---
title: 使用腾讯云函数SCF搭建TCShare
date: 2020-04-03 15:18:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
之前网站的资源分享用的是基于OneDrive存储的oneindex，但是OneDrive国际版在国内的链接速度真的是不敢恭维，世纪互联版速度是快，可惜能拿到的路子不多，也就作罢。

自从TCShare升级到了3.0版本之后，也增加了对和彩云，OneDrive，OneDrive世纪互联版的支持，再加上本就支持的天翼云盘，支持的云盘数量足以让我们从中选择一个适合自己的来使用了。

由于是卑微的移动用户，这里我用的就是移动的和彩云，空间足够用来平常分享一些东西，最重要的一点就是不限速，亲测连接速度很快。
<h2>搭建教程</h2>
搭建方法主要就是服务器搭建和腾讯云函数搭建两种方式，关于服务器搭建很简单，弄好文件后composer install就安装完成了，下面主要说一下腾讯云函数SCF的搭建方法。

为什么要选择腾讯云函数呢？腾讯云函数每个月有固定的免费额度，再加上API网关的首年每月前1G流量免费，对于个人来说完全是够用了。

<img class="aligncenter wp-image-9908 size-full" src="https://p.ratodo.com/wp-content/uploads/2020/04/03995.png@!full" alt="" width="928" height="245" />

<img class="aligncenter size-full wp-image-9909" src="https://p.ratodo.com/wp-content/uploads/2020/04/03154.png@!full" alt="" width="928" height="311" />

<strong>不过毕竟不是完全免费的东西，使用的时候还是注意一下。</strong>
<h3>1.下载源码到本地并安装依赖</h3>
[github author="xytoki" project="TCShare"][/github]

原作者由于一些原因停止更新并且删除了代码，仅保留了release，关于安装的说明可查看我的fork页面。

[github author="Ratodo" project="TCShare"][/github]

从Github上下载release的源码之后，在本地安装php和composer，php和composer的相关安装包<a href="https://h.ratodo.com/Sources/TCShare/" target="_blank" rel="noopener noreferrer">看这里</a>，当然你也可以在自己的服务器端完成composer依赖安装，然后下载安装完成依赖后的文件夹。

先解压php，然后打开composer_setup.exe，手动选择刚刚解压出的php.exe，进行安装。

安装完成之后cmd命令进入源码所在文件夹，输入命令：
<pre><code>composer install</code></pre>
<h3>2.创建SCF</h3>
进入<a href="https://console.cloud.tencent.com/scf/" target="_blank" rel="noopener noreferrer">腾讯云函数</a>，在左侧函数服务中新建函数，上方可以选择地域，创建时运行环境选择PHP7.2，方式选择空白函数。

<img class="aligncenter size-full wp-image-9910" src="https://p.ratodo.com/wp-content/uploads/2020/04/03618.png@!full" alt="" width="751" height="379" />

执行方法为index.main_handler，提交方法为上传本地文件夹，选择刚刚的文件夹提交上去。

点开高级设置，输入环境变量，相关设置如下，建议去Github仔细阅读一下说明文档：
<pre><code>##天翼云和OneDrive部分

#   XS 是前缀
#   | -KEY 是配置种类，可选KEY，APP，SEC
#   | | - -ct是key的ID（类似config.php）
#   | | - | - something是配置名称
#   | | - | - | - - - - value在等号右边
#   XS_KEY_ct_something=value

    #天翼云配置
    XS_KEY_ct=ctyun   #必填，值为ctyun
    XS_KEY_ct_FD=     #应用文件夹名
    XS_KEY_ct_AK=     #AK
    XS_KEY_ct_SK=     #SK
    #Onedrive配置
    XS_KEY_od=onedrive
    #世纪互联配置
    XS_KEY_od=onedriveCN

#   这里APP后面的可以是任意值，一般就123456下去
#          ↓
    XS_APP_1=/              #挂载路径
    XS_APP_1_NAME=TCShare   #网盘名称
    XS_APP_1_THEME=mdui     #界面主题
    XS_APP_1_BASE=/         #网盘内路径
    XS_APP_1_KEY=ct         #对应上面Key的ID

##和彩云部分

XS_KEY_cm=caiyun
XS_KEY_cm_TOKEN='{"cyToken":"******|*|RCS|******|******","encryPhone":"******"}'
XS_APP_&lt;id&gt;_NAME="TCShare 和彩云"
XS_APP_&lt;id&gt;_THEME=mdui
XS_APP_&lt;id&gt;_BASE=/
XS_APP_&lt;id&gt;_KEY=cm
XS_APP_&lt;id&gt;=/caiyun</code></pre>
等号左面为填入key，右面填入value中，其中要注意的是，如果是使用和彩云，<strong>TOKEN在这一步先不填，NAME要去掉左右的引号</strong>。

<img class="aligncenter size-full wp-image-9911" src="https://p.ratodo.com/wp-content/uploads/2020/04/03158.png@!full" alt="" width="665" height="623" />

创建完成之后再编辑函数，这时候再把TOKEN填进去，<strong>注意TOKEN的value值左右需要去掉单引号</strong>。

<img class="aligncenter size-full wp-image-9912" src="https://p.ratodo.com/wp-content/uploads/2020/04/03484.png@!full" alt="" width="420" height="46" />

选择上方的触发方式，添加触发方式，像下面这样设置即可。

<img class="aligncenter size-full wp-image-9913" src="https://p.ratodo.com/wp-content/uploads/2020/04/03594.png@!full" alt="" width="712" height="483" />

获得访问路径先打开看看有没有问题，没问题即可进入下一步。
<h3>3.设置API网关</h3>
进入<a href="https://console.cloud.tencent.com/apigateway" target="_blank" rel="noopener noreferrer">API网关</a>，左侧服务，你就会发现已经有了一个服务，单击服务名，进入设置。

点击自定义域名，输入你的域名并上传证书，如果不开启https就不需要这一步，其他像下图一样设置。

<img class="aligncenter size-full wp-image-9914" src="https://p.ratodo.com/wp-content/uploads/2020/04/03698.png@!full" alt="" width="942" height="674" />

添加完成后选择管理API，编辑，路径改为/，勾上启用响应集成，返回类型选择HTML，完成，发布。
<h3>4.返回SCF修改环境变量</h3>
最后一步返回云函数，新增一条环境变量：
<pre><code>scf_base=/</code></pre>
这时输入域名即可访问。

<img class="aligncenter size-full wp-image-9915" src="https://p.ratodo.com/wp-content/uploads/2020/04/035984.png@!full" alt="" width="1057" height="424" />

至此SCF搭建TCShare就全部完成了。
<h2>总结</h2>
本篇文章是以搭建和彩云为例，搭建天翼云盘同理，其中的AK,SK去Github上搜索一下就能找到，实在不行找我也可以私发给你。

个人觉得TCShare总体来说完成度已经很高了，对大佬做出的努力表示感谢！此外，这是我搭建的<a href="https://h.ratodo.com" target="_blank" rel="noopener noreferrer">和彩云地址</a>。

再次强调一下，SCF和API网关并非免费产品，使用免费额度的时候要多留心注意。

通过这个程序，就可以做到在文章中调用云盘中的音视频等资源了，很是方便。

[video url="https://y.ratodo.com/Video/Interesting/%E9%9F%B3%E9%98%99%E8%AF%97%E5%90%AC_%E7%8E%8B%E6%A2%93%E9%92%B0%20-%20%E7%99%BD%E9%9C%B2.mp4"][/video]
<h3>参考文章</h3>
<a href="https://www.hostloc.com/thread-651572-1-1.html" target="_blank" rel="noopener noreferrer">腾讯云SCF搭建TCShare天翼云目录列表</a>

<a href="https://xylog.cn/2020/03/03/tcshare.html" target="_blank" rel="noopener noreferrer">TCShare：云盘目录列表，支持天翼云</a>
