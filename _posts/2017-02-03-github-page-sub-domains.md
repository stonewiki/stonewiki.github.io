---
layout: post
title: GitHub Pages 二级域名的配置
date: 2017-01-01
excerpt: "如何配置GitHub Pages的二级域名."
tags: [github]
comments: true
---


#### 域名配置指南    

* 首先创建一个新的仓库，并在设置中设置GitHub Pages的Source从master主分支上构建，点击保存，如下图所示:
    {% capture images %}
        http://xueyao.org/images/2017/02/sp170202_220301.png
    {% endcapture %}
* 并在Custom domain 里填写自定义的二级域名，如下图所示:
    {% capture images %}
	    http://xueyao.org/images/2017/02/sp170202_220346.png
    {% endcapture %}
    {% include gallery images=images caption="Custom domain" cols=1 %}
* 在你的域名注册商那里设置域名的DNS,类型CNAME,具体配置如下:
     {% capture images %}
	    http://xueyao.org/images/2017/02/sp170202_220021.png
    {% endcapture %}
    {% include gallery images=images caption="配置域名DNS" cols=1 %}
* 把写好的代码同步到创建的仓库中，通过浏览器访问二级域名，效果如下：
     {% capture images %}
	    http://xueyao.org/images/2017/02/sp170202_220444.png
    {% endcapture %}
    {% include gallery images=images caption="访问二级域名" cols=1 %}
* 注意此二级域名的一级域名必须解析到自己flowstone.github.io下，如下图所示：
     {% capture images %}
	    http://xueyao.org/images/2017/02/sp170202_220120.png
    {% endcapture %}
    {% include gallery images=images caption="解析域名" cols=1 %}



             
