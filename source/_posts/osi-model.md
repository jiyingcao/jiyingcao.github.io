---
title: 网络协议模型
date: 2019-06-11 09:10:49
tags:
- 计算机网络
---

Google搜“OSI Model vs TCP/IP Model”，有大量的图片示例。随便截取几张：
![https://techdifferences.com/wp-content/uploads/2016/03/Untitled-1.jpg](https://upload-images.jianshu.io/upload_images/13318826-44d0d890a29d9199.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![http://fiberbit.com.tw/wp-content/uploads/2013/12/TCP-IP-model-vs-OSI-model.png](https://upload-images.jianshu.io/upload_images/13318826-3a2a98550c7596bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![https://www.computernetworkingnotes.org/images/cisco/ccna-study-guide/csg23-01-compare-osi-model-and-tcp-ip-model.png](https://upload-images.jianshu.io/upload_images/13318826-885d06908f391867.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![https://www.stemjar.com/wp-content/uploads/2017/12/OSI-vs-TCP-IP-model-What-is-the-difference.jpg
](https://upload-images.jianshu.io/upload_images/13318826-f5a9d5ec818920c3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# OSI七层模型

OSI模型是一个标准而不是实现，走的是学院派路子。搜“osi model mnemonic”能搜到很多助记词，有兴趣的可以点击底部的链接查看。
> **All People Seem To Need Data Processing**

当然我最喜欢这一句：
> **Please Do Not Touch Sally's Pretty Ass**

就不翻译了，自己意会吧 :)

# TCP/IP模型

TCP/IP四层模型用在开发中，是实际意义上的网络协议模型。这里英文名以维基百科的用词为准，中文名以谢希仁《计算机网络》为准：

* Application layer（应用层）
* Transport layer（运输层）
* Internet layer（网络层）
* Link layer （网络接口层？）

应用层对应OSI的应用、表示、会话层，网络接口层对应OSI的数据链路层和物理层。网络层包括IP协议，运输层包括了TCP、UDP协议。

# 五层模型
TCP/IP模型也有五层的划分方法，将网络接口层拆分为数据链路层和物理层，对应OSI的底部两层。《计算机网络》就是这种划分。

# 参考
[OSI Layer Mnemonic](https://adminhacks.com/osi-mnemonic.html)
[Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite#Key_architectural_principles)
《计算机网络》（第7版）- 谢希仁 著
[网络七层模型与四层模型区别]([https://juejin.im/post/59a0472f5188251240632f92](https://juejin.im/post/59a0472f5188251240632f92)
)