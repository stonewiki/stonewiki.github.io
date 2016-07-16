---
layout: post
title: WAMP环境的安装
categories: 泰牛程序员笔记
tags: 
- apache
- mysql
- php
comments: true
---


#### 如何安装WAMP开发环境

**1.Apache安装**  
1.以管理员方式运行cmd   
2.在apache\bin目录下运行 httpd -k install   
3.安装成功后配置apache的配置文件   
4.将配置文件中apache的安装目录改成你apache的位置   
5.并修改serverName服务地址为localhost  
6.配置后，重新启动apache服务   httpd -k start  

**2.PHP安装**  
1.将php处理模块和apache整合到一起，修改httpd.conf

//PHP - Module   
LoadModule php5_module "{php路径}/php5.6.16/php5apache2_4.dll"  
<FilesMatch \.php$>   
    SetHandler application/x-httpd-php   
</FilesMatch>   
PHPIniDir "{php路径}/php5.6.16/"  

2.将php.ini-deployment  改成 php.ini 启用开发模式  
3.开启dll库   
extension=php_bz2.dll   
extension=php_curl.dll   
extension=php_mbstring.dll   
extension=php_mysql.dll   
extension=php_mysqli.dll   
在phi.ini 中指定扩展模块路径    
extension_dir = "{php路径}/php-5.6.16/ext"    
重新apache服务

**3.mysql安装**  
典型安装-细节配置-并发设置-端口设置-字符集-服务名-密码配置