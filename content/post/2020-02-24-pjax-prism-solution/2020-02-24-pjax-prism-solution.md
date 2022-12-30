---
title: PJAX局部刷新导致Prism代码高亮失效的解决方案
date: 2020-02-24 17:33:00 +0800
author: Ratodo
comments: true
categories: [建站笔记]
---
<h2>前言</h2>
开启pjax局部刷新后在进入下一个页面的时候只需载入文章相关文件，大部分文件不需要重新载入，可以大幅降低网站的负载。并且对访问用户来说没有生硬的界面跳转，用户体验来说也很好。但是如果同时开启了prism代码高亮的话，在进入到文章页的时候，prism.js文件不会重载，这样也就导致了文章中的代码高亮失效。

我这个主题自带的Prism代码高亮重载功能对我这种情况无效，只好寻找其他方案。

对于这种情况网上有好几种解决办法，这里就针对wordpress来说其中的一个最简单的解决办法。
<h2>修改相关文件</h2>
方法确实很简单，修改一个文件就可以了，对于Asky系列主题来说，修改的文件位置是<code class="language-markup">/wp-content/themes/ASky/js/jquery.pjax.js</code>，如果不是这类主题的话，建议去搜索看看这个js文件名称。

修改位置在Line312行下方，如下图所示。

<img class="aligncenter size-full wp-image-9487" src="https://p.ratodo.com/wp-content/uploads/2020/02/23814.png@!full" alt="" width="616" height="227" />

相关代码如下：
<pre><code>//Prism Reload 
if (container.contents.find("code[class*='language-']").length &gt; 0) 
$.getScript("/wp-content/plugins/ank-prism-for-wp/out/prism-js.min.js");//Your Prism.js location</code></pre>
我这里是使用的Prism插件，所以最后一行的文件位置就是用的插件里使用的prism.js位置。

到此就完成了，此外如果使用了CDN的话，缓存可能会久一点，可以手动去CDN控制台刷新这个文件，刷新的时候注意看网站加载的jquery.pjax.js文件后面是否有?ver=x.x.x，有的话记得带上。
