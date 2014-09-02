---
layout: post
title: Chrome扩展 水木社区老板模式
tags:
- chrome
---




前段时间看到逛丢的老板模式，觉得很酷。于是就打算做一个水木社区老板模式。

    所谓老板模式，就是把水木社区的网页加一个office的皮肤，老板从远处一看，很棒，在写文档呢，然后走近了一看，很棒在写文档呢，然后凑过来一看，很棒，在写文档呢！
    于是就升职、加薪、升任CEO，迎娶白富美，走上人生巅峰！一定是这样的。


哈哈

插件的实现并不复杂，鉴于在天朝访问Google不是很方便，可以看 360 君给大家准备的教程，[点击查看](http://open.chrome.360.cn/extension_dev/overview.html)

实现思路如下：

*   首先获取网页的dom 在顶部加上office的图片
*   内容元素修改样式 实现类似一个office文档页面的效果

对<http://m.newsmth.net> 比较简单，<http://www.newsmth.net> 比较复杂，因为里面有些内容是通过js进行操作的，操作在插件的执行之后，所以效果不是很好。不知道这方面chrome插件是怎么处理的。

已经提交 360chrome插件商店。

效果图可以看这里 [lofter](http://smthboss.lofter.com/post/46729b_196b75a)

[点击下载](http://kexue.qiniudn.com/chrome-plugin-smth-bossmode.crx)


收工。



