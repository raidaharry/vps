也许未来有一天，大家的业务做到了国外，这时候我们为了用户访问速度更快体验更好可能考虑在国外建站，这时候你们可能就会需要搭建一个国外的服务器。当然国外的vps还有另外一个好处就是流量转发，没错是你们想要的那种。今天猪哥就给大家演示一下如何在国外搭建服务器。

高能提醒：此教程为傻瓜式教程，男女老幼皆可尝试！

## 一、介绍VPS
### 1.什么是VPS
VPS（Virtual Private Server 虚拟专用服务器）可以理解成就是一台虚拟的服务器，它与服务器一样，有独立的IP、内存、带宽等，可以安装各种操作系统以及运行各种软件。应用也比较广泛主要是做网站、运行OA、运行系统软件等。

简单来说`VPS`就是一种虚拟**服务器**。

### 2.它与VPN有啥区别
VPN（Virtual Private Network 虚拟专用网络）是一种虚拟专用网络，它相当于利用公共网络环境搭建一条专线，使得外地的电脑访问本地服务器数据时的速度比较快。

简单来说`VPN`就是一种虚拟**网络**。

`VPS`和`VPN`是完全两种不同的概念，一个是服务器，一个是网络。在实际工作中有时候为了使服务器利用率达到最大，会使用虚拟技术在一台服务器上**虚拟多个服务器**（虚拟出来的服务器就叫VPS），然后我们去连接这些正式服务器的时候一般都是需要拨通VPN，才可以上正式服务器！

### 3.VPS与云主机有啥区别
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019051214010085.png?)
详细对比请看这里：[云服务器与VPS和虚拟主机有什么区别？](https://yq.aliyun.com/articles/226730)

## 二、购买国外VPS
既然说`VPS`是一种虚拟服务器，那我们改如何选购呢？

### 1.国外VPS选购
目前国内用的最多的还是搬瓦工和Vultr这两家VPS服务商。

Vultr官方网站：www.vultr.com
搬瓦工官方网站：www.bwh88.net

网上也有人做过专门的测评，感兴趣的同学可以看下：https://flyzyblog.com/bandwagonhost-vultr-comparison

猪哥基本不用考虑的选择：`Vultr`，为什么？便宜啊。

Vultr首次充值10美元送50美元，最便宜的服务器5美元一月，相当于我只要还10美元（67人民币）就可以使用1年。

搬瓦工最低方案是年付19.99美元

### 2.注册Vultr用户
购买Vultr的服务器之前需要在其官网注册（[https://www.vultr.com](https://www.vultr.com)）账号，只需要一个邮箱就可以了！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190512153019694.jpg?)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190512144729980.jpg?)
### 3.充值
点击验证邮箱按钮后，会 自动跳转到Vultr的个人主页，这时候我们需要充值，目前Vultr已经支持**支付宝**支付，所以我们将使用支付宝充值10美元。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513103811265.jpg?)
充值完大家可以看看自己账户是不是已经有了60美元。
### 4.选购VPS
有了钱我们就可以开始霍霍了，我们来看看VPS（虚拟专用服务器）的配置选购。
#### a.机房
因为是选购国外服务器，所以访问速度（低延时）和稳定性是首选，这里网上已经有人做过测试（Vultr 所有数据中心 IP 测试地址：[https://www.vultrblog.com/ip.html](https://www.vultrblog.com/ip.html)），这里推荐日本和美国洛杉矶的机房，猪哥选择的机房是**美国洛杉矶**，日本机房用的人多，所以整体上看要优于日本机房。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513143005888.jpg?)

#### b.选择系统
猪哥选的系统是CentOS7 64位，建议大家选择Linux系统，因为后面会将讲解如何安装流量转发软件（ss）。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513143504670.jpg?)
注意，Vultr还支持自己上传系统。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513143841209.jpg?)
### c.选配置
配置的话我们选择最低配，5$一月的，流量是一个月1T，一般情况肯定够用！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513144307985.jpg?)
### d.其他选项
其他选项无特殊需求都可以不选，默认就好，最后点击“Deploy Now”创建VPS。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513144323854.jpg?)
### 5.查看VPS
购买了VPS（虚拟专用服务器）之后我们来看看我们的服务器
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513151510413.jpg?)
然后我们再看看服务器的一些信息，我们后面远程链接需要用到。
![在这里插入图片描述](https://img-blog.csdnimg.cn/201905131515223.jpg?)
到此VPS（虚拟专用服务器）的购买已经介绍完毕，现在你就可以将你的项目部署到这台VPS（虚拟专用服务器）上面了，具体步骤与之前的部署教程类似：[超详细Pycharm部署项目视频教程](https://blog.csdn.net/u014044812/article/details/89761580)

## 三、安装ss软件
有时候我们查阅资料可能需要到国外的网站去，但是有时候却无法访问，怎么办？我们可以采用流量转发的形式，这里猪哥就带大家看看如何在VPS（虚拟专用服务器）中安装ss软件（什么是ss？自行百度）。

真香警告：本教程仅用于学习研究，请勿做任何危害gj的行为，热爱自己的zg！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513160312724.jpeg?)
### 1.远程连接VPS
远程连接软件有非常多，如：xshell和putty（xshell可以保存密码，putty右键直接粘贴）大家可以自行选择，猪哥这里就使用Mac电脑自带的终端（terminal）连接（你也可以使用pycharm里面的teminal）。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513161717444.jpg?)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513161734654.jpg?)

### 2.一键安装SS
登录服务器之后，我们就可以开始安装ss了，复制以下命令到远程连接中执行。
```shell
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```
执行命令后过一会提示你输入输入SS的密码，端口和加密方式
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513163631233.jpg?)
点回车之后会提示你让你再按一遍回车确定，然后出现ss信息，记得复制出来妥善保存。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513170344970.jpg?)
到此ss的安装教程就结束了。

## 四、连接ss
### 1.ss客户端下载
这里猪哥就不提供ss的客户端下载，请大家自行到网上下载各个端对应的app。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513160312724.jpeg?)

### 2.配置ss
这里猪哥以**Mac客户端**和**安卓客户端**为例给大家演示如何配置ss

#### a.Mac客户端：
下载并安装软件后启动软件，然后右上角会有一个小飞机，点一下，具体操作看下图。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513185129801.jpg?)
然后点+号，添加一个服务器的配置项。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513173357759.jpg?)
然后就是选择这个配置项，打开ss就可以。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513174256696.jpg?)
然后，你就可以查阅资料咯～
![在这里插入图片描述](https://img-blog.csdnimg.cn/201905131747291.jpg?)
如果你出现无法访问的情况，可以试试手机端时候能正常访问，如何手机端没问题，那可能是你电脑浏览器安装了啥插件或其他软件，换个浏览器试试。
#### b.安卓客户端
客户端自行网上下载，本教程不提供。

安卓客户端下载之后打开软件，然后点右上角+号，会出现三个选项。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513175556362.jpg?)
给大家介绍一下这个三个选项。

 1. 扫描二维码：如果你pc端已经配置完成，那么pc端会有一个生成二维码的按钮，点一下，然后安卓端扫描一下自动加载配置。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513180052836.jpg?)
 2. 从粘贴板导入：顾名思义，但是猪哥没用过，就不瞎bb
 3. 手动设置：这里配置和pc端配置基本类似，服务器、远程端口、密码、加密方式，其他的可以不用改。![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513180553674.jpg?)
配置完之后点击右下角的小飞机，然后看下方提示信息，然后就可以查阅资料咯！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513180901750.jpg?)
## 五、总结
本来还想录制视频的，但是由于最近有点忙就没录制了。

此教程简单易学，适合小白学习。

最后祝猪哥好运吧！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190513234144826.gif)
