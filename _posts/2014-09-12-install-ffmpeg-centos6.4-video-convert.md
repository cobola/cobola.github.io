---
layout: post
date: 2014-09-12 21:01:45 +0800
title: 在Centos6.4安装ffmpeg 并在网站中集成视频转换服务
---

## 安装
安装有三个办法 

1. 自己编译安装
2. 利用yum安装
3. 下载已经编译好的 

### 1 自己编译安装
编译安装得办法可以参考这里 <https://trac.ffmpeg.org/wiki/CompilationGuide/Centos>

还有一个自动安装得脚本

<https://github.com/jnaqsh/ffmpeg_installer>

实验结果。。成功了 
一个小问题是 

<https://chromium.googlesource.com/webm/libvpx.git>

这个源码地址可能被封掉了 想办法自己下载下来
一个大问题是，和mac下通过brew安装得不太一致。ffmpeg的参数太复杂了，后面那个转换参数不能识别。

### 2 利用yum安装

安装rpmforge的源后通过yum安装

	yum -Uvh http://apt.sw.be/redhat/el6/en/x86_64/rpmforge/RPMS/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
   
yum install ffmpeg ffmpeg-devel

安装后的版本是ffmpeg 0.5.x

版本比较老 可以用 装 rpmfusion的源 再安装

	rpm -Uvh http://download1.rpmfusion.org/free/el/updates/6/x86_64/rpmfusion-free-release-6-1.noarch.rpm
    
    yum remove ffmpeg ffmpeg-devel 这儿需要先卸载，再安装 不然有冲突
    
    yum install ffmpeg ffmpeg-devel
    

比较诡异的是 同样地源 同样地系统的两台机器 装出来的结果不一样

CENTOS6.4 2.6.32-358.el6.x86_64
装出来 一个是 ffmpeg 0.10.11 一个是 ffmpeg version N-64310-gf054d1e

### 3 直接下载编译好的版本

下载地址 <http://johnvansickle.com/ffmpeg/>

这个版本 ffmpeg 2.3.3 

最后选的这个，前面都白折腾


## 和Java集成

集成方法如下：
<script src="https://gist.github.com/cobola/836a3292e2c567d3de3f.js"></script>


转换效率 这个参数 时间基本是等长时间转换。效率不好 听一个别的公司说他们做的视频转换 能做到8小时视频1小时转完。











