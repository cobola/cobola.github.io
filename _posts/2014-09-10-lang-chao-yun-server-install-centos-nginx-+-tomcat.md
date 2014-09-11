---
layout: post
date: 2014-09-10 22:40:19 +0800
title: 浪潮云服务器环境安装Centos nginx+tomcat等
---

首先更新一下

	yum update
   
更新完成后 安装nginx ``yum install nginx``
   
安装完成nginx 后 去oracle网站下载jdk 安装 去Apache网站下载tomcat 解压缩 

解压缩成两个tomcat 

	/usr/local/tomcat1
    /usr/local/tomcat2

修改 tomcat2端口，以防止启动时端口冲突 修改如下

	<Server port="18005" shutdown="SHUTDOWN">
    <Connector port="9090" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
    <Connector port="18009" protocol="AJP/1.3" redirectPort="8443" />
    
    
这样 可以通过 `/usr/local/tomcat1/bin/startup.sh` 和`/usr/local/tomcat2/bin/startup.sh`分别启动起来这两个tomcat 运行正常

修改nginx的配置

	upstream hep2d_robstodo {
    ip_hash;
    server 127.0.0.1:8080 weight=1;
    server 127.0.0.1:9090 weight=1;
    }
    
    
    location / {
         proxy_set_header X-Real-IP $remote_addr;
         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
         proxy_set_header Host $http_host;
         proxy_set_header X-NginX-Proxy true;

         proxy_pass http://hep2d_robstodo/;
         proxy_redirect off;
        }
        

设反向代理把请求转发给tomcat



启动tomcat1 tomcat2 启动nginx `service nginx start`


集群配置完成 收工。


目前没用 memcached 看情况将来再更新

参考 <http://blog.csdn.net/kongxx/article/details/5516152>

<http://www.iteye.com/topic/676347>
