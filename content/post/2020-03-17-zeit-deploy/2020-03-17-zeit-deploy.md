---
title: 使用ZEIT部署源码（Github等）
date: 2020-03-17 17:45:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<!-- wp:heading -->
<h2>前言</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>前两天无意间发现了基于<a rel="noreferrer noopener" href="https://uptimerobot.com/" target="_blank">UptimeRobot</a>接口制作的客制化网站监测页面，目前已经成功部署了，在惊讶于原作者有一个很棒的域名<a href="https://status.org.cn" target="_blank" rel="noreferrer noopener" aria-label="（在新窗口打开）">status.org.cn</a>的同时，也发现他这个服务是部署在ZEIT上的，试了一下，入门门槛比较低，还是很适合像我这样的小白来操作的。</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>部署过程</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>首先要说明一下，<a rel="noreferrer noopener" aria-label="ZEIT（在新窗口打开）" href="https://zeit.co" target="_blank">ZEIT</a>是有免费套餐的（当然，也有付费版），且与Github高度契合，配合上Github来用真的是方便到不行，同时，相当于Cloudflare Workers一样，部署成功就意味着部署到了他所有的节点服务器上（虽然对国内访问不太友好），官网介绍他们所使用的服务器有Google Cloud，Azure，Amazon。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":9670,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/19887.png@!large" alt="" class="wp-image-9670"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>在登录的时候选择Github登录或者其他的方式，经过一些简单的信息填写之后就可以选择你的源码了，像我这种不会编程的小白，通常就是在Github上Fork别人的源代码，然后稍微修改一些信息，就可以拿来用了。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":9671,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/15727.png@!large" alt="" class="wp-image-9671"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>如果是像我一样使用Github上的源码的话，在Continue之后还需要连接到你的Github账户，这样ZEIT就可以读取你的代码库了。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>像下面这样，选择你需要编译使用的库。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":9672,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/14157.png@!large" alt="" class="wp-image-9672"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>选择好你的资源名，根目录和相关编译运行代码，系统就会开始编译，编译完成之后就可以访问ZEIT给你提供的域名来查看相关信息。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":9673,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/13997.png@!full" alt="" class="wp-image-9673"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p> 此外，你还可以在Settings-&gt;Domains里面使用CNAME解析的方法来自定义你的域名，也是很方便。设置完成后会自动给你开启HTTPS访问，使用Let's Encrypt的证书，好评。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":9674,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/13947.png@!large" alt="" class="wp-image-9674"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>之后Github上有源码变动的时候，ZEIT就会自动进行编译工作，稍等片刻你就可以看到最新的编译版本。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>如果觉得他自身的服务器在国内访问不太好的话，可以去Cloudflare或者百度云加速进行CNAME接入加速，都是一样的道理，这里就不多说了。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>像我部署的这个就是网站可用性监测服务，界面比原本官方提供的界面要好看一点（个人觉得），具体可以<a rel="noreferrer noopener" aria-label="（在新窗口打开）" href="https://t.ratodo.com" target="_blank">点击看一下</a>，由于启用了百度云加速服务，所以访问应该不会有太大问题。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"align":"center","id":9685,"sizeSlug":"large"} -->
<div class="wp-block-image"><figure class="aligncenter size-large"><img src="https://p.ratodo.com/wp-content/uploads/2020/03/21192.png@!large" alt="" class="wp-image-9685"/></figure></div>
<!-- /wp:image -->

<!-- wp:heading -->
<h2>总结</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>ZEIT说起来操作并不复杂，简单几个步骤就可以完成源码编译和部署，但是只能是静态资源，像HEXO之类的静态博客使用这个服务也是完全没有问题的。具体的可用范围大家就自己去摸索吧。</p>
<!-- /wp:paragraph -->
