#开源不是免费的



之前大名顶顶的Surge软件被抄袭到app store,没想到这样的事件也发生到我身上，怎么也没想到一个自己的小开源软件会被复制成7个的情况，该哭该笑，一个是app store总榜70名，还有一个是付费分类榜21名，呵呵！

我于2015年9月29日开源了一款iOS平台的万能播放器，支持播放一些iOS framework不支持的格式，名字叫做[Eleven](https://github.com/coderyi/Eleven)，只是为了好玩而已，并且在9月20日的时候已经上架app store ,全称为[ElevenPlayer](https://itunes.apple.com/cn/app/elevenplayer/id1033773648),定价1美元。很多人想笑既然付费上架为何又开源，我只是想app的技术是开源的，但不代表app的使用价值免费。

目前我在iOS app store 发现了7款与eleven在功能与视觉上几乎一样的app，我的[ElevenPlayer](https://itunes.apple.com/cn/app/elevenplayer/id1033773648)是开源在[MIT](https://github.com/coderyi/Eleven/blob/a21614ab1589d9c83047bd16f7efa5f5443817c9/LICENSE.txt)协议之下，详细见第一次commit的readme的license [first commit](https://github.com/coderyi/Eleven/tree/9ec8cf1e987f7c4ebc7d8310040102410fc416a3)，该协议虽然规定了你可以拷贝并且发行，但是您必须包含Eleven Project的许可声明，当然我并未在这7款app中找到相关的说明。并且对于软件开源协议我至今未找到一款禁止商业软件使用的，就连最严格的GPL也是只要开源即可，商业软件一样使用。另外我在开源的时候readme另外注明了“you can not upload it to the App Store”，这好像没有任何作用吗？

这是一个开放源代码的问题，另一个是对于eleven这款app 产品，7款app在功能以及视觉几乎一样，这是否关乎抄袭，是否关乎侵权，是否关乎法律？并且对于7款app的混淆行为是否构成不正当竞争？


[ElevenPlayer](https://itunes.apple.com/cn/app/elevenplayer/id1033773648)主要有三方面功能，多种格式的本地播放，itunes或者wifi传输文件，播放网络流媒体。视觉上使用侧边栏，主要划分本地与网络两栏。我去年做这个只是为了了解iOS的视频开发，所以从源码上也可以看出来我并未花多少功夫，也没有花时间去设计，更未花精力推广，下面就截取7款app的页面来对比eleven，可以从app preview里面发现除了名字和logo，以及不同程度的加入广告，修改价格外，功能和视觉几乎一模一样，另外slogon也同ElevenPlayer一样为“一个简单强大的播放器”，具体情况您可以下载app后使用得知（虽然不建议）

eleven具体看下图
![eleven](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven.png) 上架时间：  2016年09月20日

七款app分别是

[影音先锋 - 万能视频播放器](https://itunes.apple.com/cn/app/ying-yin-xian-feng-wan-neng/id1126761053) 上架时间：2016年06月27日


[搜索播放器-找片看片神器！](https://itunes.apple.com/cn/app/sou-suo-bo-fang-qi-zhao-pian/id1097396706) 上架时间：2016年05月01日


[视频盒子-找片看片神器](https://itunes.apple.com/cn/app/shi-pin-he-zi-zhao-pian-kan/id1117602653) 上架时间：2016年06月23日

[万能免费钥匙播放器](https://itunes.apple.com/cn/app/wan-neng-mian-fei-yao-shi/id1072263654) 上架时间：2016年01月14日


[吉吉手机版搜索神器影音](https://itunes.apple.com/cn/app/ji-ji-shou-ji-ban-sou-suo/id1104837206) 上架时间：2016年05月03日

[TTPlayer Pro](https://itunes.apple.com/cn/app/ttplayer-pro-shou-ji-ban-ji/id1105305006) 上架时间：2016年04月27日

[放放影院-万能看片神器！](https://itunes.apple.com/cn/app/fang-fang-ying-yuan-wan-neng/id1086665888) 上架时间：2016年04月20日


[影音先锋 - 万能视频播放器](https://itunes.apple.com/cn/app/ying-yin-xian-feng-wan-neng/id1126761053)
是我第一个发现的，上个月才上架，就进入总榜70名，刷榜刷评论刷这么厉害，进入app之后就是跳转到app store的广告，联系方式只有一个github ，联系人只有一个github,[black-heart](https://github.com/black-heart)，这让我联系谁？

![1](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_3.png)



<img  src="https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_s1.jpg" width="320" height="570">



[搜索播放器-找片看片神器！](https://itunes.apple.com/cn/app/sou-suo-bo-fang-qi-zhao-pian/id1097396706) 

这款app除了功能视觉一样之外，可以从该app的本地视频右边按钮开启文件传输服务器后，访问web页能够看到我之前留下在web页的“Powered by Eleven Player, Copyright (c) 2015 coderyi”字样，并且web页的名字也是Eleven Player。健康健美（付费榜）第21名，售价6元，把我的elevenplayer变成看片神器，怎么好意思放在健康健美分类，appple审核的时候不知道是怎么想的，也不知道是怎么让7个相同的app通过审核的。好吧！我花了6块下载之后在app 里面找到了caoliu@sina.cn，连邮箱名字我也想吐槽，并且当我写完信之后准备发给他的时候才发现这是个假邮箱。

![2](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_5.png)


![2_reject](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_a1.png)

<img  src="https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_s4.jpg" width="320" height="570">

[万能免费钥匙播放器](https://itunes.apple.com/cn/app/wan-neng-mian-fei-yao-shi/id1072263654)
这位同学也是花了够多钱的，刷4万多app store评论的钱赚得回来吗？
![](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_6.png)

<img  src="https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_s3.jpg" width="320" height="570">


其他的4个app如下

[视频盒子-找片看片神器](https://itunes.apple.com/cn/app/shi-pin-he-zi-zhao-pian-kan/id1117602653)


![](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_7.png)


<img  src="https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_s2.jpg" width="320" height="570">


[吉吉手机版搜索神器影音](https://itunes.apple.com/cn/app/ji-ji-shou-ji-ban-sou-suo/id1104837206)


![](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_1.png)

[TTPlayer Pro](https://itunes.apple.com/cn/app/ttplayer-pro-shou-ji-ban-ji/id1105305006)


![](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_2.png)

[放放影院-万能看片神器！](https://itunes.apple.com/cn/app/fang-fang-ying-yuan-wan-neng/id1086665888) 


![](https://raw.githubusercontent.com/coderyi/blog/master/other/images/eleven_img/eleven_4.png)


我能怎么办？我进入github的时间不久，是2015年加入并注册账号的，当发现他的时候就变成了我迄今为止最喜欢的互联网产品，我看到了很多优秀的不可企及的开发者，Linus,Chris Lattner,onevcat等，我在swift开源的那一晚兴奋的睡不着觉，见到chris的第一次提交swift，这些好像让我看到了自己将如何走，这是github以及开源带来的。

好吧！我确实是比较天真的认为开源软件的问题不会发生在我身上，现在即使发生了，开源的游戏我还会继续玩，[ElevenPlayer](https://itunes.apple.com/cn/app/elevenplayer/id1033773648)我也会继续写，但是请亲爱的朋友们不要打乱游戏规则，要不然可能没人玩了。

所以最后，面对这样的情况我怎么办，并且请上面的7位app同学联系我，您应该能从我的github找到我的联系方式，然后请使用正确的使用链接[https://itunes.apple.com/cn/app/elevenplayer/id1033773648](https://itunes.apple.com/cn/app/elevenplayer/id1033773648)，谢谢！


