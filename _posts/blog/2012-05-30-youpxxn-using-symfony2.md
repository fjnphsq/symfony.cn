---
layout: post
title: 日访问量2亿PV的YouPxxn
meta_keywords: Symfony2,PHP,技术架构,重构,大访问量,负载,HAProxy,ActiveMQ,Varnish,Redis,Nginx,MySQL
meta_description: 日访问量2亿PV的网站技术重构
categories: [blog, use-cases]
active_nav: blog
---

> YouPxxn是一家国外的视频网站，其内容的性质不受相关部门的欢迎，但每天承载2亿PV，每秒钟推送3部DVD容量的视频，这样的网站规模，仍然值得我们分析了解其技术架构——尤其当Symfony2是其技术选型方案一部分的时候。 

来源：[YouPorn - Targeting 200 Million Views A Day And Beyond](http://highscalability.com/blog/2012/4/2/youporn-targeting-200-million-views-a-day-and-beyond.html)

先看一组数据
------------

* 网站2006年上线，2011年被收购
* 2008年即达到每天1亿PV的浏览量
* 每秒30万请求
* 每秒推送100Gb的视频，相当于3张DVD的内容
* 每小时生成8GB-15GB的日志

架构
----

* 之前用的是Perl
* 现在用的PHP，以FastCGI方式运行于PHP-FPM
* HAProxy
* ActiveMQ
* Varnish
* Redis
* Nginx
* MySQL
* Syslog-ng
* Symfony2

关于框架优劣之争
----------------

经常见到关于框架优劣的争论，比较性能，比较功能完备性，等等。我们的观点是，能让你获得最高开发效率的框架，就是合适的。

YouPxxn的例子说明，Symfony2在一个相对完善的技术架构里，完全可以支撑巨大的访问量。
