---
layout: post
date: 2015-01-15 20:08:05 +0800
title: 在linode上安装discuz 3.2 最新版
---

喜欢偷懒 能用yum安装的  都用yum安装

1 安装nginx

rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm

然后 yum install nginx 

service nginx start nginx启动成功

chkconfig --level 345 nginx on  


2 安装php

yum install php php-fpm


yum install install php-gd php-mysql php-mbstring php-xml php-mcrypt

chkconfig --level 345 php-fmd on  

3 安装mysql

yum install mysql-server mysql-devel

chkconfig --level 345 mysqld on

修改下密码 
/usr/bin/mysqladmin -u root password 'newpassword'



安装完成后 配置nginx


```
    root /var/www/hosts/bbs/upload;
    index index.html index.htm index.php;

    location ~ \.php$ {
        root           /var/www/hosts/bbs/upload;
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  /var/www/hosts/bbs/upload$fastcgi_script_name;
        include        fastcgi_params;
    }
```

在conf中增加这个

剩下的 就正常使用了

祝大家玩的愉快






