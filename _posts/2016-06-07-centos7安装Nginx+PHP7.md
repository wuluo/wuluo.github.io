---
layout: post
title: centos7安装Nginx+PHP7
description: 自己使用centos7安装Nginx+PHP7 的一些步骤，进行了简单的整理…… 
img: image-1.jpg
author: wuluo
---

#### 1、安装相应的扩展支持；

```
yum install gcc-c++  
yum install pcre pcre-devel  
yum install zlib zlib-devel  
yum install openssl openssl-devel 
yum -y install libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel libxml2 libxml2-devel mysql pcre-devel
yum -y install curl-devel libxslt-devel
```


#### 集成至一行命令一次安装

```
yum -y install libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel libxml2 libxml2-devel mysql pcre-devel gcc-c++  pcre pcre-devel pcre pcre-devel openssl openssl--devel curl-devel libxslt-devel
```


如有不能成功安装的，单独再安装一次即可；

#### 2、编译安装Nginx最新版本
//检查是否已经安装nginx

```
$   find / -name nginx
```

//如果已经安装nginx先卸载掉   

```
$   yum remove nginx
```

//进入习惯使用的下载目录，下载想要使用的nginx版本

```
$   wget http://nginx.org/download/nginx-1.7.4.tar.gz
```

//解压nginx安装包

```
$   tar -zxvf nginx-1.7.4.tar.gz
```

//进入解压后的目录

```
$   cd nginx-1.7.4
```

//配置安装信息，要加载什么扩展，安装到什么目录之类的
//使用--prefix参数指定nginx安装的目录,
make、make install安装
$   ./configure  $默认安装在下载目录
//指定目录

```
$   ./configure --prefix=/usr/local/nginx
```
 
//指定安装在/usr/local/nginx
//编译安装

```
$   make && make install
```


//检查是否安装成功

```
$   whereis nginx
```


#### 3、编译安装PHP7
//下载、解压、进入目录：

```
$   wget http://downloads.php.net/~ab/php-7.0.6RC1.tar.gz
$   tar -zxvf php-7.0.6RC1.tar.gz
$   cd php-7.0.6RC1
```

//配置安装信息、扩展

```
$  ./configure --prefix=/usr/local/php --exec-prefix=/usr/local/php --bindir=/usr/local/php/bin --sbindir=/usr/local/php/sbin --includedir=/usr/local/php/include --libdir=/usr/local/php/lib/php --mandir=/usr/local/php/php/man --with-config-file-path=/usr/local/php/etc --with-mysql-sock=/var/run/mysql/mysql.sock --with-mhash --with-openssl --with-mysql=shared,mysqlnd --with-mysqli=shared,mysqlnd --with-pdo-mysql=shared,mysqlnd --with-gd --with-iconv --with-zlib --enable-zip --enable-inline-optimization --disable-debug --disable-rpath --enable-shared --enable-xml --enable-bcmath --enable-shmop --enable-sysvsem --enable-mbregex --enable-mbstring --enable-ftp --enable-gd-native-ttf --enable-pcntl --enable-sockets --with-xmlrpc --enable-soap --without-pear --with-gettext --enable-session --with-curl --with-jpeg-dir --with-freetype-dir --enable-opcache --enable-fpm --enable-fastcgi --with-fpm-user=nginx --with-fpm-group=nginx --without-gdbm --disable-fileinfo
```

//编译检查不通过，缺少什么扩展安装了重新检测，通过后编译安装

```
$   make clean && make && make install

$   make test
```


#### 配置文件

```
# cp php.ini-development /usr/local/php/lib/php.ini
# cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
# cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
# cp -R ./sapi/fpm/php-fpm /etc/init.d/php-fpm
```


//安装完成后修改nginx配置文件nginx.conf，添加对php的支持，指定项目目录，完成后重启nginx
//启动php-fpm

```
#  /etc/init.d/php-fpm
```





