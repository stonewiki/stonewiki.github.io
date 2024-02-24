## 个人博客
> blog.xueyao.me

### 项目介绍

这是一个通过Hugo搭建的博客程序

主题使用的是[devise](https://github.com/austingebauer/devise)

我已经fork到自己仓库中[地址](https://github.com/flowstone/hugo-theme-devise),并做了相关调整

博客预览如下

![](/blog-preview-image.png)

### 项目部署

项目是博客+主题(子模块)形式，

如果您修改了主题，并已提交到仓库中，

那么您要在博客项目中同步主题的代码
``` bash
git submodule update --remote themes/devise
```

其实这些操作主题文档中已经详细说明了，

那么我们只需要在博客项目中的写文章就可以了，

如果你想在本地预览博客效果
``` bash
hugo server -D
```

博客通过Github Action实现自动部署，

脚本在.github/workflows目录下
``` yml
hugo.yml 是生成静态代码保存到gh-page分支下
push-pages.yml 是同步代码到其它代码平台
```

### 特殊说明

博客的DNS解析已经修改成

国内IP访问Github Page项目地址

国外IP访问Fleek平台项目地址

#### 小插由

为了博客的稳定性，原本准备用多个代码平台的静态网页服务来实现DNS解析负载均衡，多个域名商并不支持这项功能，但是阿里云的DNS服务有这项功能，不得不说阿里云YYDS(例如免费企业邮箱)，测试如下
1. Coding是我的第一个选项，自从被腾讯收购后Coding提供了更多新的功能，原本的Page服务还是有的，但是后来却收费了(一定免费额度)
2. Gitee平台支持Page服务，但是要提交手持照片，而且想自定义域名需要开通会员，想了想还是算了
3. 阿里云的Code平台，因为之前某功能有问题，现在已升级成云效，没有发现有Page服务
4. Bitbueckt只支持自己的二级域名，暂时不支持绑定自定义域名
5. Gitlab支持Page服务，需要另外写流水线脚本，但是我是从Github那里同步过来，想让我增加新代码，没门!!!

其它代码仓库平台我已经不想测试了，国内的许多平台不允许大家白嫖服务资源，所以说免费才是最贵的，最终也是走向收费

### 更新说明

* 2024年2月24日 新增初始说明






