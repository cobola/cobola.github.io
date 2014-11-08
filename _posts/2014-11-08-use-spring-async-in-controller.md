---
layout: post
date: 2014-11-08 20:08:05 +0800
title: 利用spring async特性异步处理大文件
---

项目中，有上传视频的需求，上传的视频，要利用ffmpeg转码。这个费时比较久，利用spring的async特性，让转码的任务异步执行，从而不用前台等待响应。

使用方法很简单 在需要异步处理的方法上 加上@Async 注解 即可

```java
    @Async
    public void storeFile(Res res, String file);
```

在spring的xml文件中增加

```xml



<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc" xmlns:task="http://www.springframework.org/schema/task"
       xsi:schemaLocation="
           http://www.springframework.org/schema/beans   
           http://www.springframework.org/schema/beans/spring-beans-3.0.xsd   
           http://www.springframework.org/schema/context   
           http://www.springframework.org/schema/context/spring-context-3.0.xsd  
           http://www.springframework.org/schema/mvc   
           http://www.springframework.org/schema/mvc/spring-mvc-3.0.xsd http://www.springframework.org/schema/task http://www.springframework.org/schema/task/spring-task-3.0.xsd"
       default-autowire="byName">

    <task:annotation-driven/>
```


这样 体验就好多了 





