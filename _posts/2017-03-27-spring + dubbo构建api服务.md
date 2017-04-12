---
layout: post
title: spring + dubbo构建api服务
description: eclipse + tomcat + spring +dubbo 构建http服务基础配置，对初始化环境做简单的记录……
img: image-5.jpg
color: FF6F00
author: wuluo
---

1、安装eclipse java IDE，可以选择JavaEE，也可以选择Java；
2、安装tomcat，官网下载解压包或安装程序均可，建议选择tomcat7.0以上版本，使用exe安装，省心；
3、安装jdk，建议选择最新的，也就是1.8以上；安装完成，配置patch环境变量，到jdk目录的bin层级下，配置classpath，到jdk目录；配置JAVA_HOME，到jdk目录；
4、安装maven，官网下载安装包，直接解压到目标目录，配置MAVEN_HOME与M2_HOME环境变量,配置到安装目录下MAVEN的一级目录即可。
5、启动eclipse，配置maven项目创建器，配置默认运行服务器（server）为tomcat；如果缺少插件，需要安装插件。配置路径：windows->perfomence->maven || server
6、import（导入）项目，或者创建项目，第一次配建议导入现成的项目，主要是xml配置太操蛋；
7、启动server下的tomcat，即可访问，启动成功的标识是在console下可以看到所有可以访问的pathinfo；
过程中需要注意的坑：
1、端口占用问题，最常见，tomcat默认使用8080，启动过程中8005与8009也会用到；
2、如果你是maven项目，tomcat在发布项目的时候没有同时发布maven依赖所添加的jar包，
你需要设置一下eclipse：
项目 —> 属性 -> Deployment Assembly -> Add -> Java Build Path Entries -> 选择Maven Dependencies -> Finish -> OK
把对应的Maven依赖包也发布到tomcat，调试时会自动把那些jar发布到指定目录下，tomcat也能找到那些jar了。
3、如果你需要设置自己的maven 设置，settings文件，放到当前计算机用户目录下的.m2目录中，然后通过maven刷新项目；
4、注意在运行前确认一下你的eclipse是否勾选了自动构建选项，如果没有勾选，恭喜你，你项目中的代码都加载不到，只能看到项目根目录；

dubbo教程：http://dubbo.io/Home-zh.htm





