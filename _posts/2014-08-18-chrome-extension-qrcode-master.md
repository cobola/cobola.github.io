---
layout: post
title: Chrome扩展 二维码大师
tags:
- chrome
- qrcode
---



这个其实是在写完[水木社区老板模式](http://cobola.github.io/2014/08/07/chrome-plugin-smth-boosmode.html)后就写了。

这个扩展最开始的想法是,[知乎](http://zhihu.com) 的内容分享里面没有 **分享到微信** 的功能 通过查看知乎页面的dom结构拿到问题的url 然后把这个url生成二维码图片 就可以了



 	 var shares = $(".zm-meta-panel");
 	 for (var i = 0; i < shares.length; i++) {

	    try {
    	  	var share = shares[i];
      		var p = $(share).parents(".feed-item");

	        var qid = $(p).find("meta[itemprop='question-url-token']").attr("content");

      		var url = "http://www.zhihu.com/question/" + qid;
      		if ($(p).find("meta[itemprop='answer-url-token']") != 'undefined' && $(p).find("meta[itemprop='answer-url-token']").length > 0) {
        		url = url + "/answer/" + $(p).find("meta[itemprop='answer-url-token']").attr("content");
      		}
	.....


同样地情况 也可以给[水木社区](http://www.newsmth.net)生成一个二维码图片

拿起手机 扫描就后就可以分享到朋友圈了。

掏了5刀 插件提交到了Google扩展商店 地址在这里 [点击在线安装](https://chrome.google.com/webstore/detail/qrcode-master/eandllggnghikbggfgifghhbhfahojfm?hl=zh-CN)







