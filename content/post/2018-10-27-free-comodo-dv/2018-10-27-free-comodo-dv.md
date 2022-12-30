---
title: 免费申请COMODO DV证书（3个月）
date: 2018-10-27 00:59:00 +0800
author: Ratodo
comments: true
categories: 
    - 建站笔记
---
<h2>前言</h2>
之前有说到GoGetSSL可以申请免费的COMODO证书，这里详细说明一下申请的流程。

<strong>注意：此文申请的COMODO证书为三个月有效期，到期需要手动去续期。并且！此证书与Let‘s Encrypt和阿里云等申请的DV证书没有除了颁发者以外的任何差别。</strong>

我申请的原因主要是比较喜欢COMODO这个品牌，因为当时注册第一个.me域名的时候就附带了一张一年期的COMODO证书。
<h2>准备</h2>
生成自己的CSR和KEY文件

推荐使用MySSL <a href="https://myssl.com/csr_create.html" target="_blank" rel="noopener noreferrer">CSR<span style="text-indent: 0em;">在线生成工具</span></a>

当然，你也可以使用你的服务器来生成这两个文件，在此就不多赘述了。

<strong>生成的CSR和KEY用Notepad++分别保存为service.csr和private.key（名称随意）。</strong>
<h2>申请证书</h2>
证书申请网站：<a href="https://www.gogetssl.com/dv-ssl/" target="_blank" rel="noopener noreferrer">Buy Free SSL from $0.00/year. Cheap Comodo Free SSL</a>

进入网站你就可以看到下面的界面，点击<strong>Buy SSL Certificate</strong>即可进入下一步。

<strong>注意：</strong>这里虽然显示的是一年期，但是到下一步就会变成90天，毕竟是人家提供的服务（摊手.jpg），而且这里不用担心账户注册的问题，后面会提醒你注册的。

<img class="alignnone size-full wp-image-58" src="https://p.ratodo.com/wp-content/uploads/2018/10/27000640.png@!full" alt="" width="823" height="383" />
<h3>Step1</h3>
选择你的产品，这里不用选，直接点击下面的<strong>Complete Order</strong>进入下一步。

<img class="alignnone size-full wp-image-59" src="https://p.ratodo.com/wp-content/uploads/2018/10/27001009.png@!full" alt="" width="801" height="799" />
<h3>Step2</h3>
到这一步它就会要求你登陆账号了，没有的话就点击上方的<strong>Create new account</strong>创建一个新账号即可。

注册过程就不细说了，就是填写一下个人信息，邮箱，联系方式等信息即可。

注册完成后登陆你的账号，它会跳转到DashBoard首页，这时我们点击左侧的<strong>SSL Certificates</strong>即可找到我们还未完成的订单。

<img class="alignnone size-full wp-image-60" src="https://p.ratodo.com/wp-content/uploads/2018/10/27011.png@!full" alt="" width="251" height="47" />
<h3>Step3</h3>
点击<strong>Generate</strong>，来进行必要的信息补充。

<img class="alignnone size-full wp-image-61" src="https://p.ratodo.com/wp-content/uploads/2018/10/27001806.png@!full" alt="" width="858" height="121" />

在<strong>Paste your CSR</strong>一栏中填入你刚刚生成好的CSR，然后点击下面的<strong>Validate </strong><strong>CSR</strong>进入到最后的认证阶段。

<img class="alignnone size-full wp-image-62" src="https://p.ratodo.com/wp-content/uploads/2018/10/27002407.png@!full" alt="" width="922" height="769" />
<h3>Step4</h3>
接下来就是完成对你域名所有权的认证了，这儿有四个方式可以选择，因为我用的是宝塔面板，管理文件比较方便，所以用的HTTPS文件认证，你们可以根据自己的情况来选择最适合自己的验证方式。

选择完毕后点击<strong>Next Step</strong>进行到最后一步。

<img class="alignnone size-full wp-image-64" src="https://p.ratodo.com/wp-content/uploads/2018/10/27003045.png@!full" alt="" width="921" height="421" />

进入下一步后，按照要求来填写网站联系人信息即可完成此订单。

J<strong>ob Title</strong>可以直接写<strong>Owner</strong>。

<img class="alignnone size-full wp-image-65" src="https://p.ratodo.com/wp-content/uploads/2018/10/27003228.png@!full" alt="" width="922" height="886" />

点击<strong>Complete Generation</strong>结束。
<h3>Step5</h3>
进行域名所有权验证。

完成订单后我们再次点击左侧的<strong>SSL Certificates</strong>，找到我们刚刚的订单，点击最右侧的<strong>View</strong>查看详情。

<img class="alignnone size-full wp-image-66" src="https://p.ratodo.com/wp-content/uploads/2018/10/27003947.png@!full" alt="" width="924" height="141" />

点击上方的<strong>Domain Validation</strong>即可查看所需要的验证信息，更具此验证信息去配置文件或者DNS即可。

<img class="alignnone size-full wp-image-67" src="https://p.ratodo.com/wp-content/uploads/2018/10/27004157.png@!full" alt="" width="927" height="250" />

配置好后点击<strong>Revalidate</strong>即可刷新状态，成功验证后，证书会自动颁发。

再次回到<strong>Details</strong>，即可选择<strong>Download al files(ZIP)</strong>来下载你的证书。
<h3>Step6</h3>
配置你的证书，私钥文件就是刚刚与CSR一同生成的key，而此处颁发的crt证书文件共有三个，使用时需要将它们合为一个crt证书使用，顺序为你的域名.crt+COMODO_...<em>Authority.crt+AddTrust</em>.._Root.crt。

<img class="alignnone size-full wp-image-69" src="https://p.ratodo.com/wp-content/uploads/2018/10/27004943.png@!full" alt="" width="527" height="67" />

安装时可以直接一个一个用记事本打开按顺序复制粘贴，也可以提前使用Notepad++将三个文件内容按顺序合并生成一个新的完整证书文件full_chain.crt（名称随意）。
<h2>总结</h2>
申请过程不复杂但也没什么必要一定要申请COMODO的证书，当然，这也是免费证书的一类罢了，看个人喜好吧。

有效期只有90天，到期要自己去手动续期。

虽然这个是免费证书获取方法之一，但我还是推荐购买一份自己的证书，几十的也好，几百的也罢，毕竟，免费的和收费的差别还是很大的。GoGetSSL里最便宜的<span class="com-GGSSL">GGSSL</span>  Domain SSL Certificate只要$4.30一年，还是比较划算的。
<h2>参考文章</h2>
<a href="https://www.laozuo.org/11866.html" target="_blank" rel="noopener noreferrer">GoGetSSL申请免费Comodo SSL证书 - 注册和申请过程</a>
