---
layout: post
title:  "bootstrap框架-导航条"
category: "学习笔记"
comment: true
---

#### 导航条有下列几种
**1.普通导航条**
{% highlight html linenos %}
<nav class="navbar navbar-default navbar-fixed-top">
    <div class="container-fluid">
        <div class="navbar-header">
            <div class="navbar-brand">导航条的品牌/logo</div>     
        </div>
        <ul class="nav navbar-nav">
           <li><a href="#">具体内容</a></li>
        </ul>
    </div>
</nav>
{% endhighlight %}

首先指定nav 是一个导航栏 ，navbar-fixed-top固定在顶部
container-fluid 告诉导航栏里面的内容为流式布局
navbar-header 里面的内容只有一个，就是导航条的品牌名
其它的导航栏里的内容，应该用ul包含


**2.带有隐藏功能的导航条**
{% highlight html lineos%}
<!--导航条-->
 <nav class="navbar navbar-default navbar-fixed-top">
     <div class="container-fluid">
         <div class="navbar-header">
             <div class="navbar-brand">
                 <a href="#">
                     <span class="glyphicon glyphicon-home"></span>
                 </a>
             </div>
             <!-- 三个横线-->
             <button class="navbar-toggle" data-toggle="collapse" data-target="#divNav">
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
                 <span class="icon-bar"></span>
             </button>
         </div>
         <!-- 导航内容-->
         <div class="collapse navbar-collapse" id="divNav">
             <ul class="nav navbar-nav">
                 <li><a href="#info">基本信息</a></li>
                 <li><a href="#skill">所会技能</a></li>
                 <li><a href="#work">工作经验</a></li>
                 <li><a href="#projcet">项目展示</a></li>
                 <li><a href="#contact">请联系我</a></li>
             </ul>
         </div>
     </div>
 </nav>
{% endhighlight %}

解释：

data-target 绑定目标

data-toggle 事件响应

collapse 堆叠