---
layout: post
title: 百度地图和腾讯地图
---



百度地图的开发文档 写的太不认真了

http://developer.baidu.com/map/sdkandev-2.htm

    <uses-permission android:name="android.permission.CHANGE_WIFI_STATE" >

少了一个 / 结尾

    <com.baidu.mapapi.map.MapView
    android:id="@+id/bmapView"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:clickable="true" >

少了一个 / 结尾


    <ses-permission android:name="android.permission.READ_PHONE_STATE" />

拼错了单词 还重复了


    LatLng llText = new LatLng(39.86923, 116.397428);
    //构建文字Option对象，用于在地图上添加文字
    OverlayOptions textOption = new TextOptions()
        .bgColor(0xAAFFFF00)
        .fonSize(24)
        .fontColor(0xFFFF00FF)
        .text("百度地图SDK")
        .rotate(-30)
        .position(llText);
    //在地图上添加该文字对象并显示
    mBaiduMap.addOverlay(textOption);

fontSize 拼错了


怎么就不能认真一点！



关于那个腾讯地图。。。 功能太少了！




当然 最后我选的是 高德地图 。

原因

    1 百度地图通过location获得位置描述失败。。
    2 去论坛问 没人理

高德地图就是好啊就是好







